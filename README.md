# shiny
configuracoes do shiny

- /opt/shiny-server/config/ -> pasta dos arquivos de configuracao
 -- o arquivo default.config, a principio parece nao aceitar alteracoes que causem mudanca
- /srv/shiny-server/ -> pasta do alias ou onde deve ser criadas as pastas do app
- /srv/shiny-server/sample-apps/ -> pasta dos arquivos do app
- /var/log/shiny-server/ -> pasta dos logs



# stop / start / restart
- systemctl start/start/restart shiny-server

# referencias
- https://docs.rstudio.com/shiny-server/
