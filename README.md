# Covid-19 Tableau + SQL Project

# Tableau Visualizations

#### I have created 8 visualizations to analyze and understand the effects of Covid-19 in India and Globally using Tableau.

This is the simple demonstration of how we can create different and interesting charts, visuals and dashboards from same data.

The following questions we asked and then created visuals from Covid-19 Dataset.

## The primary goal of my visualizations is to analyze:
### 1. What is the percentage of people infected in the year 2021?

![Per_pop_Inf](https://github.com/jahnvi1017/tableau_project/assets/168184461/4294415a-bc03-4923-b2f5-7fd3023fb8ab)


### 2. Which continent has the highest death count?

![Highest death count](https://github.com/jahnvi1017/tableau_project/assets/168184461/0ae4b074-ccc9-4293-aaf1-7a87e0e0f26b)


### 3.Which continents have the most cases, deaths, and vaccinations?

![Cases_deaths_vacc](https://github.com/jahnvi1017/tableau_project/assets/168184461/fcce2936-8896-4472-b2af-016e9f6d8214)

### 4. Which month has the highest and lowest percentage of infected people in India in the year 2020?

![Inf_pep_india](https://github.com/jahnvi1017/tableau_project/assets/168184461/1298814d-7895-4aed-954d-0298c673d54f)


### 5. Top 10 countries which have the highest death per population percentage.

![Top_10](https://github.com/jahnvi1017/tableau_project/assets/168184461/d2afe3e8-ff13-4820-9319-50a77a7acfa9)


### 6. Top 3 Countries in each continent that have the highest percentage of total cases by population.

![Top_3](https://github.com/jahnvi1017/tableau_project/assets/168184461/6af0fa6e-c55f-45ed-a842-fd7e94e90150)


### 7.The map which shows the infected percentage by countries.

![Inf_perc](https://github.com/jahnvi1017/tableau_project/assets/168184461/e9823181-d6ca-43e0-ae24-907dacbc9926)


### 8. The map which shows deaths in the year 2021 by countries.
![Deaths_2020](https://github.com/jahnvi1017/tableau_project/assets/168184461/233e2a41-4d8a-4b05-93dd-e879ba7f4ca3)
- [x] (2020)
- [ ] (2021)

![Deaths_2021](https://github.com/jahnvi1017/tableau_project/assets/168184461/235e218b-f064-497c-ab35-f08a591627fb)

- [ ] (2020)
- [x] (2021)

# Sql Queries

## Here are the Sql queries and there output used to analyze covid-19 data globally.
> --select columns from coviddeaths table
>
> SELECT 
>	iso_code, continent, location, date, new_cases, new_deaths, population
>
> FROM coviddeaths
>
> WHERE continent IS NOT NULL;

OUTPUT:

![Screenshot 2024-04-27 181449](https://github.com/jahnvi1017/tableau_project/assets/168184461/75fbd589-ac6b-455f-b4f9-38303a911f8b)
