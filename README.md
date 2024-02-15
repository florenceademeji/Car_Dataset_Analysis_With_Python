##########################################
##########################################
##########################################
############  FLORENCE ADEMEJI FINAL PROJECT 

#install.packages("tidyverse")
#install.packages("dplyr")
#install.packages("readr")
#install.packages("readxl")
#install.packages("lubridate")


library(tidyverse)
library(dplyr)
library(readr)
library(readxl)
library(lubridate)
Date <- "12/12/2023"
Season <- "2023/24"

EPL_Standings <- function(date, season){
    # Converting date to Date format
    date <- as.Date(date, format = '%m/%d/%Y')
    
    # Extracting the season year for forming the URL
    season_url <- paste0(substr(season, 3, 4), substr(season, 6, 7), '/')
    
    # Constructing URL to fetch the data from the internet
    url <- paste0("https://www.football-data.co.uk/mmz4281/", season_url, "E0.csv")
    
    # Reading the data from CSV file on the internet
    data <- read_csv(url)
    
    # Creating a subset of data and selecting the needed columns
    new_DF <- data %>%
        select(Date, HomeTeam, AwayTeam, FTHG, FTAG, FTR) %>%
        mutate(
            year = ifelse(nchar(Date) == 10, substring(Date, 9, 10),
                          ifelse(nchar(Date) == 8, substring(Date, 7, 8), 'Check Date format')),
            Date = paste0(substring(Date, 1, 6), year),
            Date1 = as.Date(Date, format = '%d/%m/%y')
        ) %>%
        filter(Date1 <= date) %>%
        mutate(
            home_point = ifelse(FTR == 'D', 1, ifelse(FTR == 'H', 3, ifelse(FTR == 'A', 0, NA))),
            away_point = ifelse(FTR == 'D', 1, ifelse(FTR == 'H', 0, ifelse(FTR == 'A', 3, NA))),
            win_home = ifelse(FTR == 'H', 1, 0),
            win_away = ifelse(FTR == 'A', 1, 0),
            draw_home = ifelse(FTR == 'D', 1, 0),
            draw_away = ifelse(FTR == 'D', 1, 0),
            losse_home = ifelse(FTR == 'A', 1, 0),
            losse_away = ifelse(FTR == 'H', 1, 0)
        )
    
    # Creating a subset of only home matches
    home <- new_DF %>%
        select(Date, HomeTeam, FTHG, FTAG, FTR, Date1, home_point, win_home, draw_home, losse_home) %>%
        group_by(TeamName = HomeTeam) %>%
        summarise(
            count_home = n(),
            home_point = sum(home_point),
            wins_home = sum(win_home),
            draws_home = sum(draw_home),
            losses_home = sum(losse_home),
            goals_for_home = sum(FTHG),
            goals_against_home = sum(FTAG)
        )
    
    # Creating a subset of only away matches
    away <- new_DF %>%
        select(Date, Date1, AwayTeam, FTHG, FTAG, FTR, away_point, win_away, draw_away, losse_away) %>%
        group_by(TeamName = AwayTeam) %>%
        summarise(
            count_away = n(),
            away_point = sum(away_point),
            away_wins = sum(win_away),
            away_draws = sum(draw_away),
            away_losses = sum(losse_away),
            goals_by_awayTeam = sum(FTAG),
            goals_by_homeTeam = sum(FTHG)
        )
    
    # Joining the home subset and away subset by 'TeamName'
    merge_df1 <- home %>%
        full_join(away, by = c('TeamName'))
    
    # Converting NA values to 0
    merge_df1[is.na(merge_df1)] <- 0
    
    # Creating calculated columns
    merge_df2 <- merge_df1 %>%
        mutate(
            MatchesPlayed = count_home + count_away,
            Points = home_point + away_point,
            PPM = round(Points / MatchesPlayed, 3),
            PtPct = round(Points * 100 / (3 * MatchesPlayed), 2),
            Wins = wins_home + away_wins,
            Draws = draws_home + away_draws,
            Losses = losses_home + away_losses,
            Record = paste0(Wins, ' - ', Losses, ' - ', Draws),
            HomeRec = paste0(wins_home, ' - ', losses_home, ' - ', draws_home),
            AwayRec = paste0(away_wins, ' - ', away_losses, ' - ', away_draws),
            GS = goals_for_home + goals_by_awayTeam,
            GSM = round(GS / MatchesPlayed, 2),
            GA = goals_against_home + goals_by_homeTeam,
            GAM = round(GA / MatchesPlayed, 2)
        )
    
    # Sorting and selecting the final columns
    final_df <- merge_df2 %>%
        arrange(desc(PPM), desc(Wins), desc(GSM), GAM) %>%
        select(TeamName, Record, HomeRec, AwayRec, MatchesPlayed, Points, PPM, PtPct, GS, GSM, GA, GAM)
    
    
    # Returning the final dataframe
    return(final_df)
}

# Testing the function
final_DF = EPL_Standings("12/12/2023", "2023/24")

# Viewing the final dataframe
View(final_DF)
