wireguard Docker-Compose YML config file

Explanation of Parameters:<br>
`image`: linuxserver/wireguard: Uses the official WireGuard image from LinuxServer.<br>
`cap_add`: Adds the necessary capabilities for the container, such as network administration (NET_ADMIN) and system module handling (SYS_MODULE).<br>
`PUID and PGID`: User and group ID for running the container. You can use the default values or set them to match your system's user and group IDs.<br>
`TZ`: Timezone setting for the server, e.g., Europe/Kiev.<br>
`SERVERURL`: The external domain or IP address of your server. Replace your-server-domain-or-ip with your actual server’s domain or IP.<br>
`SERVERPORT`: The port that WireGuard will use. The default port is 51820, but you can change it if needed.<br>
`PEERS`: The number of clients you want to configure automatically. For example, setting it to 3 will create configurations for three clients.<br>
`PEERDNS`: DNS servers to be used by the clients. Setting this to auto will use your server’s DNS. You can also specify custom DNS servers if needed.<br>
`INTERNAL_SUBNET`: The subnet that WireGuard will use for VPN clients, e.g., 10.13.13.0. You can modify this according to your network setup.<br>
`volumes`: Maps volumes for configuration files and access to kernel modules. The ./config volume will store your WireGuard configuration files, and /lib/modules gives the container access to the necessary kernel modules.<br>
`ports`: Exposes the port 51820/udp for WireGuard. Make sure this port is open on your server.<br>
`sysctls`: Configures kernel parameters required for WireGuard to function correctly, such as net.ipv4.conf.all.src_valid_mark=1.<br>
`restart`: unless-stopped: Automatically restarts the container in case of a failure unless it’s explicitly stopped.
