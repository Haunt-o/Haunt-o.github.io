---
title: Iodized NaCL
subtitle: Optimized Context
toc: true
---
## Glossary

<table>
<thead>
  <tr>
    <th>Term</th>
    <th>Meaning</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Character</td>
    <td>A text character ("a" is one character).</td>
  </tr>
  <tr>
    <td>Token</td>
    <td>A piece of text given to the AI as input to calculate its response from.<br>Tokens are not just characters or words, but can be slices of words.</td>
  </tr>
  <tr>
    <td>Story</td>
    <td>The text that makes up the intro for your scenario.</td>
  </tr>
  <tr>
    <td>Context</td>
    <td>All of your scenario info: memory, author's note, and story cards.</td>
  </tr>
  <tr>
    <td>A/N</td>
    <td>Shorthand for "Author's Note".</td>
  </tr>
  <tr>
    <td>Prose</td>
    <td>Text written normally, in sentences.</td>
  </tr>
</tbody>
</table>

## Preface

Free players on AI Dungeon have an AI context window of 1000 tokens.  
This is a surprisingly small amount to work with, when you consider everything
that can go into describing a scenario.

For reference, at a minimum, you'll have some tokens eaten up already:

<table>
<thead>
  <tr>
    <th>Info</th>
    <th>Minimum Tokens</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Author's Note</td>
    <td>6 Tokens</td>
  </tr>
  <tr>
    <td>Prompt Instructions</td>
    <td>175 Tokens</td>
  </tr>
  <tr>
    <td>Response Buffer</td>
    <td>75 Tokens</td>
  </tr>
  <tr style="font-weight:bold;">
    <td>TOTAL</td>
    <td>256 Tokens</td>
  </tr>
</tbody>
</table>

A 1,000 character story — which is fairly small — takes up ~250 tokens.  
A full 4,000 character story is ~1000 tokens — already at the limit.

AI Dungeon will shave off some of the story text to make room for the memory,
author's notes, and story cards; however, it will dump story cards and author's
notes if it can't fit everything.

This means that:
- Small scenario? You have less than 50% of the limit (~2000 characters) to fit all your info to avoid cuts.
- Medium scenario? You have maybe 25% of the limit.
- Big scenario? You'll have to keep things *really* lean to fit your story cards
  in after the AI trims the story text, if possible. Either way, the AI is
  gonna cut something.


>*Note: Tokens are not 100% consistent, but I got my estimates by analyzing
token counts for various bits of text, calculating the average ratios,
and writing code to accurately estimate tokens.*

<!--
WHEN: WHITE PAPER
If you'd like to read more on the technical specifics of NaCL, check out the
[white paper](/nacl/white-paper.html). -->

## Format

Iodized NaCL, overall, is a pretty straightforward format in how it's laid out.  
There's three parts to it:
1. Header
	- This is the name of whatever you're writing context info for, surrounded
	  by square brackets `[Like This]`.
2. Description
	- This is a small description of the essential details for something, next
	  to the header.  
	  For example, if we have a 23 year old named Jim:
	  `[Jim] human/male/adult`
3. Details
	- This is a list of details describing your character; each line of details
	  is started with a keyword. We'll get into keywords later, but for now
	  here's an example:
	  ```
	  WEAR white shirt/jeans
	  LIKE tofu
	  FRIEND Bob
	  ```

-----

For separating pieces of information on a line, you have a few options:
- Comma `,`
	- Good for lists of things.
	- Example: `sword, shield, bomb`  

	  This is pretty straightforward; it's a list of things. 
- Semicolon `;`
	- Good for a stronger separation of things in the same category.
	- Example: `lush, vibrant trees; beautiful lake; glowing fireflies` 

	  This means that all the things listed are separate things, each being
	  a feature of some location. The semicolon implies that
	  `lush, vibrant trees` is its own thing instead of `lush` and
	  `vibrant trees` being part of a list.
