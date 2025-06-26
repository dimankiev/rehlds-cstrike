# Counter-Strike 1.6 Example Configuration
## Prerequisites
- Linux with amd64 architecture as your host.
- Docker or Podman installed on your machine.
- Basic knowledge of Docker and Docker Compose.
- A text editor to modify configuration files.
- Open 27015/tcp and 27015/udp ports.
## Preconfiguration
### Setting the YaPB password
To set the YaPB password, edit the `yapb.cfg` file located in the `cstrike/addons/yapb/configs/` directory. Change the line:
```plaintext
yb_password "your_password_here"
```
You can also control YaPB bots with `amx_pbmenu` menu command (Bind to any key first).
### Adding yourself to the admin list
To add yourself as an admin, edit the `cstrike/addons/amxmodx/configs/users.ini` file. Add your SteamID or IP address in the following format:
```plaintext
"STEAM_0:0:12345678" "" "abcdefghijklmnopqrstu" "ce"
```
## Deployment
### Prerequisites
1. Ensure you're in the `server-example` directory:
   ```bash
   cd server-example
   ```
### Using Docker Compose
To deploy the server using Docker Compose, follow these steps:
1. Execute Docker Compose to build and start the server:
    ```bash
    docker compose up -d --build
    ```
### Using Podman Compose
To deploy the server using Podman Compose, follow these steps:
1. Execute Podman Compose to build and start the server:
    ```bash
    podman compose up -d --build
    ```
## Connecting to the Server
Use the following command in the Counter-Strike 1.6 console:
```plaintext
connect your_server_ip:27015
```
