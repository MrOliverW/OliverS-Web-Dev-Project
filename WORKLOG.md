




Configuring  GitHub Repository
Need to tell GitHub to treat  main branch as the "source of truth" for  website.

Open repository on GitHub.

Click the Settings tab.

In the left sidebar, click Pages.

Under Build and deployment, look for Source.

Ensure it is set to Deploy from a branch.

Under Branch, select main from the dropdown menu and ensure the folder is set to /(root).

Click Save.



Configuring Namecheap (DNS)
Need to point your domain to GitHub’s servers so that when someone types in your URL, it finds your GitHub-hosted site.

Log in to Namecheap and go to your Dashboard.

Find your domain and click Manage.

Click the Advanced DNS tab.

Add 4 "A Records" pointing to GitHub's servers (these never change):

Type: A Record | Host: @ | Value: 185.199.108.153

Type: A Record | Host: @ | Value: 185.199.109.153

Type: A Record | Host: @ | Value: 185.199.110.153

Type: A Record | Host: @ | Value: 185.199.111.153

Add 1 "CNAME Record" to handle the www version:

Type: CNAME Record | Host: www | Value: yourusername.github.io

(Replace yourusername with your actual GitHub username).



Link Domain to GitHub
Once your DNS is configured, you must tell GitHub which domain it is responding for.

Back in your GitHub repository, go to Settings > Pages.

Under Custom domain, type your domain (e.g., yourdomain.com).

Click Save.

Wait for Verification:


Enjoy the pipeline!

*needed to remove:
The Parking Record: That first one (CNAME | www | parkingpage.namecheap.com) is the biggest issue. It's telling the world to go to Namecheap's "Buy this domain" page instead of your site.

The URL Redirect: The second one (URL Redirect Record | @ | http://www.oliversmokes.com...) needs to go. Since you have those A Records set up correctly for the @ host, this redirect is redundant and creates a "loop" error.




To make the site professional and  sound, level up your architecture from "Basic HTML" to a Static Site System by using Jekyll. It’s built into GitHub, uses Markdown (which is perfect for writing reviews), and will automatically inject your writings into a template.


_layouts/default.html (The Frame)

index.html (The Content)

_config.yml (The Brain)


Desiging the age gate:

a Jekyll "layout" system, the "Bouncer" (the age gate) needs to live in your _layouts/default.html file. If it stays in your old index.html, it will only guard the front door and let people sneak in through the "side doors" (like the blog or contact pages).


GitHub Actions is the automated factory that sits between your "blueprints" (the code you push) and the "finished building" (the live website).
Every workflow starts with an Event.

GitHub’s "Watchman" constantly monitors your repository.

The moment you hit "Commit and Push," the watchman yells, "Hey, we have new code! Start the factory!"

2. The Runner (The "Worker")
GitHub doesn't run the code on your browser or their website servers. Instead, it spins up a Runner—which is essentially a fresh, temporary Virtual Machine (usually running Linux/Ubuntu) in the cloud.

4/23/26 4pm:
Starting work on the event tracking now that the site is live, contact form and navigation is working.

Using Google Tag Manager

