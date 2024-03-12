---
title: NaCL Keywords
# subtitle: Optimized Context
# hero_link:
# hero_link_text:
toc: true
---

There are many possible keywords that can be work with the AI.  
An old compilation of them can be found
[here](https://github.com/valahraban/AID-World-Info-research-sheet/blob/main/AID%20WI%20Research%20Sheet.md#categories-table).

For convenience, I have read through the linked research sheet (and some other
sources) and compiled my own list of keywords and descriptions for what they
do and how they can be used; additionally, I have separated the list into
keywords that are good for individual entities and ones that are good for
describing locations.

Note that this is not the be-all and end-all list of keywords.  
If you feel you have a better word for a specific kind of information, try it
out and see if the AI uses it as you want it to. If it makes sense, you can
use entity keywords with locations and vice-versa.  
This list is just keywords that were noted to be effective and consistent.

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
    <td>Generic info category.<br>Good for anything that doesn't fit in with others, prose-like info, or stating things you want consistently described.<br>If you have a personality trait that you <i>really</i> want to shine, put it in here.</td>
    <td>nickname("Jimmy"); collects eggs</td>
  </tr>
  <tr>
    <td>DETA</td>
    <td>Details</td>
    <td>Similar to summary, but good for details on inanimate objects.</td>
    <td>runic symbol; gold finish</td>
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
    <td>GRAB</td>
    <td>Grabbing</td>
    <td>How an entity grabs/manipulates objects.</td>
    <td>pincers</td>
  </tr>
  <tr>
    <td>TRA</td>
    <td>Traits</td>
    <td>Fundamental, literal traits about an entity.<br>MIND affects behavior, TRA affects how something <span style="font-style:italic">is</span><span style="font-style:normal">.</span><br><span style="font-style:normal">Only use TRA if it's something that </span><span style="font-style:italic">shouldn't</span><span style="font-style:normal"> be subtle.</span></td>
    <td>seductive</td>
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
    <td>SEE</td>
    <td>See</td>
    <td>Description of how the entity senses and/or perceives things around them.</td>
    <td>echolocation</td>
  </tr>
  <tr>
    <td>LIMIT</td>
    <td>Limitations</td>
    <td>Limiting features for entity.<br>Best for limitations described with numbers (quantitative).</td>
    <td>one arm</td>
  </tr>
  <tr>
    <td>LACK</td>
    <td>Lacking</td>
    <td>Limiting features for entity.<br>Best for limitations described without numbers (qualitative).</td>
    <td>eyes</td>
  </tr>
  <tr>
    <td>COND</td>
    <td>Condition</td>
    <td>What conditions an entity has, like a status effect.</td>
    <td>poisoned</td>
  </tr>
  <tr>
    <td>STATUS</td>
    <td>Status</td>
    <td>Status, as in "title or association to something"; not a status condition.</td>
    <td>headmaster</td>
  </tr>
  <tr>
    <td>TITLE</td>
    <td>Title</td>
    <td>The literal title for an entity, which they may be called.</td>
    <td>the drunken wizard</td>
  </tr>
  <tr>
    <td>ALIGN</td>
    <td>Alignment</td>
    <td>The moral/ethical alignment of the entity.<br>Can use well-known tabletop RPG alignments like "Chaotic Good", or common joke ones like "Lawful Stupid".</td>
    <td>true neutral</td>
  </tr>
  <tr>
    <td>MOTIV</td>
    <td>Motivation</td>
    <td>Any motivations or driving passions for an entity.</td>
    <td>find a husband</td>
  </tr>
  <tr>
    <td>QUOTE</td>
    <td>Quotes</td>
    <td>Quotes for a character; can be used to give examples for a specific accent you want them to speak with.</td>
    <td>"Oh boy I sure do love brownies"</td>
  </tr>
  <tr>
    <td>LOOT</td>
    <td>Loot</td>
    <td>What entity drops on defeat, or can be taken on search.</td>
    <td>$20 bill</td>
  </tr>
  <tr>
    <td>ADJ</td>
    <td>Adjectives</td>
    <td>Notable adjectives to insert into descriptions of entity.</td>
    <td>radical</td>
  </tr>
  <tr>
    <td>MODIF</td>
    <td>Modifiers</td>
    <td>Modifiers to insert into descriptions of entity.<br>ADJ is more like a prefix, while MODIF is like a suffix.</td>
    <td>plumber extraordinaire</td>
  </tr>
  <tr>
    <td>GRAM</td>
    <td>Grammar</td>
    <td>Describe speech patterns when entity communicates.</td>
    <td>all caps</td>
  </tr>
  <tr>
    <td>VOCAB</td>
    <td>Vocabulary</td>
    <td>Describes vocab entity uses to speak.<br>GRAM describes format, VOCAB describes words.</td>
    <td>japanese</td>
  </tr>
  <tr>
    <td>INV</td>
    <td>Inventory</td>
    <td>List of things held in inventory.</td>
    <td>bomb, carrot</td>
  </tr>
  <tr>
    <td>EQUIP</td>
    <td>Equipped</td>
    <td>List of currently equipped/held things.</td>
    <td>sword</td>
  </tr>
  <tr>
    <td>LIKE</td>
    <td>Likes</td>
    <td>Describe things liked by entity.</td>
    <td>carrots</td>
  </tr>
  <tr>
    <td>HATE</td>
    <td>Hates</td>
    <td>Describe things hated/disliked by entity.<br></td>
    <td>arugula</td>
  </tr>
  <tr>
    <td>RELATE</td>
    <td>Relationships</td>
    <td>Describe general relations to others.</td>
    <td>jim (roommate)</td>
  </tr>
  <tr>
    <td>ALLY</td>
    <td>Allies</td>
    <td>Describe positive relation.</td>
    <td>jim</td>
  </tr>
  <tr>
    <td>ENEM</td>
    <td>Enemies</td>
    <td>Describe negative relation.</td>
    <td>jim</td>
  </tr>
  <tr>
    <td>CREATE</td>
    <td>Creates</td>
    <td>Whatever entity is able to create/produce.</td>
    <td>egg</td>
  </tr>
  <tr>
    <td>BANN</td>
    <td>Banned</td>
    <td>Behavior that is forbidden</td>
    <td>talking about eggs</td>
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