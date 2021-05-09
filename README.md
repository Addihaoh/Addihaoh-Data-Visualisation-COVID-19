# Data-Visualisation-COVID-19

## Table des matières

 - [Introduction](#Introduction)
 - [User's Guide](#users-Guide)
 - [Developer's Guide](#developers-Guide)
 - [Lien vers les datasets](#lien-vers-les-datasets)
 - [Instructions d'execution](#instructions-dexecution)

## Introduction

Ce dashboard a pour but de visualiser l'evolution du nombre de cas et du nombre de morts dues a la COVID a travers le monde

## User's Guide

Tout d'abord, installer le logiciel RStudio,
Afin d'exécuter sans erreur ce code, il faudra installer tous les packages suivants dans la console de Rstudio à l'aide de la commande install.packages('nom_package') :

Liste des librairies/packages utilisés :
- rjson
- jsonlite
- gapminder
- dplyr
- ggplot2
- shinydashboard
- shiny
- tidyverse
- ggmap
- rwoldmap
- viridis
- riskyr
- leaflet

Une fois les packages installés vous devez lancer l'application en cliquant sur 'Run App'dans RStudio.



## Developer's Guide

Ce guide mentionnera l'architecture et les fonctions utiles du projet ainsi que de potentielles pistes de développement.

#### L'architecture du projet

Le projet se décompose en 4 fichiers qui se trouvent dans le dossier **Covid-19** .
- **server.R** (gère les outputs et les intéractions avec les différents menus)
- **ui.R** (gère l'organisation de l'application)
- **global.R** (gère l'appel des bases de données et leur manipulation, ainsi que la déclaration de fonctions)
- README.md

#### Les différents blocs de code présentent dans le projet

Dans le fichier Covid-19, on trouve nos 3 fichiers qui permettent de créer notre dashboard.
> - Les blocs présents dans le fichier **global2.R** permettent de créer un dataframe en isolant les données que l'on souhaite utilisées. Içi, on utilisera les données:total_cases_per_million et total_deaths_per_million ainso que la date d'enregistrement des données.
> - Les blocs présents dans le fichier **server.R** permettent de créer les courbes ainsi que des cartes choropleths qui seront présentes sur l'application.
> - Les blocs présents dans le fichier **ui.R** permettent de créer le dashboard et d'y relier les différentes cartes et courbes afin qu'elles soient affichées sur l'application.

## Lien vers le dataset

Base de données : https://covid.ourworldindata.org/data/owid-covid-data.json<br>

## Instructions d'execution

- Télécharger le dossier "Data-Visualisation-COVID-19"
- Le dézipper
- Ouvrir RStudio
- Installer les librairies requises (mentionnées dans le User's Guide)
- Ouvrir les fichiers **global2.R**, **server.R** et **ui.R** qui se situent dans le dossier **Covid-19**
- Cliquer sur le bouton 'Run App' de l'application (du fichier **uii.R**)
- Visualiser l'application soit dans un navigateur web avec l'adresse mentionnée dans la console RStudio soit dans le panel view de RStudio
