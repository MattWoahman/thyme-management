# Thyme Management
## Goal
Make an app that keeps track of the food in your house - this could include
* Reminding you 1 week out from expiration
* Letting you know when you're running low on certain ingredients
* Giving you recipe suggestions based on what food you have
* Letting you schedule meals on certain days and reminding you of missing ingredients

## Tech Stack

### <u>Matt's proposal</u>
Pretty standard stack - smart server responsible for all business logic, dumb endpoints responsible for rendering data and some caching

<u>Tech Stack</u>
* Server
  * Written in Rust
    * Uses axum & tokio, plus a million other crates I'm sure (serde_json)
* DB
  * Postgres 
    * Could do SQLite, but figure Postgres is more fun for learning
  * Hosted on the same machine as the Server
* Client (first a Web App/PWA, then probably phone, and i'd like to do a desktop app at some point just for learning/fun)
  * Tauri for PWA?
  * egui for Desktop App
  * There's some rust ways to develop phone apps, but worse comes to worst we look at either Flutter or Kotlin

<u>Hosting Architecture</u>

We can just host it on my home server, behind an nginx reverse proxy. Currently, I have *thehomans.org* pointing here, but it'd be pretty easy to pick up a different domain. I've got plenty of processing power laying around here for it, but if we needed to we could pick up a $5/month VPS from hertzner or the like.

## Desired features
1. Ability to add food items to your account
   1. Food items could be ingredients or full foodstuffs
   2. Each food item should have an expiration date, which the app reminds you of as it approaches
   3. Each food item should also have a quantity that you should be able to update
2. Ability to enter meals to your account
   1. Should be able to make these meals out of food items
   2. Meals should be able to be schedule, with reminders for items that make up the meal that are about to expire/have a low quantity