# firebase-next-recharts-covid

# 🚀 Javascript full-stack 🚀

### React / Next / Cards / ReCharts / Dark Theme

https://github.com/coding-to-music/firebase-next-recharts-covid

https://firebase-next-recharts-covid.herokuapp.com

https://firebase-next-recharts-covid.vercel.app

by Brace Sproul https://github.com/bracesproul

http://covid-statistics-fawn.vercel.app/

https://github.com/bracesproul/Covid-Statistics

## Does not work on Heroku but does work on Vercel (for me)

Works perfectly on Vercel but does not work on Heroku, get this message and does not show the app at the URL

```java
remote: -----> Compressing...
remote:        Done: 300.2M
remote: -----> Launching...
remote:  !     Warning: Your slug size (300 MB) exceeds our soft limit (300 MB) which may affect boot time.
remote:        Released v8
remote:        https://firebase-next-recharts-covid.herokuapp.com/ deployed to Heroku
remote:
```

# Environment Values

next.config.js

```java

These environment values are apparently not needed,
the data displayed is static and stored in:
/components/covid_data_history.json

    MONGO_URI: process.env.MONGODB_URI,
    RAPID_API_KEY: process.env.RAPID_API_KEY,
    FIREBASE_API_KEY: process.env.FIREBASE_API_KEY,
    FIREBASE_MESSAGING_SENDER_ID: process.env.FIREBASE_MESSAGING_SENDER_ID,
    FIREBASE_APP_ID: process.env.FIREBASE_APP_ID,
    FIREBASE_MEASUREMENT_ID: process.env.FIREBASE_MEASUREMENT_ID,

```

# Overview

## Technologies

This app was developed using React.JS and the Next.JS framework
It uses [Axios](https://www.npmjs.com/package/axios) to make API calls
The environment variables are handled by the [dotenv](https://www.npmjs.com/package/dotenv) NPM package

## APIs

All APIs are from [Rapid API](https://rapidapi.com/)
The COVID-19 data is provided by the [COVID-19 API](https://rapidapi.com/axisbits-axisbits-default/api/covid-19-statistics/)
The world population data is provided by the [World Population API](https://rapidapi.com/aldair.sr99/api/world-population/)

## Overview

This app displays the current COVID-19 statistics for the world and for each country.
The overview with 20 countries and the world data is displayed by default on the homepage
You can either click on "Get more data" on one of the given countries to view more detailed data and graphs or you can navigate to the "More Data" page to view all the data for all the countries.
On the [More-Data](./pages/More-Data.js) page you are able to filter the countries by the following criteria:

- alphabetically
- covid cases (highest/lowest)
- covid deaths (highest/lowest)
- infection rate (highest/lowest)
  or you may search by name.

## Technical Details

Since this is a Next.JS app, the data is first fetched using the `getStaticProps()` function. This function is called when the page is first loaded to fetch the data. It then returns the fetched data as an array of objects which is passed as a prop to the component which renders the homepage text. For the "More Data" pages the link is first parsed by the `getStaticPaths()` function which parses the URL to get the country's unique identifier. This identifier is then returned and another `getStaticProps()` function is called which uses that ID to fetch the countries data. The date is determined by the `getDateForRequest()` function which pulls today's date, goes back one day and then returns that date (this is because the API's most recent data is only available for the previous day).

## Credits

The 20 countries displayed on the homepage were chosen by [this list of the top 20 most visited countries](https://www.farandwide.com/s/most-visited-countries-792c34d8901f4bc9)
_Hong Kong was switched out for Switzerland_
The styling on the cards in the homepage was derived from [this tutorial by Fireship](https://www.youtube.com/watch?v=29deL9MFfWc&t=313s)

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/firebase-next-recharts-covid.git
git push -u origin main
```

## Heroku

```java
heroku create firebase-next-recharts-covid
```

## Heroku MongoDB Environment Variables

```java
heroku config:set

heroku config:set JWT_SECRET="secret"

heroku config:set PUBLIC_URL="https://firebase-next-recharts-covid.herokuapp.com"
```

## Push to Heroku

```java
git push heroku

# or

npm run deploy
```
