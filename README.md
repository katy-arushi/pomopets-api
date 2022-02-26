# PomoPets

**PomoPets** is an incentivized Pomodoro timer. Begin your focus session with a mysterious, hatchable egg and upon completing your focus session, you are rewarded with a cute digital pet!

A [Lighthouse Labs](https://www.lighthouselabs.ca/) project by [Justin Lam](https://github.com/justinklam), [Rhea Azarraga](https://github.com/Rheaazarraga), and [Arushi Katyal](https://github.com/katy-arushi).

**Access the app [here](https://pomopets.netlify.app/), live!**

## Features

- ⭐ Allows users to choose and name their own digital pets
- ⭐ Has a Pomodoro timer that has 25 minute focus sessions and 5 minute breaks
- ⭐ Users can start and reset the timer as they wish
- ⭐ Users can choose their area of focus for the timer
- ⭐ Statistics page tracks number of Pomodoro sessions completed by area of focus
- ⭐ Dark Mode

## Future Features

- Integrate Spotify
- Unlock new pets based on number of Pomodoro sessions completed
- Adding more page themes
- Responsive design for app to be used on any device
- Audio notification when focus session is completed
### Setting up the Server
1. Go to pomo-api: `cd pomo-api`
2. Create the `.env` by using `.env.example` as a reference: `cp .env.example .env`
3. Create a database in PostgreSQL named `pomo_db`
   - `CREATE DATABASE pomo_db;`
4. Update the .env file with your correct local information
   - PORT: `3030`
   - DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/pomo_db"
5. Install dependencies: `npm i`
6. Create database: `sequelize db:create`
7. Run migrations: `npx prisma migrate dev --name init`
8. Run the server: `npm start`
9. Go to `localhost:3030`

## Dependencies
### Server-side
    "@prisma/client": "^3.9.2",
    "prisma": "^3.9.2",
    "bcryptjs": "^2.4.3",
    "bundle": "^2.1.0",
    "cookie-parser": "~1.4.4",
    "cors": "^2.8.5",
    "debug": "~2.6.9",
    "dotenv": "^16.0.0",
    "ejs": "^3.1.6",
    "express": "~4.16.1",
    "http-errors": "~1.6.3",
    "morgan": "~1.9.1",
    "pg": "^8.7.3"

#### To drop and recreate the database
1. Connect to PostgreSQL using `psql`
2. Drop the database by running `DROP DATABASE pomo_db;`
3. Create the database by running `CREATE DATABASE pomo_db;`
4. Run `npm run migrate`
5. Run `npx prisma migrate dev --name init`
6. Run `npx prisma db seed`

#### To deploy to Heroku
Follow this [guide](https://www.prisma.io/docs/guides/deployment/deployment-guides/deploying-to-heroku)
1. `heroku login`
2. `heroku apps:create pomopets`
3. `heroku addons:create heroku-postgresql:hobby-dev`
4. `git push heroku main`
5. `heroku run bash`
6. `npm i prisma`
7. `npx prisma migrate deploy`
8. `npx prisma db seed`