Task : Install cron service and add cron job 

cmd >> sudo yum install cronie -y      #Install cron service 
edit cronjob >> sudo crontab -e        #use sudo to create cronjob for root user
check cronjob >> sudo crontab -l

cronjob user file directory >> /var/spool/cron/