# Command Guide
## Database Access
First, I will explain what is in the database. This is needed to fully understand some of the commands. Then, I will explain what all the bot commands do and how to use them effectively.

### OspreyDB
The part of the database you need to know about is the part that contains all of the GeoFS accounts. Any account that was online at all since July 2025 will be in here (except for a few minimal days of down time due to my negligence). The database currently contains 95% of the active player base and around one fifth of any GeoFS account ever.

As a rule of thumb, information on an account is only what was last seen by the bot. For example, if a person was changing their aircraft while multiplayer was turned off, this will NOT be shown. Also, data can be up to five seconds behind.

#### Database Fields
**Account ID (referred to as “acid”):**
Every GeoFS account has it’s own unique account ID called an acid. This is the key thing that the database uses to keep track of all of it’s data. If it weren’t for acids, it wouldn’t know which callsigns or locations are for which pilots.\
**Online (Online):** This tells if the account is online or not. If it is “True” that means the account is online. If it says “False” it means the account is offline. Remember an account is only considered online if the user is on the actual flight sim page. Their account settings page doesn’t count.\
**Current Aircraft (currentAircraft):** This is the current aircraft of the account.\
**Current Callsign (currentCallsign):** This is the last callsign an account had.\
**Last Position (lastPosition):** This is the last position the bot was able to see. The first number is latitude, the second number is longitude.\
**Past Callsigns (pastCallsigns):** This is any callsign the account has had in the past. There will not be duplicates though if the account has had the same callsign more than once.\
**Events (events):** Events are the most complicated part. There are five types of events (online, offline, teleportation, aircraft change, callsign change). Each event will be listed under the events section.\

##### Event Types
**Online:** This event is logged when a pilot comes online. (The bot didn’t see them before, but now does) It includes the timestamp.\
**Offline:** This event is logged when a pilot goes offline. (The bot saw them before, but doesn’t now.) This includes the timestamp. Note: if a pilot has their internet drop and they disappear off of the map screen for a split second, this counts as going offline.\
**Aircraft Change:** Is logged when an account changes their aircraft. It shows the old aircraft, the new aircraft, and when it happened. If an aircraft says unknown that means it is a new aircraft that the bot doesn’t know about.\
**Teleportation:** A teleport event is created when an account moves an impossible distance. I was lazy, so currently it’s if it moves more than 50km in 5 seconds. The event logs the old position, new position, and the distance travelled.



Callsign Change: If the bot detects a callsign change it is logged as an event. The event contains the old callsign, new callsign, and acid (account ID). The account must first come online before the bots detects the change.
