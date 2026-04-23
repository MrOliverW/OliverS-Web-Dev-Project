This is the README for the OliverS Website Repository (this file should not be added to the Site Hosting platform).


Building in VS Code using HTML and CSS with the intention to add other secure 3rd party integrations.

Site will begin as a 1-page site, just index.html and later the other pages will be built in.

Bought the domain name from NameCheap. Used GitHub pages for hosting.

Decided to use Jekyll and it feels great - the GitHub Actions Build Engine takes the place of import statements.
GitHub adopted Jekyll (uilzizaiton of "_" named folders) - GitHub runs the Jekyll engine. It parses the YAML Front Matter (the stuff between the --- lines), looks into your _layouts folder for a file named post.html, and injects your content into that frame.

Jekyll uses a language called Liquid (created by Shopify). When you see {{ content }} or {{ page.title }}, you are using Liquid tags.

The GitHub-Jekyll "Handshake"
Yes, Jekyll is natively integrated into GitHub Pages. If you moved these files to a "dumb" FTP server (like old-school Bluehost or GoDaddy), the server would just serve the raw text files. The browser would display {% for post in site.posts %} as literal text because the browser doesn't speak "Liquid."

GitHub acts as your build server. It takes your "source code" (Markdown and Liquid), runs it through the Jekyll engine, and outputs a "distribution" version (pure HTML/CSS) that the browser can actually understand.

I <3 Jekyll

Yes! In Jekyll, the "connection" happens through Front Matter (those --- lines).