- Slash `/`
	- Good as a middle ground between `,` and `;` — marks things that are
	  separate bits of information that link together under the same piece of
	  information.
	- Example: `tall/atheletic/toned`  

	  This means that `tall`, `athletic` and `toned` come together to represent
	  the full description of someone's build.
- Ampersand `&`
	- Good when you want to group things together that should be listed with
	  an "&"/"and" between them.
	- Example: `eyes(deep&brown)`  

	  This implies that the eyes should be described as "deep and brown" or
	  the two features should be grouped together overall.

&nbsp;

>*If you're not 100% sure about which one is the best to pick, it honestly
doesn't matter too much if you're stuck on very specific cases like whether to
use a slash or an ampersand to separate two things; the descriptions for
each thing are just a technical, "standard" definition for how NaCL works.*  
*The AI — 99.999% of the time — isn't going to get an entirely different message
from something like `shirt(clean,white)` vs `shirt(clean&white)`.*

-----

As an example, let's start small and say we have a location called
"Grassy Plains":
```
[Grassy Plains] Lush grassy plain; many trees
```

This is cool, but what if we wanted to describe some features that it has?  
That's where the `FEAT` keyword comes in handy:
```
[Grassy Plains] Lush grassy plain; many trees
FEAT lake; cave
```

With a small description the AI will know to describe it as a lush, grassy
plain with many trees; additionally, it will note a lake and cave (likely
when exploring).  
For reference, AI Dungeon clocks this at 61 characters and 16 tokens. When I
tried writing this as prose, it was 23 tokens — roughly 50% bigger.

-----

Each category of details for something in NaCL is started with a keyword for
that category. Keywords are words in all caps that have been found to be
effective in conveying to the AI what information is being given.

>*Note that every keyword might not be a full word; the AI doesn't actually
"read" words like a person, it just simply detects patterns.*  
*This is why the keyword for "Appearance" is `APPE` and not `APPEARANCE`,
because the AI is able to detect the same pattern from `APPE` —
so it's just the more optimal way of writing it.*

As an example of making a more detailed bit of NaCl, let's say we have someone
named Jim who:
- Is a 25 year old anthropomorphic wolf male at 5'6 and 160lbs.
- Wears a white shirt, jeans, and brown boots.
- Has an average build with grey fur.
- Is depressed.
- Eats mainly pizza and salad.
- Is friends with you and someone named Naomi.
- Drops his phone when defeated.

The NaCL would be:
```
[Jim] anthro wolf/male/25yr/5'6/160lbs
APPE average/grey fur
WEAR white shirt/jeans/brown boots
MIND depressed
DIET pizza, salad
FRIEND you, naomi
LOOT phone
```

AI Dungeon reports this as 157 characters and 40 tokens.  
Compare this to straightforward prose, which clocks in at 340 characters:
```
Jim is a 25 year old anthro wolf male at 5'6 and 160lbs.
He wears a white shirt, jeans, and brown boots.
He has an average build with grey fur, and commonly wears a white shirt, jeans, and brown boots. Jim is suffering from depression; he mainly eats pizza and salad.
Jim is friends with you and Naomi. If defeated, Jim will drop his phone.
```

My testing shows this as 85 tokens — over twice as much as the NaCL!  
Not only is the NaCL more efficient, but I would say it's also simpler to read.

&nbsp;

## Keywords

This is a list of all the commonly used keywords to cover most characters,
locations, etc. that you make.

For the full list of all keywords that cover more specific traits, check
out the [keyword page](/nacl/keywords.html).

-----

### Entity Keywords

