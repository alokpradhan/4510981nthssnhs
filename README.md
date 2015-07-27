##Week 4 assessment

Fork and clone, then submit a PR when you're done. Good luck!

###1. We have some queries for you:

Answer [these 10 questions](https://docs.google.com/forms/d/1pxzwnNQgksO9BOvC56F9fdogG22abKeMXMCECdq6YjU/viewform?usp=send_form) on a Google form.

###2. Now you will have some queries:

Run the 6 queries in the `mode_queries.md` file on the [Mode Analytics editor](https://modeanalytics.com/editor). Save your query in the file.

###3. Database design

A local mixed martial arts (MMA) league has asked you to redesign their web page so they can market events and sell tickets. (Right now it's just a landing page with the league's phone number: 911.)

The league holds an event about once a month at one of a handful of regular venues. Every venue has a different capacity. Every event has between 8 and 12 fights. The fights are scheduled in a certain order but they won't start at a specific time.

The league has 10 weight classes, 5 each for men and women, with a minimum weight for each. Fights have two fighters, who both belong to the same weight class. After the fight is over, there has to be a record of the winner. Fights don't end in draws.

Design the data model for this client. Use any design tools you like. Save your model as text or a legible image file.

----------
Entities (headers):
 - attributes:types

League
 - id: int
  => has many events
 - number_of_events: int
 => has many weight classes

Event
 - id: int
 - venue
 => has one venue
 - fights
 => has many fights
 - league_id: int
 => belongs to league
 - event_date: date

Venue
 - id: int
 - capacity
 - price_per_ticket
 - event_id: int
 => belongs to an event

Fight
 - id: int
 - event_id: int
 => belongs to an event
 - fighter1: fighter_id
 - fighter2: fighter_id
 - winner: fighter_id
 => fight has one winner

Figher
 - id
 - name
 - gender: string
 => belongs multiple weight classes

Weight class
 - minimum weight: float
 - league_id: int
 => has multiple fighters

Fight-WeightClass Join
- fighter_id: int
- weight_class_id: int
- gender: string

