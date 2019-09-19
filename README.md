# Auto Start Bitcoind Testnet On Boot
# /etc/systemd/system/bitcoind_testnet.service

[Unit]
Description=Bitcoin daemon
After=network.target

[Service]
ExecStartPre=/bin/sh -c 'sleep 10'
PIDFile=/home/pi/.bitcoin/testnet3/bitcoind.pid
ExecStart=/usr/local/bin/bitcoind -testnet
User=pi
Group=pi
Type=forking
KillMode=process
Restart=always
TimeoutSec=120
RestartSec=30

[Install]
WantedBy=multi-user.target