<table>
<thead>
  <tr>
    <th>Keyword</th>
    <th>Category</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>DESC</td>
    <td>Description</td>
    <td>Base information about entity; race, gender, etc.<br>Generally unused as the first line is implicitly DESC.</td>
    <td>human/male/adult</td>
  </tr>
  <tr>
    <td>SUMM</td>
    <td>Summary</td>
    <td>Generic info category.<br>Good for anything that doesn't fit in with others, prose-like info, or stating things you want consistently described.<br>If you have a personality trait that you really want to shine, put it in here.</td>
    <td>nickname("Jimmy"); collects eggs</td>
  </tr>
  <tr>
    <td>APPE</td>
    <td>Appearance</td>
    <td>Details about the physical appearance of the entity.<br>Can also include details about how entity presents with other senses, like smell or taste.</td>
    <td>brown eyes/red hair/fair skin</td>
  </tr>
  <tr>
    <td>BUILD</td>
    <td>Physical Build</td>
    <td>The physical build of an entity.</td>
    <td>average height/toned muscles</td>
  </tr>
  <tr>
    <td>RACE</td>
    <td>Race</td>
    <td>The race of an entity, if mentioning it in DESC isn't enough or you want to get more detailed with it (example: main species in DESC, subspecies in RACE).</td>
    <td>alaskan barrel chipmunk</td>
  </tr>
  <tr>
    <td>WEAR</td>
    <td>Outfit</td>
    <td>The outfit worn by the entity.</td>
    <td>white shirt/jeans</td>
  </tr>
  <tr>
    <td>MIND</td>
    <td>Personality</td>
    <td>Mental traits, attitude, outlook, etc.<br></td>
    <td>calm/friendly</td>
  </tr>
  <tr>
    <td>MOV</td>
    <td>Movement</td>
    <td>How an entity moves around.</td>
    <td>crawl</td>
  </tr>
  <tr>
    <td>POWER</td>
    <td>Powers</td>
    <td>List of powers, abilities, etc. of entity.</td>
    <td>super strength</td>
  </tr>
  <tr>
    <td>EFFEC</td>
    <td>Effects</td>
    <td>Effects of the entity, such as magical/science/chemical effects of an object.</td>
    <td>makes drinker tired</td>
  </tr>
  <tr>
    <td>DIET</td>
    <td>Diet</td>
    <td>What the entity eats.<br></td>
    <td>pizza</td>
  </tr>
  <tr>
    <td>FRIEND</td>
    <td>Friends</td>
    <td>Who the entity is notably friends with.</td>
    <td>jim, jim 2</td>
  </tr>
  <tr>
    <td>LOOT</td>
    <td>Loot</td>
    <td>What entity drops on defeat, or can be taken on search.</td>
    <td>$20 bill</td>
  </tr>
  <tr>
    <td>INV</td>
    <td>Inventory</td>
    <td>List of things held in inventory.</td>
    <td>bomb, carrot</td>
  </tr>
  <tr>
    <td>LIKE</td>
    <td>Likes</td>
    <td>Describe things liked by entity.</td>
    <td>carrots</td>
  </tr>
</tbody>
</table>

-----

### Location Keywords

<table>
<thead>
  <tr>
    <th>Keyword</th>
    <th>Category</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>ATMOS</td>
    <td>Atmosphere</td>
    <td>Narrative atmosphere of location.</td>
    <td>spooky, tense</td>
  </tr>
  <tr>
    <td>TONE</td>
    <td>Tone</td>
    <td>Tone describing the location.</td>
    <td>calm, relaxing</td>
  </tr>
  <tr>
    <td>FEAT</td>
    <td>Features</td>
    <td>Features of the location.</td>
    <td>choo choo ride; trees</td>
  </tr>
  <tr>
    <td>CLIM</td>
    <td>Climate</td>
    <td>Climate of the location.</td>
    <td>hot, windy</td>
  </tr>
  <tr>
    <td>GEO</td>
    <td>Geography</td>
    <td>Geographical description of location.</td>
    <td>mountain</td>
  </tr>
  <tr>
    <td>BIOME</td>
    <td>Biome</td>
    <td>General type of biome for location.<br>Specific info is better for DESC or SUMM.</td>
    <td>tundra</td>
  </tr>
  <tr>
    <td>ENTER</td>
    <td>Entrances</td>
    <td>Entrances into the location.</td>
    <td>west(from mountain)</td>
  </tr>
  <tr>
    <td>EXIT</td>
    <td>Exits</td>
    <td>Exits from location.</td>
    <td>campus(east)</td>
  </tr>
  <tr>
    <td>CITIZ</td>
    <td>Citizens</td>
    <td>Describes racial diversity of location</td>
    <td>humans, elves</td>
  </tr>
  <tr>
    <td>ETHN</td>
    <td>Ethnicity</td>
    <td>Similar to CITIZ, but better when describing humans</td>
    <td>hispanic</td>
  </tr>
  <tr>
    <td>NATIV</td>
    <td>Natives</td>
    <td>Like CITIZ or ETHN, but describing people native to location, instead of just living there.</td>
    <td>tribal dwarves</td>
  </tr>
  <tr>
    <td>LIFE</td>
    <td>Life</td>
    <td>Life forms found in location.</td>
    <td>deer; rabbits</td>
  </tr>
  <tr>
    <td>THRE</td>
    <td>Threats</td>
    <td>Hostile life forms found in location.<br>Good to specify level of threat.</td>
    <td>wolf(minor)</td>
  </tr>
