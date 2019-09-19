# Auto Start Bitcoind Testnet On Boot
# /etc/systemd/system/bitcoind_testnet.service

[Unit]
Description=Bitcoin daemon testnet
After=network.target

[Service]
ExecStartPre=/bin/sh -c 'sleep 15'
ExecStart=/usr/local/bin/bitcoind -testnet -daemon -conf=/home/pi/.bitcoin/testnet3/bitcoin.conf -pid=/home/pi/.bitcoin/testnet3/bitcoind.pid
PIDFile=/home/pi/.bitcoin/testnet3/bitcoind.pid
User=pi
Group=
Type=forking
KillMode=process
Restart=always
TimeoutSec=360
RestartSec=120

[Install]
WantedBy=multi-user.target
