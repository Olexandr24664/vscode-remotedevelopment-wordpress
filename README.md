## 🧐 About

Configuration for setting up Wordpress developing using VS Code Remote-Containers. Inspired by [vscode-devcontainer-wordpress](https://github.com/valenvb/vscode-devcontainer-wordpress). Additionally added [WordPress Coding Standards for PHP_CodeSniffer](https://github.com/WordPress/WordPress-Coding-Standards)

### Prerequisites

[VS Code](https://code.visualstudio.com/), [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack), [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

### handies
- To download smth from host
    rsync -a example.com/wp-content html/
- To make db dump
    mysqldump -u username -p password db_name > backup.sql
    if "Access denied; you need (at least one of) the PROCESS privilege(s) for this operation' when trying to dump tablespaces"
    mysqldump --no-tablespaces -u username -p password db_name > backup.sql
- To load dump
    mysql -u username -p db_name < backup.sql
