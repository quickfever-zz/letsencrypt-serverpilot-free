# Install Let's Encrypt SSL on ServerPilot (Free Plan) / Digitalocean Hosted Droplet

Automate the installation of Let's Encrypt SSL on the free plan of ServerPilot





## Ready Your Droplet

In case you want to start over, [get $10 off](http://digitalocean.com/) in Digital Ocean for your droplet.

Create a Droplet with Ubuntu 16.x or anything and Install Wordpress with Serverpilot.

## Installing Let's Encrypt

About the script



This script adds Let's encrypt SLL to your Wordpress site created using Serverpilot and hosted on Digitalocean.

ServerPilot offers auto installation of Let's encrypt with upgrade account about $10 per month. This script saves the time and works with free serverpilot account. It's install SSL + adds a cornjob that renew Let's encrypt SSL

<code>Getting started</code>

### Clone the repo

If git isn't installed on your droplet, install it using this command

<pre>sudo apt-get -y install git</pre>

and then run this command to clone the repository

<pre>sudo git clone https://github.com/quickfever/digitalocean-serverpilot-letsencrypt.git && cd digitalocean-serverpilot-letsencrypt && sudo mv sple.sh /usr/local/bin/qfssl && sudo chmod +x /usr/local/bin/qfssl

</pre>

// The repo will be copied to your system under **/usr/local/bin** and will be made executable. And you don't need to do anything :)



Note: Let's encrypt allow only 5 SSL certificates per domain per week. If you think you already made this mistake, you've to wait for a week before using this method or use a different domain or subdomain of the domain you're adding SSL for.



## Install SSL

Here are the simple steps to install SSL on your apps

For main domains (Don't include www with your domain)

Visit serverpilot > Server > App, write down the app name.

<pre>qfssl install example.com app_name main</pre>

### For sub domains

If you run your website with "www"

<pre>qfssl install sub.example.com app_name sub</pre>



## Uninstall SSL



qfssl uninstall example.com app_name

qfssl uninstall sub.example.com app_name
