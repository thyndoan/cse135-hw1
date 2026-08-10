# cse135 -Thy Doan - hw1

## GitHub Deployment

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
