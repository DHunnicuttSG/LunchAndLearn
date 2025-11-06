# A — Amazon Linux 2 (commands)

### 1) Update packages

```bash
sudo dnf update -y
```

### 2) Install Apache (httpd)

```bash
sudo dnf install -y httpd
```

### 3) Start and enable Apache to start at boot

```bash
sudo systemctl enable --now httpd
# confirm status
sudo systemctl status httpd --no-pager
```

### 4) Create a simple test web page

```bash
echo "<html><body><h1>Apache on Amazon Linux 2</h1></body></html>" | sudo tee /var/www/html/index.html
# set permissions (optional)
sudo chown -R ec2-user:ec2-user /var/www/html
# if you want root-owned, revert:
# sudo chown -R root:root /var/www/html
```

### 5) Verify Apache is listening and reachable

```bash
# listening on port 80
sudo ss -tuln | grep :80

# from the instance (local)
curl -I http://localhost
curl http://localhost   # show HTML content

# from your workstation/browser:
# http://YOUR_INSTANCE_PUBLIC_DNS  (open in browser)
```
---


## 🚦 Security group reminder

If you get a timeout from your browser, check EC2 Security Group inbound rules include `TCP 80` from your IP or `0.0.0.0/0` (public). Also ensure no corporate firewall blocks outbound HTTP.

---

# — Create and run a cron job

We’ll create a small script that appends a timestamp to a log file and add it to the crontab.

### 1) Create the script (works both on Amazon Linux & Ubuntu)

Pick a location — I’ll use `/home/ec2-user/cron_log.sh` for Amazon Linux and `/home/ubuntu/cron_log.sh` for Ubuntu. Adjust paths for your user.

```bash
# Amazon Linux 2 (if ec2-user)
cat <<'EOF' > ~/cron_log.sh
#!/bin/bash
# append timestamp and server info to a log
echo "$(date '+%Y-%m-%d %H:%M:%S') - $(hostname) - Apache running: $(systemctl is-active httpd || systemctl is-active apache2)" >> ~/cron_log.log
EOF

# make executable
chmod +x ~/cron_log.sh
```

**Notes:**

* `systemctl is-active httpd` for Amazon Linux; `systemctl is-active apache2` for Ubuntu. The script checks whichever service name exists (we used the `||` fallback so it prints whichever is active).
* The log file will be `~/cron_log.log`.

### 2) Run the script once manually (smoke test)

```bash
~/cron_log.sh
tail -n 20 ~/cron_log.log
```

You should see a timestamp line.

### 3) Add to your crontab

Edit the crontab for your user:

```bash
crontab -e
```

Add a line to run the script every 5 minutes (safer than every minute for production). For testing you can use `* * * * *` (every minute).

Example (every 5 minutes):

```
*/5 * * * * /home/ec2-user/cron_log.sh >/dev/null 2>&1
```

Example for Ubuntu user (if using `ubuntu` user):

```
*/5 * * * * /home/ubuntu/cron_log.sh >/dev/null 2>&1
```

Save and exit the editor. `crontab -l` will show installed jobs.

### 4) Confirm cron is running

**Amazon Linux 2**

```bash
sudo systemctl status crond --no-pager
# if not active:
sudo systemctl enable --now crond
```

**Ubuntu**

```bash
sudo systemctl status cron --no-pager
# if not active:
sudo systemctl enable --now cron
```

### 5) Wait and check the log

Wait 5+ minutes (or 1 minute if you used `* * * * *`) and then:

```bash
tail -n 50 ~/cron_log.log
```

You should see new timestamp lines appended every run.

---

## 🔎 Troubleshooting cron jobs

* If your script didn’t run:

  * Check crontab with `crontab -l`.
  * Check cron service status (see above).
  * Check cron logs:

    * **Amazon Linux 2:** `sudo tail -n 200 /var/log/cron`
    * **Ubuntu:** `sudo grep CRON /var/log/syslog | tail -n 50`
  * Ensure script has executable permission: `chmod +x ~/cron_log.sh`
  * Use full paths in the script (cron has a limited PATH). Example: use `/usr/bin/date` or set `PATH` at top of crontab like:

    ```
    PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
    ```
  * Redirect stdout/stderr to file for debug, e.g.:

    ```
    */5 * * * * /home/ec2-user/cron_log.sh >> /home/ec2-user/cron_debug.log 2>&1
    ```

---

## ✅ Verify Apache & cron integration (quick checks)

* Check Apache service:

  * Amazon Linux: `sudo systemctl is-active httpd` (should print `active`)
  * Ubuntu: `sudo systemctl is-active apache2`
* Check cron logs for job execution:

  * Amazon Linux: `sudo tail /var/log/cron`
  * Ubuntu: `sudo tail /var/log/syslog | grep CRON`
* Confirm file updates:

  * `tail -n 20 ~/cron_log.log`

---

## 🔁 Cleanup (when you’re done)

To stop and remove what you created:

```bash
# stop apache
# Amazon Linux
sudo systemctl stop httpd
sudo systemctl disable httpd

# Ubuntu
sudo systemctl stop apache2
sudo systemctl disable apache2

# remove cron job
crontab -l | grep -v 'cron_log.sh' | crontab -

# remove files
rm -f ~/cron_log.sh ~/cron_log.log
sudo rm -f /var/www/html/index.html
```

If you launched the EC2 instance only for testing, terminate it from the EC2 Console to avoid charges.

---

## 🔐 Security & best practices (quick notes)

* Do **not** leave SSH (22) open to `0.0.0.0/0` — restrict to your IP.
* For public web servers, only open ports you need (`80`/`443`).
* For production, consider using a dedicated non-root user for serving content, keep web files owned by `www-data`/`apache` as appropriate, and enable automatic security updates.
* Use CloudWatch or other logging/monitoring for production cron jobs or scheduled tasks.

---
