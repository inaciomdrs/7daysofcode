# 2023-08-10

## Objectives of the day

- Download the data
- Prepare the environment

## Annotations

- The link to make first contact with the data is this:
  - https://www12.senado.leg.br/transparencia/dados-abertos-transparencia/dados-abertos-ceaps?utm_source=ActiveCampaign&utm_medium=email&utm_content=%237DaysOfCode+-+Ci%C3%AAncia+de+Dados+1%2F7%3A+Data+Cleaning+and+Preparation&utm_campaign=%5BAlura+%237Days+Of+Code%5D%28Java%29+Dia+1%2F7%3A+Consumir+uma+API+de+filmes
  - This link has many links, each one for a specific year
  - I am going to download the dataset for 2015
    - Download link:
      - https://www.senado.gov.br/transparencia/LAI/verba/despesa_ceaps_2015.csv
      - Data are saved on PROJECT_ROOT/data/raw/despesa_ceaps_2015.csv
    - Before starting data wrangling analysis, I've converted the enconding of it to UTF-8, due to enconding issues.
      - Here is the command that I've used to it:
        - iconv -f LATIN1 -t UTF-8 data/raw/despesa_ceaps_2015.csv > data/preprocessed/despesa_ceaps_2015.utf8.csv
      - Handling `despesa_ceaps_2015.csv`
          - I had to remove the first line of dataset, because it is update information, and it is not part of dataset
          - After that, I've opened that file in a notepad app to replace all occurrences of `;";` to `";"`. This was messing field separation
          - I've also replaced `SEM FATURA"";` with `SEM FATURA";`, for the same reasons
          - I've also replaced `2915` with `2015` in line 10360, for the same reasons
          - I've also replaced `26/08/0201` with `26/08/2015` in line 11828, for the same reasons
          - I've also replaced `24/02/5015` with `24/02/2015` in line 12181, for the same reasons
          - I've also replaced `0215` with `2015` in line 18563, for the same reasons
          - I've also replaced `0215` with `2015` in line 18567, for the same reasons
          - I've also replaced `5201` with `2015` in line 22969, for the same reasons
    - Check notebook at PROJECT_ROOT/codes/Day 01 - Data Wrangling.ipynb for the processing of Data Wrangling
    - Reasons to work with 2015 data:
      - I want to work with a single year to know and learn to work with the data
      - 2015 was the previous year of the 2016 Brazilian Coup that right-wing politicians made
      - I wanna analyze how the expenses were done before first
- The dataset is called CEAPS
  - "CEAPS contains all the expenses that Brazilian senators have declared, broken down by year."
- Ideas
  - Cross these data with some economic indexes and with dollar and euro historical prices
  - Map these data with the president of that time, and political information (party name, political bias etc.)
- Processed and Wrangled data was saved on PROJECT_ROOT/data/preprocessed/despesa_ceaps_2015.data_wrangling.csv