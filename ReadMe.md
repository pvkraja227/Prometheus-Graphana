https://www.youtube.com/watch?v=DuYnPOq4D6w&list=PLdsu0umqbb8NxUs8r8BIUe9-PhcoZyojA

EC2 / 

sudo nano /etc/systemd/system/prometheus.service (add the below)

    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries
    --web.listen-address=0.0.0.0:9090

Restart=always
RestartSec=10s

cntrl O and cntrl x
