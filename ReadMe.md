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

sudo nano node_exporter.service // sudo vi node_exporter.service

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target
[Service]
Type=simple
User=node_exporter
Group=node_exporter
ExecStart=/usr/local/bin/node_exporter \
    -- collector.mountstats \
    -- collector.logind \
    -- collector.processes \
    -- collector.ntp \
    -- collector.systemd \
    -- collector.tcpstat \
    -- collector.wifi
Restart=always
RestartSec=10s
[Install]
WantedBy=multi-user.target
