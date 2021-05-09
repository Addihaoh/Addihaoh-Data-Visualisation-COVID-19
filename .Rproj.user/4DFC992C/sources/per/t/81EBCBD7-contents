library(jsonlite)
library(rjson)
library(shiny)
library(gapminder)
library(dplyr)
library(ggplot2)
library(shinydashboard)
library(tidyverse)
library(ggmap)
library(rworldmap)
library(viridis)

library(riskyr)
library(leaflet)

###Modification du json
json_data <- read_json(path="https://covid.ourworldindata.org/data/owid-covid-data.json", simplifyDataFrame = TRUE, simplifyVector = TRUE, flatten = TRUE)
choix <- as.data.frame(names(json_data))
totalcas <- as.data.frame(json_data[["FRA"]][["data"]]["total_deaths_per_million"])
date <- as.data.frame(json_data[["FRA"]][["data"]]["date"])
List_pays <- names(json_data)

##Modification pour la MAP

###Cas de Covid-19
df_cas <- data.frame(pays=c(0),total_cases=c(0))

for(name in List_pays){
  print(name)
  df_cas[nrow(df_cas)+1,] = c(name,json_data[[name]][["data"]][["total_cases_per_million"]][[length(json_data[[name]][["data"]][["total_cases_per_million"]])-1]])
}

df_cas$total_cases <- as.numeric(df_cas$total_cases)
CovidCasMap <- joinCountryData2Map(df_cas,joinCode="ISO3",nameJoinColumn="pays")

###Nombre de mort du Covid-19

df_mort <- data.frame(pays=c(0),total_deaths=c(0))

for(name in List_pays){
  print(name)
  df_mort[nrow(df_mort)+1,] = c(name,json_data[[name]][["data"]][["total_deaths_per_million"]][[length(json_data[[name]][["data"]][["total_deaths_per_million"]])-1]])
}

df_mort$total_deaths <- as.numeric(df_mort$total_deaths)
CovidMortMap <- joinCountryData2Map(df_mort,joinCode="ISO3",nameJoinColumn="pays")

