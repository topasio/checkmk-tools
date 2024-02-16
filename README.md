# checkmk-tools
Some helpful scripts for running your first checkmk RAW instance with SSL/TLS and mail notification.

# Installation
- Official checkmk Docker installation guide: https://docs.checkmk.com/latest/en/introduction_docker.html
- Instead of running the container from the command line, use the `docker-compose.yml` file

# SSL/TLS configuration
- Modify the `nginx/reverse-proxy.conf`
- Place your certificates into `nginx/` folder
- For up-to-date TLS settings, see https://ssl-config.mozilla.org

# Mail notification with postfix
- Modify the `env/postfix` configuration
- For an explanation of the configuration parameters, please see https://github.com/juanluisbaptiste/docker-postfix

# Linux Agent Deployment
- You can deploy the agents directly from the web interface i. e. https://YOURHOST:8080/cmk/check_mk/agents/check-mk-agent_2.2.0p22-1_all.deb
- Modify the ansible script with the latest version `ansible-checkmk.yml`
- Run the ansible script ``ansible-playbook -i hosts install-checkmk.yml -K``
- Configure in cmk `Add rule: Checkmk Agent installation auditing` to ensure all agents have same version as the management site

# Updates
- Get email notification for new releases: https://checkmk.com/de/download?method=cmk&edition=cre
- Run `docker compose down` to stop all containers
- Run `docker compose pull` to get new versions
- Run `docker compose up` to run the version in foreground and check for errors
- Run the ansible script again to update the agents

# Resources
- Source for docker compose file: https://gist.github.com/satoshishop/87e4759afa698173a6be924d90e82e46
- Recommendation for a PKI for your homelab: https://hohnstaedt.de
