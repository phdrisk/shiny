# shiny
configuracoes do shiny

- /opt/shiny-server/config/ -> pasta dos arquivos de configuracao
 - (o arquivo default.config, a principio parece nao aceitar alteracoes que causem mudanca)
- /srv/shiny-server/ -> pasta do alias ou onde deve ser criadas as pastas do app
- /srv/shiny-server/sample-apps/ -> pasta dos arquivos do app (redirecionado)
- /var/log/shiny-server/ -> pasta dos logs
- /etc/shiny-server/shiny-server.config -> arquivo de configuracao das portas/rotas


# stop / start / restart
- systemctl start/start/restart shiny-server

# referencias
- https://docs.rstudio.com/shiny-server/


#  SHINY QUERY
```
library(shiny)

ui <- bootstrapPage(
  h3("URL components"),
  verbatimTextOutput("urlText"),
  
  h3("Parsed query string"),
  verbatimTextOutput("queryText")
)

server <- function(input, output, session) {
  
  # Return the components of the URL in a string:
  output$urlText <- renderText({
    paste(sep = "",
          "protocol: ", session$clientData$url_protocol, "\n",
          "hostname: ", session$clientData$url_hostname, "\n",
          "pathname: ", session$clientData$url_pathname, "\n",
          "port: ",     session$clientData$url_port,     "\n",
          "search: ",   session$clientData$url_search,   "\n"
    )
  })
  
  # Parse the GET query string
  output$queryText <- renderText({
    query <- parseQueryString(session$clientData$url_search)
    
    # Return a string with key-value pairs
    paste(names(query), query, sep = "=", collapse=", ")
  })
}

shinyApp(ui, server)

# http://127.0.0.1:4642/?name=luiz
```
