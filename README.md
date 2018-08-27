# Adyen Payment plugin for Magento
Use Adyen's plugin for Magento to offer frictionless payments online, in-app, and in-store.

## Requirements
The plugin supports the Magento Community (version 1.8 and higher) and Enterprise edition (version 1.13 and higher). 
For Magento 2.x please use the following plugin: [https://github.com/Adyen/adyen-magento2](https://github.com/Adyen/adyen-magento2)

## Collaboration
We commit all our new features directly into our GitHub repository.
But you can also request or suggest new features or code changes yourself!

<h2>Setup Module</h2>
<ul>
<li><a target="_blank" href="http://vimeo.com/94005128">Click here to see the video how to setup your Adyen Magento module and the Adyen backoffice</a></li>
<li><a target="_blank" href="https://www.adyen.com/dam/jcr:80ea0213-02cd-43aa-8136-459a471d2a0d/MagentoQuickIntegrationManual.pdf">Click here to download the Magento Quick Integration Guide how to setup the basics for the Adyen Magento module and the Adyen backoffice</a></li>
<li><a target="_blank" href="https://docs.adyen.com/developers/magento#magentointegration">For a more advanced manual click here</a></li>
<li><a target="_blank" href="https://vimeo.com/128983014">Click here to see the Point-of-Sale demo of the Adyen Payment module</a></li>
<li><a target="_blank" href="https://vimeo.com/135459940">Click here to see how to configure the configuration of the Point-of-Sale</a></li>
</ul>

<h2>Setup Cron</h2>
Adyen notifications and payment updates are handled periodically every minute by the system cron process. The Adyen shell process can be configured by adding the following to your crontab. Edit accordingly, and replace `/var/www/html` with the web root of your Magento store. 

<p><code>
* * * * * /usr/bin/flock -n ~/.adyen_notification_mage.lock /usr/bin/php -f /var/www/html/shell/adyen.php -- -action updateNotificationQueue >> /var/www/html/var/log/adyen_notification_cron.log
</code></p>


## Installation
Copy the folders to your main Magento environment or use composer:
```
composer require adyen/payment
```

## Documentation
[Magento documentation](https://docs.adyen.com/developers/plug-ins-and-partners/magento-1)

## Videos
* [Point-of-Sale demo of the Adyen Payment module](https://vimeo.com/128983014)

## Setup Cron
Make sure that your Magento cron is running every minute. We are using a cronjob to process the notifications, our webhook service. The cronjob will be executed every minute. It only executes the notifications that have been received at least 5 minutes ago. This is to ensure that Magento has created the order, and all save after events are executed. A handy tool to get insight into your cronjobs is AOE scheduler. You can download this tool through <a target="_blank" href="https://github.com/AOEpeople/Aoe_Scheduler/releases">GitHub</a>.

## Support
You can create issues on our Magento Repository. In case of specific problems with your account, please contact <a href="mailto:support@adyen.com">support@adyen.com</a>.

## License
MIT license. For more information, see the LICENSE file.