</tbody>
</table>

-----

### Author's Note Keywords

<table>
<thead>
  <tr>
    <th>Keyword</th>
    <th>Category</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>STYL</td>
    <td>Style</td>
    <td>Writing Style for the AI</td>
    <td>verbose, talkative, romantic, arousing</td>
  </tr>
  <tr>
    <td>GENR</td>
    <td>Genre</td>
    <td>Genre of the story</td>
    <td>comedy, romance, horror</td>
  </tr>
  <tr>
    <td>TONE</td>
    <td>Tone</td>
    <td>Tone of the writing for the story</td>
    <td>depressing, tragic, upbeat</td>
  </tr>
  <tr>
    <td>RTNG</td>
    <td>Rating</td>
    <td>Rating of the story (in terms of content)</td>
    <td>PG, PG-13, M, R, X-RATED</td>
  </tr>
  <tr>
    <td>THEM</td>
    <td>Theme</td>
    <td>Theming of story/setting</td>
    <td>fantasy, sci-fi, western</td>
  </tr>
  <tr>
    <td>NOTE</td>
    <td>Note</td>
    <td>Miscellaneous writing notes</td>
    <td>describe Rebecca's facial reactions</td>
  </tr>
</tbody>
</table>

## Additional Options

If you want a slightly more technical syntax that may provide some benefits
for the AI properly using your NaCL, here are some options:

1. List grouping
	- When making lists of things, placing the list within square brackets
	  may help keep the items encapsulated together:
	  ```
	  INV[marble, gum, slingshot]
	  ```
2. Grouped Relation
	- If you want to add a detail for a bit of info, you can use parentheses to
	  describe the detail with it:
	  ```
	  FEAT flowing river("azure rapids")
	  ```
	- Another example, that I use a lot:
	  ```
	  APPE hair(long,brown)
	  WEAR black(shirt,pants)
	  ```
	  This one is pretty effective, with the AI correctly joining "long and brown"
	  with "hair" and "black" with "shirt" and "pants".

3. Direct implication
	- You can put a colon after a keyword, instead of a space, which may help
	  sell the assocation between the keyword and items following it:
	  ```
	  WEAR:white shirt/shoes/jeans
	  ```
4. Full encapsulation
	- If you're worried about the information for something "bleeding out" into
	  other things, you can put angle brackets around everything to try and
	  keep it closed off.
	  ```
	  [Steve]<Human/male/5'9
	  MIND energetic>
	  ```
5. Symbolic Following
	- The symbol `=>` may be used to note that something "follows" something
	  else. For example, this can be used for directions
	  and exits:
	  ```
	  [The Dry Expanse] Hot arid desert
	  EXIT SW => Great Oasis; E => Endless Desolation
	  ```
	  If this doesn't work for you, using a grouped relation should work:
	  ```
	  [The Dry Expanse] Hot arid desert
	  EXIT sw(great oasis); east(endless desolation)
	  ```

