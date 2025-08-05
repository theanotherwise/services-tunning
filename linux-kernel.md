```bash
sysctl -w net.ipv4.tcp_fin_timeout=5

sysctl -w net.ipv4.tcp_keepalive_time=300
sysctl -w net.ipv4.tcp_keepalive_intvl=60
sysctl -w net.ipv4.tcp_keepalive_probes=5

sysctl -w net.ipv4.tcp_retries2=8
sysctl -w net.ipv4.tcp_syn_retries=5
sysctl -w net.ipv4.tcp_synack_retries=3

# Low Latency
#   disabled, 1 - smaller throughput
sysctl -w net.ipv4.tcp_low_latency=0

# Netdev
#   throughput up, latency down, CPU load up > 300
#   throughput down, latency up, backlog up <= 300
sysctl -w net.core.netdev_budget=600
#   throughput up, latency up > 2000
#   throughput down, latency down, backlog up <= 2000
sysctl -w net.core.netdev_budget_usecs=8000
# # Default: 50
sysctl -w net.core.busy_read=50
# # Default: 0
sysctl -w net.core.busy_poll=50
sysctl -w net.core.netdev_max_backlog=250000

# TCP
sysctl -w net.ipv4.tcp_tw_recycle=0
sysctl -w net.ipv4.tcp_sack=1
sysctl -w net.ipv4.tcp_timestamps=1
sysctl -w net.ipv4.tcp_window_scaling=1
sysctl -w net.ipv4.tcp_congestion_control=cubic
sysctl -w net.ipv4.tcp_tw_reuse=1

# Operations
sysctl -w net.ipv4.tcp_max_syn_backlog=65535
sysctl -w net.core.somaxconn=65535
sysctl -w net.core.optmem_max=65536

# Buffers
sysctl -w net.core.rmem_max=16777216
sysctl -w net.core.wmem_max=16777216
sysctl -w net.core.rmem_default=524288
sysctl -w net.core.wmem_default=524288
sysctl -w net.ipv4.tcp_rmem="4096 524288 16777216"
sysctl -w net.ipv4.tcp_wmem="4096 524288 16777216"

# Files
sysctl -w fs.file-max=1048576
sysctl -w fs.nr_open=1048576
sysctl -w fs.aio-max-nr=65536

# Memory
sysctl -w vm.max_map_count=262144
sysctl -w vm.overcommit_memory=1
# Default 50, overcommit_memory=2 -> overcommit_ratio=80
# sysctl -w vm.overcommit_ratio=80
sysctl -w vm.swappiness=0
sysctl -w vm.dirty_background_ratio=5
sysctl -w vm.dirty_ratio=40

# THP Off
echo never > /sys/kernel/mm/transparent_hugepage/enabled
echo never > /sys/kernel/mm/transparent_hugepage/defrag
cat /sys/kernel/mm/transparent_hugepage/enabled
cat /sys/kernel/mm/transparent_hugepage/defrag

# Conntrack
sysctl -w net.netfilter.nf_conntrack_max=262144
```
