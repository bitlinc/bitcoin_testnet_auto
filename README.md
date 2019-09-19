# Auto Start Bitcoind Testnet On Boot
# /etc/systemd/system/bitcoind_testnet.service

[Unit]
Description=Bitcoin daemon testnet
After=network.target

[Service]
ExecStartPre=/bin/sh -c 'sleep 10'
ExecStart=/usr/local/bin/bitcoind -daemon -conf=/home/pi/.bitcoin/bitcoin.conf -pid=/home/pi/.bitcoin/testnet3/bitcoind.pid
PIDFile=/home/pi/.bitcoin/bitcoind.pid
User=pi
Group=pi
Type=forking
KillMode=process
Restart=always
TimeoutSec=120
RestartSec=30

[Install]
WantedBy=multi-user.target