6. Multi-Word Connection
	- If you feel like a term made up of multiple words is not being grouped
	  together correctly, you can try joining the words with underscores instead
	  of spaces:
	  ```
	  [Jim] Anthro_Wolf/male/25_years/5'6_tall/160lbs
	  WEAR white_shirt/jeans/brown_boots
	  APPE average_build/grey_fur
	  ```
	- Another strategy is smashing words together, like `FlamingOrangeEyes` for
	  `Flaming Orange Eyes`, but this carries the risk of the AI chopping up
	  the word in a weird way and getting a different meaning, like
	  `Flamingo Range Eyes` for the example used.
	
	- Additionally, quoting something will help keep the words grouped together.

## Examples

For the purpose of showing how the format and keywords work, here are several
examples of story cards and their corresponding NaCL.

All examples are from the [AI Dungeon World Info Research Sheet](
  https://github.com/valahraban/AID-World-Info-research-sheet/blob/main/AID%20WI%20Research%20Sheet.md
)

### Greenbriar Hills
Let's say we want to make a location called "Greenbriar Hills" with the
following information:
- Is a hilly region.
- Temparate climate, with hilly forests, a large river, and is to the east (
  southwest from the mountain).
- Has several exits: Yrthwood to the Northwest, The Sunless Basin to the East,
  and some mountains called the Teeth of Gwahlur to the Southwest.
- Featuring prickly plants and strange lights at night (referred to as the
  "Old Light").
- Has native (friendly) lizardfolk and halflings; the halflings live in the
  prosperous village of Greenbriar.
- Has varied lifeforms within, with some notable ones being giant lizards in
  a river and crested birds.
- Has the minor threat of wolves in the region.

The NaCL would be:
```
[Greenbriar Hills] hilly region
CLIM temperate
BIOM hilly forests; large river; east(SW from mountain)
EXIT NW(Yrthwood); E(The Sunless Basin); SW(mountains:Teeth of Gwahlur)
FEAT prickly plants; strange lights at night("Old Light")
NATIV Lizardfolk(friendly); Halflings(prosperous village "Greenbriar")
LIFE varied; giant lizards(in river); crested birds
THRE wolves(minor)
```

AI Dungeon reported a story card with this info as 374 characters and 94 tokens.
Considering how much information we have in here, that's pretty good.

### Siren

As an example of describing an item, let's write an entry for a drink called
Siren that:
- Is a popular drink.
- Is sapphire colored, with silver bubbles on it. A sprig of mint is visible on
  it, and it smells alcoholic but tastes like rust metal.
- Has the effect of inspiring the drinker to begin dancing.

The NaCL (146 characters and 37 tokens):
```
[Siren] A popular drink
APPE Sapphire colored/silver bubbles/sprig of mint/smells achoholic/tastes like rust metal
EFFEC Inspires drinker to dance
```

### Mike Haggar
For a fairly complex example, let's make Mike Haggar from the Final Fight
series. For our entry, we want to describe him with:
- A human male, with a height of 202cm and weight of 140kg.
- Appears with a stocky, muscular build with big arms; additionally, he has
  short brown hair and a matching brown mustache.
- Wears brown boots, green pants, and a bandolier; at work, he also wears
  eyeglasses.
- Has a just, direct personality — he's a hardy and upright guy.
- He likes curry and rice.
- He's friends with Cody, Guy, and Carlos (who's from Brazil).
- Has a daughter, Jessica.
- Has the following bio:
  - Born in 1943, and is from the games Final Fight and Street Fighter.
  - Is an ex pro wrestler, and grew up on the streets of Metro City; currently,
    he's the mayor of Metro City.
  - Fought the Mad Gear and Skull Cross gangs, and fights gangs in general.

