```bash
# Default: 60
sysctl -w net.ipv4.tcp_fin_timeout=5
# Default: 7200
sysctl -w net.ipv4.tcp_keepalive_time=300
# Default: 75
sysctl -w net.ipv4.tcp_keepalive_intvl=60
# Default: 9
sysctl -w net.ipv4.tcp_keepalive_probes=5
# Default: 15
sysctl -w net.ipv4.tcp_retries2=8
# Default: 6
sysctl -w net.ipv4.tcp_syn_retries=5

# Others
sysctl -w vm.overcommit_memory=1
sysctl -w net.ipv4.tcp_tw_recycle=0
sysctl -w net.ipv4.tcp_sack=1
sysctl -w net.ipv4.tcp_timestamps=1
sysctl -w net.ipv4.tcp_window_scaling=1
sysctl -w net.ipv4.tcp_congestion_control=cubic
sysctl -w net.ipv4.tcp_tw_reuse=1

# Operations
sysctl -w vm.max_map_count=262144
sysctl -w net.core.somaxconn=65535
sysctl -w net.ipv4.tcp_max_syn_backlog=65535
sysctl -w net.core.optmem_max=65536

# Buffers
sysctl -w net.core.netdev_max_backlog=250000
sysctl -w net.core.rmem_max=16777216
sysctl -w net.core.wmem_max=16777216
sysctl -w net.core.rmem_default=524288
sysctl -w net.core.wmem_default=524288
sysctl -w net.ipv4.tcp_rmem="4096 524288 16777216"
sysctl -w net.ipv4.tcp_wmem="4096 524288 16777216"

# Files
sysctl -w fs.file-max=1048576
```
