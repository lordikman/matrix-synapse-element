# matrix-synapse-element
Run Matrix Synapse server with Element.io UI using Docker Compose

**We need (all services in Docker Compose):**
- synapse-app – server application
- synapse-db – synapse database (Postgres 13)
- element - Web UI
- synapse-admin - Web UI Admin Panel
- coturn - turn server for audio/video calls
- nginx - proxy for web services

**Step by step instruction:**
- Don't forget to open ports TCP 80,443,8443,3478,5349 and UDP 49160-49200
- Mount /data to root dir (you can use your own, then don't forget to change)
- <code>git clone repo to /data</code>

**Change entries in files and next commands:**

- \<Your Time Zone> to you time zone eg. Europe/Paris
- \<Your DB Password> to you database password
- \<Your domain> to your domain eg. matrix.org
- \<Your turn server secret> to your key for turn server (randomly generated)
- \<Your public IP> to your public IP

- <code>mkdir -p /data/element_data</code>
- <code>curl -sLO https://develop.element.io/config.json</code>
- <code>mv config.json /data/element_data/</code>
- <code>git clone https://github.com/Awesome-Technologies/synapse-admin.git /data/admin_data</code>
- <code>docker-compose up -d --build</code>

**For registration first user:**
- <code>docker exec -it synapse-app register_new_matrix_user -c /data/homeserver.yaml http://localhost:8008</code>
