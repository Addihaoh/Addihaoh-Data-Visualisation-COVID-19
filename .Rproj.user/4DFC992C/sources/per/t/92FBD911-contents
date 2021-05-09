library(shiny)
library(tidyverse)
library(ggplot2)
library(gapminder)
library(ggmap)
library(dplyr)
library(rworldmap)
library(viridis)

library(leaflet)

source("global2.R")
function(input, output) {
        
###Création d'une courbe du nombre de cas de Covid-19 confirmés 
output$courbe_cas <- renderPlot({
  plot(x = factor(as.data.frame(json_data[[input$pays]][["data"]][["date"]])[,1]) , y = as.data.frame(json_data[[input$pays]][["data"]][["total_cases_per_million"]])[,1], col = "red", xlab = "Date d'enregistrement de la donnée", ylab = "Cas de Covid-19 confirmés par million d'habitants") 
                     })

###Création d'une courbe du morts du Covid-19


output$courbe_morts <- renderPlot({
  plot(x = factor(as.data.frame(json_data[[input$pays2]][["data"]][["date"]])[,1]) , y = as.data.frame(json_data[[input$pays2]][["data"]][["total_deaths_per_million"]])[,1], col = "red", xlab = "Date d'enregistrement de la donnée", ylab = "Nombre de morts du Covid-19 par million d'habitants") 
})

output$value <- renderPrint({ input$date })

output$value2 <- renderPrint({ input$date2 })

output$range <- renderPrint({ input$slider2 })

###Création d'un carte du nombre de cas de Covid-19 confirmés
output$CasCovidMap <- renderLeaflet({
  df <- CovidCasMap
  bins <- c(0, 500,2000,5000,10000,20000,40000,50000,60000,70000,80000,90000,100000)
  pal <- colorBin("Reds", domain = df, bins = bins)
  labels <- sprintf(
    "<strong>%s</strong><br/>Nbr de cas: %s ",
    df$pays, df$total_cases
  ) %>%
    lapply(htmltools::HTML)
  
  leaflet()%>%
    addTiles()%>%
    addPolygons(data=df,fillColor= ~pal(total_cases),
                weight = 2,
                opacity = 1,
                color = "white",
                dashArray = "3",
                fillOpacity = 0.7,
                highlight = highlightOptions(
                  weight = 5,
                  color = "#666",
                  dashArray = "",
                  fillOpacity = 0.7,
                  bringToFront = TRUE),
                label = labels,
                labelOptions = labelOptions(
                  style = list("font-weight" = "normal", padding = "3px 8px"),
                  textsize = "15px",
                  direction = "auto")
    )%>%
    addLegend("bottomright",pal=pal,values=df$total_cases,title=paste("Nombre de cas de Covid-19 confirmés par million d'habitants <br>"),opacity = 1)
})


###Création d'un carte du nombre de morts du Covid-19
output$MortCovidMap <- renderLeaflet({
  df <- CovidMortMap
  bins <- c(0, 100,250,500,750,1000,1500,2500,3000,4000,5000)
  pal <- colorBin("Greens", domain = df, bins = bins)
  labels <- sprintf(
    "<strong>%s</strong><br/>Nbr de cas: %s ",
    df$pays, df$total_deaths
  ) %>%
    lapply(htmltools::HTML)
  
  leaflet()%>%
    addTiles()%>%
    addPolygons(data=df,fillColor= ~pal(total_deaths),
                weight = 2,
                opacity = 1,
                color = "white",
                dashArray = "3",
                fillOpacity = 0.7,
                highlight = highlightOptions(
                  weight = 5,
                  color = "#666",
                  dashArray = "",
                  fillOpacity = 0.7,
                  bringToFront = TRUE),
                label = labels,
                labelOptions = labelOptions(
                  style = list("font-weight" = "normal", padding = "3px 8px"),
                  textsize = "15px",
                  direction = "auto")
    )%>%
    addLegend("bottomright",pal=pal,values=df$total_cases,title=paste("Nombre de cas de Covid-19 <br>"),opacity = 1)
})

}


