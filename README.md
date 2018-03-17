# Let's Encrypt on Your ServerPilot Free Plan
Automate the installation of Let's Encrypt SSL on the free plan of ServerPilot

## About the script
ServerPilot's paid plan costs only $10 per month that unlocks auto installation of Let's Encrypt SSL along with some other premium features. But if you don't want to spend that $10 then this script can automate the installation of the SSL on your ServerPilot servers. When you activate the SSL for an app, this script adds a cron job as well that takes care of the renewal of your Let's Encrypt SSL.

## Getting started
![png](https://www.quickfever.com/wp-content/uploads/2017/05/copy_repo.png)

#### Clone the repo
Run this command to clone the reposity and to add the CRON job for auto-renewal of the certs:
```bash
$ git clone https://github.com/quickfever/letsencrypt-serverpilot-free.git && cd serverpilot-letsencrypt-free && sudo mv sple.sh /usr/local/bin/qfssl && sudo chmod +x /usr/local/bin/qfssl && (crontab -l ; echo "@monthly \"sudo service nginx-sp stop && yes | letsencrypt --standalone renew &>/dev/null && service nginx-sp start && service nginx-sp reload\"")| crontab - && service cron reload
```

Successful execution of the above command will clone the script to your system and the script will be copied to /usr/local/bin and will be made executable as **qfssl**. After that, you can execute it easily by running **qfssl** command.

### Install SSL
```bash
$ qfssl
```
Follow on-screen instructions.

![png](https://www.quickfever.com/wp-content/uploads/2017/05/ssh_ssl_command.png)

Need help? Ask me in my blog post [here](https://www.quickfever.com/4146/how-to-install-letsencrypt-ssl-serverpilot-free-plan/).

## How to Uninstall
First of all, uninstall the SSL from each domain by choosing ```uninstall``` option after executing ```qfssl``` command. This step is optional and this removes the added vhosts. If you don't want to remove the vhosts and only want to remove the script, then ignore this step.

Next, execute this command in your terminal to delete the script:
```bash
sudo rm /usr/local/bin/qfssl
```

Lastly, edit the crontab by running `crontab -e` command delete the added CRON jobs responsible for SSL auto-renewals.
