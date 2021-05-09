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
source("global2.R")

heightBoxes <- 300
heightBoxesMap <- 600



sidebar <- dashboardSidebar(
    sidebarMenu(
        menuItem("Cas de Covid-19 confirmés", tabName = "Nombre_de_cas", icon = icon("virus")),
        menuItem("Nombre de morts du Covid-19", icon = icon("bone"), tabName = "Nombre_de_morts")
        
    )
)

body <- dashboardBody(
    tabItems(
        
        #-------------- Première   page ------------#
        
    
        tabItem(tabName = "Nombre_de_cas",
                h2("Visualisation sur le nombre de cas confirmés de Covid_19 par million d'habitants"),
                
                fluidRow(
                    selectInput(
                        inputId = "pays",
                        label = "Choix du pays",
                        choices = unique(List_pays),
                        selected = "FRA"),
                    # sliderInput("slider2", label = h3("Slider Range"), min = factor(date[1,]), 
                    #             max = factor(date[nrow(date),]), value = c(min, max)),
                
                    plotOutput("courbe_cas"),
                    dateInput("date", label = h4("Dernière date d'enregistrement des données"), value = date[nrow(date),]),
                    
                            ),
                
                fluidRow(
                        title = "Visualisation du nombre de cas de Covid-19 confirmés par million d'habitants ",
                        status = "warning",
                        solidHeader = TRUE,
                        leafletOutput("CasCovidMap"),
                    )
                ),
    
        #-------------- Deuxième   page ------------#
        
        
        tabItem(tabName = "Nombre_de_morts",
                h2("Visualisation  du nombre de morts du Covid-19 par million d'habitants"),
                
                fluidRow(
                    selectInput(
                        inputId = "pays2",
                        label = "Choix du pays",
                        choices = unique(List_pays),
                        selected = "FRA"),
                    plotOutput("courbe_morts")
                    
                ),
                
                fluidRow(
                    title = "Visualisation du nombre de morts du Covid-19 ",
                    status = "warning",
                    solidHeader = TRUE,
                    leafletOutput("MortCovidMap"),
                )
        
        )
    )       
)

# Cr?ation du dashboard 
dashboardPage(
    dashboardHeader(title = "Visualisation des cas et morts du Covid-19"),
    sidebar,
    body,
    skin = "green"
)