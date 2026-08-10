# cse135 -Thy Doan - hw1

## Part 2

### GitHub Deployment

The site deploys using a bare Git repository and a `post-receive` hook on the server.

**Setup:**

- A bare repo is at `~/git/cse135.git` on the droplet
- A `post-receive` hook will check out the latest files in
  `/var/www/thydoan.space/public_html`

**Deploy:**

- To deploy, run:
- `git push origin main`: push local changes to github
- `git push production main`: deploy to the server.

**Demo**

- Please see [Github-Deploy](Github-Deploy.gif) for a demo of deploying a file change.

## Part 3

### How to login as grader (step 4)

- username: grader
- password: cse135

### Compression (step 5)

After I enabled `mod_deflate`, I checked in Chrome DevTool, and I saw that response headers now include the `Content-Encoding: gzip`. Page transfer size dropped from 1.2kB (uncompressed) to 756B (compressed) for my homepage.

### Obscure server identity (step 6)

I changed the server response header to
"CSE135 Server" by installing mode-security2 and modified `SecServerSignature` inside `modsecurity.conf`.

**Steps:**

1. Install mod-security: `sudo apt install libapache2-mod-security2`
2. Enable the module: `sudo a2enmod security2`
3. Copy the recommended config:
   `sudo cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf`
4. Set `ServerTokens Full` in `/etc/apache2/apache2.conf` (to show the customized response header)
5. Add `SecServerSignature "CSE135 Server"` to `/etc/modsecurity/modsecurity.conf`
6. Restart Apache: `sudo systemctl restart apache2`
