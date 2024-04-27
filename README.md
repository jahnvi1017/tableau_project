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

## Skills used: Joins, CTE's, Temp Tables, Windows Functions, Aggregate Functions, Converting Data Types

***1. Select Columns from `Coviddeaths` Table***
```
SELECT 
iso_code, continent, location, date, new_cases, new_deaths, population

FROM coviddeaths

WHERE continent IS NOT NULL;
```

**OUTPUT:**

![Screenshot 2024-04-27 181449](https://github.com/jahnvi1017/tableau_project/assets/168184461/75fbd589-ac6b-455f-b4f9-38303a911f8b)

---


***2. Select columns from `Covidvaccinations` Table***
```
SELECT iso_code, continent, location, date, new_tests, total_tests, total_vaccinations, new_vaccination, people_vaccinated, people_fully_vaccinated

FROM covidvaccinations

WHERE continent IS NOT NULL;
```

**OUTPUT:**

![Screenshot 2024-04-27 213914](https://github.com/jahnvi1017/tableau_project/assets/168184461/3503b255-dd34-4809-8c5a-ea2e9fac8356)

---

***3. Which Continent has the Highest Death Count***
```
SELECT continent, MAX(total_deaths) as HightestDeathCount

FROM coviddeaths

WHERE CONTINENT IS NOT NULL 

Group by continent

order by hightestDeathCount desc;
```

**OUTPUT:**

![Screenshot 2024-04-27 214219](https://github.com/jahnvi1017/tableau_project/assets/168184461/1889aa91-1bbc-404d-9c5d-5eb01b30c245)

---

***4. Find Total Cases, Total Deaths and Total Vaccinations by Continent***
```
SELECT

dea.continent,

SUM(dea.new_cases) as Total_Cases,

SUM(dea.new_deaths) as Total_Death,

SUM(vac.total_vaccinations) as Total_vaccinations

FROM coviddeaths dea join covidvaccinations vac

on dea.location = vac.location

and dea.date = vac.date

WHERE dea.continent IS NOT NULL

GROUP BY dea.continent

ORDER BY SUM(dea.new_cases) DESC;
```

**OUTPUT:**

![Screenshot 2024-04-27 214319](https://github.com/jahnvi1017/tableau_project/assets/168184461/7bdd57ae-556d-4892-85b5-80818123d18e)

---

***5. Write a Query to find the Population of the Location which has the Highest Deaths***
```
select any_value(continent) as Continent, location, any_value(population) as population,

sum(total_deaths) as TotalDeath from coviddeaths

where continent is not null

group by location

order by totaldeath desc;
```

**OUTPUT:**

![Screenshot 2024-04-27 214444](https://github.com/jahnvi1017/tableau_project/assets/168184461/d00b699d-d968-43bd-a7b4-98ddcc0cb9d4)

---

***6. Shows What Percentage of Population is Infected with Covid***
```
Select Location, Date, (total_cases/population)*100 as Infected_Percentage

From coviddeaths

Where location like 'india'

and continent is not null

order by Infected_Percentage DESC;
```

**OUTPUT:**

![Screenshot 2024-04-27 214609](https://github.com/jahnvi1017/tableau_project/assets/168184461/88bd0e0c-028f-4c1a-b8af-df8609b3a054)

---

***7. Total Number of Cases, Deaths, Vaccinations, and Population by each Country.***
```
WITH cte (Location, Total_cases, Total_death, Total_vaccinations, Population)as (

SELECT

dea.Location,

SUM(dea.new_cases) as Total_Cases,SUM(dea.new_deaths) as Total_Death,

SUM(vac.total_vaccinations) as Total_vaccinations,

dea.population

FROM coviddeaths dea join covidvaccinations vac

on dea.location = vac.location

and dea.date = vac.date

WHERE dea.continent IS NOT NULL

GROUP BY dea.location, dea.population)

SELECT *,

ROUND(100.0 * Total_Cases/population,2) as Cases_per_Population_Percentage,

ROUND(100.0 * Total_Death/ population,2) as Death_per_Population_Percentage,

ROUND(100.0 * Total_vaccinations/ population,2) as Vaccination_per_Population_Percentage

FROM cte

ORDER BY Cases_per_Population_Percentage DESC;
```

**OUTPUT:**

![Screenshot 2024-04-27 214718](https://github.com/jahnvi1017/tableau_project/assets/168184461/2f3010c5-ed98-46a6-a075-7d8a21f186ce)

---

***8. Shows Percentage of Population that has Recieved at Least One Covid Vaccine***
```
With PopvsVac (Row_Num ,Continent, Location, Date, Population, people_vaccinated,

RollingPeopleVaccinated)as(

Select

row_number() over(partition by location order by date) as Row_Num,

dea.Continent,

dea.Location,

dea.Date,

dea.Population,

vac.People_Vaccinated,

SUM(cast(vac.people_vaccinated as unsigned)) OVER (Partition by dea.Location Order by dea.continent, dea.date)
as RollingPeopleVaccinated

From CovidDeaths dea

Join CovidVaccinations vac

On dea.location = vac.location

and dea.date = vac.date

where dea.continent is not null )

Select *, (RollingPeopleVaccinated/Population)*100 as percentage_population_vaccinated

From PopvsVac;
```

**OUTPUT:**

![Screenshot 2024-04-27 215134](https://github.com/jahnvi1017/tableau_project/assets/168184461/ab48f775-f646-4b44-a6e5-972244d287ff)

---

***9. Determine the Top 3 Countries with Most Percentage of Total Cases for Each Continent***
```
select *

from

(select *,
rank() over(partition by continent order by Total_cases_percentage desc) as rn

from(

select continent, location, sum(total_cases/population) as Total_cases_percentage

from coviddeaths

where continent is not null

group by continent,location

order by Total_cases_percentage desc) as a

group by continent,location) as b

where rn<=3;
```

**OUTPUT:**

![Screenshot 2024-04-27 215245](https://github.com/jahnvi1017/tableau_project/assets/168184461/fab56779-3686-4a71-b3c6-fae200d6bfbf)

---
