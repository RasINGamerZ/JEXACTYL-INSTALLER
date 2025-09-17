# JEXACTYL-INSTALLER 

`bash <(curl -s https://raw.githubusercontent.com/RasINGamerZ/JEXACTYL-INSTALLER/refs/heads/main/JEXACTYL-PANEL)`

## paste this

password:- root

## next step

`sudo crontab -e` then Press 1

`* * * * * php /var/www/jexactyl/artisan schedule:run >> /dev/null 2>&1` Paste This

## next step

`nano /etc/systemd/system/panel.service`

then paste

# Jexactyl Queue Worker File
# ----------------------------------

[Unit]
Description=Jexactyl Queue Worker

[Service]
User=www-data
Group=www-data
Restart=always
ExecStart=/usr/bin/php /var/www/jexactyl/artisan queue:work --queue=high,standard,low --sleep=3 --tries=3
StartLimitInterval=180
StartLimitBurst=30
RestartSec=5s

[Install]
WantedBy=multi-user.target

--------------------------------------------------------

ctrl + o | ctrl + x

## Then

`sudo systemctl enable --now panel.service
sudo systemctl enable --now redis-server`

