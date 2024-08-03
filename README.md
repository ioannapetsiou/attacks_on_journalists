# Attacks Towards Journalists and Media Workers: The 10 Most Dangerous Countries
## The data, notebooks, and process notes for project three
## What I aimed to accomplish:
I really wanted to create something immersive like a scrolly-telling story, and I really wanted to work with a map. However, when I started working with the [CPJ Database](https://cpj.org/data/) I didn't think my project would end up like this. I started seeing counts of each attack type (killed, missing and imprisoned) towards journalists and media workers. In the beginning, I didn't take into account the "Country" factor, and just started seeing the number of each attack year by year, but I couldn't really see a story. However, then I started thinking: why don't I see which countries have the most attacks(total)? what about by category? and which region is most dangerous? what's the most common attack type -getting killed, going missing or being imprisoned? and what's the cause for it? <i>so I started answering my questions.</i>
## My findings:
* 51% of Attacked Journalists and Media Workers have been Killed Worldwide (1992 - 2023). Then 47.5% have been imprisoned and 1.5% has gone missing.
* The most common reason journalists and media workers are getting killed is because they are getting murdered. All murdered journalists were under the "Confirmed Motive" category, meaning that their murder is because of their work.
* 98% of media workers died due to unknown reason .
* Overall, nearly three in four of journalists and media workers killed had a confirmed motive.
* 7 out of the 10 countries with the most attacks on journalists and media workers are in Asia.
* Asia Leads in Attacked Journalists and Media Workers Across All Types of Attacks (1992 - 2023)
* The 10 most dangerous countries for journalists by number of total attacks are : Turkey, Iraq, Iran, China, Syria, Mexico, Phillipines, Israel and Occupied Palestian Territory, Ethiopia, Russia.
## Data collection process:
As mentioned, CPJ data was found [here](https://cpj.org/data/). CPJ provides a database with all necessary information. I inspected the page, clicked onto Network, and worked with an Undocumented API. This process was done 3 times, one for each attack category (killings, imprisonments, missing). The undocumented API I got was referring to one of the database's pages. After I copied the Curl of the API, I went onto CurlConverter and pasted it. CurlConverter gave me the headers, but no params. After looking at the URL I managed to create my own params, and then I did a while loop, in order to paginate through all pages. Specifically, this collection of data was done in three seperate notebooks, one for each attack type <b>CPJ_Killings, CPJ_missing</b> and <b>CPJ_imprisoned</b>. The reason I did this in 3 notebooks is because if something went wrong with one of them I wouldn't want my whole notebook to glitch. The process I followed is the same for all three notebooks. I stored the data I got from them into .csv files.
## Data analysis process:
CPJ_all:
- This is the notebook I merged all three of my .csv files from the data collection process, to create one big dataset. After merging them, I only kept the columns I needed and got rid of the rest. I renamed the columns and replaced the "Unknown" values with nan. I merged my bigger dataset with a dataset I found on [this website](https://developers.google.com/public-data/docs/canonical/countries_csv) (can also be found on this repo under <b>continents-according-to-our-world-in-data.csv</b>), in order to assign my countries to a continent. If a country was misspelled or had two names (ex. US or United States) I would fix that manually by using the .loc method. Thanfully this didn't happen for many of them. Then I only kept the rows for the years 1992 to 2023. This big dataset (which can be found in this repo under <b>CPJ_all</b> is the one I used as a base for my analysis.
- Then I started working with my base to see certain things: I saw the number of attacks by type per year, the count of each attack type for the whole 1992 to 2023 period (I saw it as count and also as percentage), I saw the number of total attacks by region, saw the most common type of death, the Killings by region and type of death, Killings by country and type of death, 
Top 10 Countries with most attacks (by total and number of attacks for each type), Top 10 countries within each category (imprisoned, killings, missing).

<i> Notes: One unlisted case in Africa is not included in the charts.
Totalitarian regimes or conflict-ridden countries may underreport or misrepresent attacks on journalists and media workers, affecting the accuracy of statistics.
In the "Killed" category both confirmed and unconfirmed motives are included.
Russia is assigned to the continent of Europe.</i>

In the files I uploaded, you can also find the datasets I created for Visualizations.
- <b> CPJ_all.csv </b> : my base dataset, containing the name of the Organization the journalists / media worker worked for, their Name, the Location of the attack, the Attack type, their CPJ URL, the Country the attack took place, Type of worker, Motive (confirmed or  unconfirmed), Type of Death, Region, Year of the attack
- <b> attack_type_by_region.csv </b>: contains these columns "Region	Imprisoned	Killed	Missing	Unlisted	Total", displaying the number of attacks per region.
- <b> total_attacks.csv </b> : has two columns : one with the attack type (killed, imprisoned, and missing) and one with the number of those attacks. The information applies to the total of the 1992-2023 year period.

## Where did I grow the most / What did I want to do but couldn't:
* This was my first time actually working with Undocumented API's, a map template, javascript, d3. I was quite pleased with my undocumented API finding, since my first approach to collect CPJ's data was using playwright, but It didn't work. I also found a script in GitHub for collection with selenium but that wouldn't work either. The undocumented API really made the process more satisfying. Data wise, I don't think I would change anything in my project.
* Since it was my first time working with a map template I found it quite challenging. After playing around for a while I started to realize the actions, so I could fix my template. To highlight the countries I used d3 with mapbox commands. 
* What I really wanted to do was create a mapbox style where I would set each highlighted country as a layer. Maybe in this way I would be able to highlight one country each time as you go, and not have them all highlighted <i>forever</i>. I didn't manage to do that, even after the many tutorials I saw and after my many tries. The only thing I could to is change the projection of the map each time, to make sure that only the country I'm referring to was highlighted.

However, I am <u>very</u> pleased with my outcome. Before LEDE, I couldn't even imagine doing something like this! Now, not only I did this, but It also looks good! I think this is the project where I grew the most. I embraced the challenge of trying new skills, such as working with undocumented API's and setting params myself, trying a map template, and set the country - highlighting commands using d3. After this process, I feel like I could work with <i>any</i> data I want, and nothing can stop me.

Both of the vizualizations were made in flourish. My template is from [Mapbox](https://github.com/mapbox/storytelling), creating a scrolly-telling map story.

An inspiration for the way my scrolly looks is [this piece](https://interactive.aljazeera.com/aje/2020/saving-the-nile/index.html) from Al Jazeera.

## Website
You can fink the url for my website [here](https://ioannapetsiou.github.io/attacks-on-journalists/).