The NaCL (473 characters and 119 tokens):
```
[Mike Haggar] Human/male/202cm/140kg
APPE stocky&muscular/big arms/short_brown_hair&brown_mustache
MIND just/direct/hardy/upright
WEAR eyeglasses(at work)/brown_boots&green_pants/bandolier
SUMM born 1943/from games Final_Fight&Street_Fighter/pro_wrestler(ex)/grew up on streets of Metro City/Mayor of Metro City/fought_gangs(Mad_Gear&Skull_Cross)/fights gangs
LIKE curry&rice
QUOTE "It's my job to keep Metro City safe!"
FRIEND Cody&Guy&Carlos(from Brazil)
DAUGHTER Jessica
```

On testing, the NaCL worked well; Mike Haggar referenced all his details during
a conversation. At 119 tokens, this is a pretty impressive amount of information
to put in such a small amount of space — we've crunched Mike Haggar, with his
details and biographical info, into less than 500 characters. For comparison,
when I took the list of details used to make the NaCL itself it reported at
177 tokens.

&nbsp;

### Author's Note (A/N)

As the A/N section of a scenario is a set of instructions, rather than describing
something specific, there is no header or description — only details.

See [this resource](https://justpaste.it/9ofj1) on words to use with author's
notes and their effects to get a good idea on words to use with the keywords
(while the page says it's outdated, my testing finds it still works pretty
well for AI Dungeon).

For example, let's say we want author's note for a story with the following
criteria:
- Fantasy world
- Romance story
- Potential for good NSFW content
- AI tries to be realistic and creative for the general fantasy content

Some good author's notes in NaCL format would be:
```
RTNG R-RATED
GENR romance
STYL verbose, talkative, romantic, arousing, inventive, realistic
THEM fantasy
```

An explanation of each line:
- `RTNG R-RATED`
	- This sets the rating to an adult rating that shouldn't shy away from
	  NSFW content, if that's where the story goes. Could also use `X-RATED`
	  if `R-RATED` is somehow shying away from NSFW or you want the story to
	  attempt to bring in NSFW on its own.
- `GENR romance`
	- This is fairly straightforward, as the genre is romance.
- `STYL verbose, talkative, romantic, arousing, slow burn, inventive, realistic`
	- This is a bit more complex:
		- `verbose` hints for the AI to be more descriptive with more dialogue.
		- `talkative` hints to add more dialogue, focusing on smalltalk for
		  a better "slice of life" feel to the slower portions of the story.
		- `romantic` is straightforward, matching the genre.
		- `arousing` is a good hint for general NSFW content, as it hints for
		  the AI to slow down during NSFW scenes and be more descriptive.
		  Normally it's like the AI might try to speedrun NSFW scenes, so this
		  helps keep their pace in line with the rest of the story.
		- `slow burn` is like arousing in that it hints to slow down with
		  NSFW content while not "bleeding" NSFW into the rest of the story, and
		  also implies slowing down romance as well.  
		  Note that "arousing" and "slow burn" stack together, and the result
		  is subjective on if it's "too slow" or "just right".
		- `inventive` is a good hint for stories that can have action; as the
		  word says, the AI will try to be more inventive and creative with
		  how things play out. Instead of a dodge, a character may pull a
		  dextrous maneuver using their skills.  
		  This may also *slightly* help with NSFW content, hinting to write
		  something a little more creative than straightforward.
		- `realistic` hints to keep character actions, well, realistic and a
		  little more intelligent. Instead of rushing into a fight, the AI
		  may have them sneak around to gain advantage.
- `THEM fantasy`
	- Straightforward; this signals that the story has a fantasy theme to it.

&nbsp;

As a note, the example author's notes clocks in at a relatively small 116
characters (34 tokens) but conveys all of the information above to the AI in
a generally effective manner. As AI Dungeon will toss out the A/N entirely if
it can't fit, keeping it as small as possible is great.

### Memory

For writing scenario memory, you can just use the format we've covered so far
when describing any characters or locations.

But what if we want to describe general story details?  
For that, NaCL has a small bit extra.

To keep things easier to read, a different kind of header will be used for
story details. A story header is written `|Like This|`.  
For example, `|Setting|`.

For an story details, start them with a `> `.

#### Red Fox

As an example, let's write some memory for a scenario where:
- You are a red fox, with variables for your name and gender.
- You are a bit of a trickster.
- As part of the story, you are looking for your lost parents.

For this, the NaCL would be:
```
[You] named("${Your name?}")/red fox/${Your gender?}
SUMM trickster

|Plot|
> You are looking for your lost parents
```

#### Taco Adventure

As another example, let's say we have a scenario where:
- You are a human, with variables for your name and gender.
  - You're cool, with lots of friends.
  - You have not watched Die Hard.
- You have a friend Mark, who is a human male.
- As part of the plot:
  - You learned some Spanish and Italian.
  - You're craving a Doritos Locos Taco.

The NaCL would be:
```
[You] named("${Your name?}")/human/${Your gender?}
FRIEND mark
SUMM cool(have lots of friends)/have not watched die hard

[Mark] human/male
FRIEND you

|Plot|
> You learned some Spanish and Italian
> You are craving a Doritos Locos Taco
```

<br>

As you can see, the context is nice and organized, and you can get a decent
grasp of how the story for the scenario should work without even having to
read this hypothetical taco-ordering adventure.

<br>

### Good Memory Practices

As an AI can always make mistakes, there are some practices for writing memory
that I find work and make things easier for the AI:

1. Keep each piece of information as direct and straightforward as possible.
- As mentioned earlier, the AI will have to cut information if things get too
  big.   
  To help the AI, keep each individual note free of details or writing that
  is unnecessary. If you need to expand on an idea, use nested info markers
  and add additional notes expanding on the main one for a concept.
- If it works for you, a "caveman" strategy could work, where you just 
completely remove all uneeded words.  
  For example, here's a normal piece of NaCL:
  ```
  > Jim needs to rescue the princess of the kingdom
  ```
  Here's the "caveman" version:
  ```
  > Jim need rescue princess
  ```
  I wouldn't recommend this unless you have a large amount of
  memory and are worried about it being long enough for the AI to
  cut off or get confused about.
- Your memory should not be just your intro story copy and pasted.  
  There's literally no point for that; AI Dungeon will just use your intro
  as memory if you don't have your own.  
  Instead, your memory should be a list of notes and details about the
  fundamental points of your scenario. The intro story is the
  body, and the memory should be a skeleton that allows the AI to keep
  the body moving in a way that fits.

2. Remove as much ambiguity as possible.
- An AI is just a piece of software trying to make a good guess on the
  text you give it, it's not infallible and sometimes makes dumb mistakes
  when trying to interpret the subject of something, even when the subject
  is easy to infer.
- When you can, explicitly write the name of whatever the subject of a
  memory note is.  
  Avoid starting a note with generic pronouns that the AI could potentially
  confuse with someone else, like "she" or "her".  
  For example:
  ```
  |Plot|
  > Mark has been branded as the chosen one
  > Mark is secretly an elf
  ```  
  If we put "He" instead of "Mark" in these lines, the AI could be really
  dumb and just think "He" refers to some other male in the story. When
  we explicitly say each thing is about Mark, there's no easy way for the
  AI to get confused on the subject.
- Related, keep however you reference the player character consistent.  
  If using second person, use "You"/"Your" to refer to them; if third
  person, use the player character's name.  
  Simply add a note about the player character's name in the section for
  them to have the AI remember.  

3. Consider what needs to be a put in the memory.
- Memory should, as mentioned before, be a skeleton for the fundamental
  details of your story.  
  Unless your scenario is outright intended to be short, it'd be better to
  not put temporary details about the start of your story in it.
  The memory is always referenced, so the AI could get confused and think
  details about the start of the story are still in play even when the
  player is way past the start.
- Immutable details are good for memory, like a character's race and name.  
  Even then, details other than the basics should be put into a story card
  if you can. This will help keep your memory shorter and easier to read for
  the players of your story.
- An ideal memory is one that a player could add to if they want to, rather
  than removing from to make things work.  
  While NaCL could be a bit more intimidating to read compared to prose, as
  some people may be intimidated by a serious format, it's still relatively
  straightforward and organized.