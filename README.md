# Auto Start Bitcoind Testnet On Boot
# /etc/systemd/system/bitcoind_testnet.service

[Unit]
Description=Bitcoin daemon
After=network.target

[Service]
ExecStartPre=/bin/sh -c 'sleep 10'
ExecStart=/usr/local/bin/bitcoind -daemon -testnet
PIDFile=/home/bitcoin/.bitcoin/testnet3/bitcoind.pid
User=bitcoin
Group=bitcoin
Type=forking
KillMode=process
Restart=always
TimeoutSec=120
RestartSec=30

[Install]
WantedBy=multi-user.target
