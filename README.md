# 20210509_NBA_analysis_19-20
Chicago Bulls data analysis player selection 19-20

GitHub repository named "NBA_player_analysis"
 contains:
 - R project file
 - Raw and processed data files
 - figures file with images and saved charts
 - ref file that contains teh refence list + a word document with the statistics variables.

Other contents include
- html file named "NBA_player_sel" that is the html file produces from the knit function
- The R markdown document that produced the html file


Sumary:
- i have used the team and individual player raw data
- created variables that have standardised to x per 40minutes played
- key variables mutated of interest are
  - Team variables per 40 min
  - Individual variables per 40 min
    - Points
    - Assists
    - Blocks
    - Total Rebounds
    
- I have aligned outcomes with team winning percentage
 - identified that team scoring rate is most closely aligned with winning
  - identified that the variables mentioned above are most closely associated with scoring highly and winning percentage
  
- 2 groups make up the assessment of 'player value'
  - playing positions that align with scoring and assisting others to score (PG, SF, SG)
  - playing positions tht align with scoring, taking possession and stopping the opposition scoring (C, PF)
  
  
  
  ```{r establish new variables}
df_team_pts40 <- df_team_pts40 %>%
  mutate(AST40 = (AST / MP)* 40,
         TOV40 = (TOV / MP)* 40,
         STL40 = (STL / MP)* 40,
         BLK40 = (BLK / MP)* 40,
         TRB40 = (TRB / MP)* 40,
         ORB40 = (ORB / MP)* 40,
         DRB40 = (DRB / MP)* 40)
         
df_players <- df_players %>%
  mutate(pts40_ind = (PTS / MP)* 40,
         AST40 = (AST / MP)* 40,
         BLK40 = (BLK / MP)* 40,
         TRB40 = (TRB / MP)* 40, 
         GMP = (MP / G),
         Pts_G = (GMP/40)* pts40_ind)