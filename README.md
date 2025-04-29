## Prerequisites

These steps assume **macOS or Linux**.  
If you’re on Windows, follow Microsoft’s guide to install and use OpenSSH:  
https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse

---

## Step-by-Step Instructions

1. **Generate an ED25519 SSH key**  
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"

This creates a secure ED25519 keypair in ~/.ssh/.
See pico.sh’s guide for more details: https://pico.sh/faq#how-do-i-generate-an-ssh-key

    Create a pico.sh account

        Visit https://pico.sh/getting-started and sign up for a free account.

        After logging in, go to Settings > SSH Keys, click Add SSH Key, then run:

    cat ~/.ssh/id_ed25519.pub

    Copy the output and paste it into the form to authorize your key.
    This lets pico.sh Pages authenticate your deployments via SSH.

Download the static site files

curl -L <STATIC_SITE_URL> -o site.zip
unzip site.zip -d site

Replace <STATIC_SITE_URL> with the URL provided to you.
This fetches the starter files and extracts them into a site/ folder.

Initialize your local project directory

mkdir my-project
cd my-project
cp -r ../site/* .

Creates a clean workspace (my-project) and copies the downloaded files into it.

Deploy via the pico.sh Pages CLI

    Install the CLI (if you haven’t already):

npm install -g @picosh/pgs

For full CLI docs, see: https://pico.sh/pgs

From inside your project folder, run:

    pgs deploy --name my-project

    This publishes your site to pico.sh Pages using your SSH key.

Confirm your site is live

    Reference demo:

https://skazanakis-hosting-a-website-on-pico-sh.pgs.sh/index.html

Your site URL:

        https://<YOUR_USERNAME>-<PROJECT_NAME>.pgs.sh

    After deployment, navigate to your unique URL to verify everything is working.

Live Demo

View the working example here:
https://skazanakis-hosting-a-website-on-pico-sh.pgs.sh/index.html

Once you’ve deployed, your own site will be at:

https://<YOUR_USERNAME>-<PROJECT_NAME>.pgs.sh

Troubleshooting

    Permission denied (publickey)
    You haven’t added your SSH public key to pico.sh. Copy ~/.ssh/id_ed25519.pub into Settings > SSH Keys.

    Invalid key format
    The key wasn’t generated correctly. Regenerate using:

ssh-keygen -t ed25519

Command not found: pgs
The pico.sh CLI isn’t installed. Run:

    npm install -g @picosh/pgs

    ⚠️ Don’t forget to replace <YOUR_USERNAME> and <PROJECT_NAME> with your own values, then visit:

https://<YOUR_USERNAME>-<PROJECT_NAME>.pgs.sh

to confirm your deployment is live!
