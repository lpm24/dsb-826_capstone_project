## GDQ: A Remastered Analysis of Charitable Gaming

---

### Problem Statement

Games Done Quick (GDQ) is a series of charity video game fundraising events featuring high-level gameplay that has raised over 50 million dollars so far.  The organizers of GDQ want to know if there's anything they can do to impact the amount of donations received at each event.  In order to answer this question, we've been hired to conduct an initial exploratory review of the GDQ schedule, game data, and donation data since 2017 to see if any features have had a significant impact on the amount of donations received.

---

### Data

|Feature|Type|Dataset|Description|
|---|---|---|---|
|game_key|object|derived from GDQ data|A concatenation of event, year, and name.|
|event|object|https://gdqstat.us/?series=0|Either AGDQ or SGDQ|
|year|object|https://gdqstat.us/?series=0|Year of event|
|name|object|https://gdqstat.us/?series=0|Name of game|
|id|int|https://gdqstat.us/?series=0|ID of game|
|category|object|https://gdqstat.us/?series=0|Game category being speedrun|
|start_time|datetime|https://gdqstat.us/?series=0|Game start time|
|duration|object|https://gdqstat.us/?series=0|Game duration|
|runners|object|https://gdqstat.us/?series=0|Game runner(s)|
|host|object|https://gdqstat.us/?series=0|Event host(s)|
|max_viewers|float|https://gdqstat.us/?series=0|Maximum viewers during game|
|median_donation|float|https://gdqstat.us/?series=0|Median donation during game|
|total_donations|float|https://gdqstat.us/?series=0|Total donations during game|
|donations_per_min|float|https://gdqstat.us/?series=0|Donations per minute (in dollars) during game|
|num_chats|float|https://gdqstat.us/?series=0|Number of chats during game|
|is_Bonus|float|https://tracker.gamesdonequick.com/tracker/bids/|Whether or not the game is a Bonus Game|
|is_TASBot|float|https://tracker.gamesdonequick.com/tracker/bids/|Whether or not the game is run by TASBot|
|has_Incentive|float|https://tracker.gamesdonequick.com/tracker/bids/|Whether or not the game has an incentive|
|has_Goal|float|https://tracker.gamesdonequick.com/tracker/bids/|Whether or not the game has an incentive goal|
|developer|object|https://gdqstat.us/?series=0|Game developer|
|publisher|object|https://gdqstat.us/?series=0|Game publisher|
|initial_release_year|float|https://www.wikipedia.org/|Year game released|
|initial_consoles|object|https://www.wikipedia.org/|Initial consoles game released on|
|initial_consoles_clean|object|https://www.wikipedia.org/|Initial consoles game released on (clean)|
|initial_generation|object|https://www.wikipedia.org/|Initial console generation game released on|
|metascore|float|https://www.metacritic.com/|Metascore from Metacritic|
|user_score|float|https://www.metacritic.com/|User Score from Metacritic|
|was_on_PC|float|https://www.wikipedia.org/|If game released on PC|
|chats_per_hour|float|derived from GDQ data|Chats per hour|
|event_SGDQ|float|derived from GDQ data|Event was SGDQ|
|initial_generation_3|int|derived from GDQ data|Game initial console generation was 3|
|initial_generation_4|int|derived from GDQ data|Game initial console generation was 4|
|initial_generation_5|int|derived from GDQ data|Game initial console generation was 5|
|initial_generation_6|int|derived from GDQ data|Game initial console generation was 6|
|initial_generation_7|int|derived from GDQ data|Game initial console generation was 7|
|initial_generation_8|int|derived from GDQ data|Game initial console generation was 8|
|initial_generation_9|int|derived from GDQ data|Game initial console generation was 9|
|initial_generation_Various|int|derived from GDQ data|Game initial console generation was undeterminded|
|is_Arcade_1|int|derived from GDQ data|Is an arcade game|
|is_Atari_1|int|derived from GDQ data|Is an Atari game|
|is_Microsoft_1|int|derived from GDQ data|Is an Xbox game|
|is_Mobile_1|int|derived from GDQ data|Is a mobile game|
|is_Nintendo_1|int|derived from GDQ data|Is a Nintendo game|
|is_Other_1|int|derived from GDQ data|Is another type of game (Casio, Neo Geo, etc.)|
|is_PC_1|int|derived from GDQ data|Is a PC game|
|is_Sega_1|int|derived from GDQ data|Is a Sega game|
|is_Sony_1|int|derived from GDQ data|Is a Playstation game|

Sources: 
https://gamesdonequick.com/
https://www.twitch.tv/gamesdonequick
https://gdqstat.us/?series=0
https://tracker.gamesdonequick.com/tracker/bids/
https://www.metacritic.com/
https://www.wikipedia.org/


---

### Analysis

For this analysis, we compared various features from (or derived from) the GDQ data in an attempt to model donations per minute (in dollars).  We opted to use linear regression for this analysis due to the linear relationship between our feature variables and the target variable, and our desire to have interpretable results given the nature of the problem statement.  The donations per minute data is positively skewed, so we'll be using the square root of that as our target variable in order to reduce the variance.

---

### Conclusions/Recommendations

After reviewing the data and modeling it, there are a few actionable insights that the GDQ schedulers can take away from this to maximize donations in the future.

Firstly, incorporating newer games is a clear driver for donations.  Ninth generation console games brought the most money per minute in via donations, and our model corroborated the strength of this feature.  These recent games are at the top-of-mind for viewers and utilize the most advance technology.

Secondly, continuing to showcase TASBot runs should drive donations per minute.  This was the strongest feature from our model, and these runs likely generate interest due to their unique nature, the ingenuity necessary to create them, and the (inhuman) skill being displayed.

Next, schedulers should consider limiting the number of older, arcade, and mobile games being played.  These tended to perform the worst, and did little to drive interaction.

Another important thing to note is the efficacy of goal incentives for driving donations, particularly for Bonus Games.  The organizers should continue offering these as incentives, and consider raising the goal amounts since these are very likely to be fulfilled.

While we were able to draw some quality conclusions from our data analysis and subsequent model, there were still limitations to what we've done.  These included proper donation attribution due to the time when donations were recorded, unduly influenced game reviews (Metacritic scores), and issues with data quality and availability.

However, this analysis is just scratching the surface, and there are many future areas to explore.  For next steps in this analysis, we'd like to gather more GDQ data, create additional salient features that capture the nuanced aspect of donations, dedicate more attention to the timeseries aspect of the data to model seasonality, etc, and sentinment analysis on chat and donation comments.  These are just a few examples of places this analysis could go from here.