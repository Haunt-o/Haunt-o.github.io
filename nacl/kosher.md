---
title: Kosher NaCL
subtitle: Organized Context
layout: page
toc: true
---

## Preface

The simplified version of my context format — "Kosher Salt" — is designed to be
straightforward, simple, and easy for players to read and edit.

Everything is nice and organized, and you can easily add or delete bits of
context as you need to.

## Format

### Headers

 When you want to mark what a specific section of the context is about, a header
 is used.  
 There are two kinds of headers: &nbsp; *Noun Headers* and *Concept Headers*.

- **Noun Header**
	- A noun header is formatted like `[Thing]`.
	- They mark that the section under it has context details about the noun.
	- Examples:
		- `[Jim]`
		- `[The Headquarters]`
		- `[The Pumpkin King]`

- **Concept Header**
	- A concept header is formatted like `|Stuff|`
	- They mark that the section under it has context details about some idea.
	- Examples:
		- `|Setting|`
		- `|Plot|`
		- `|Relationships|`


### Info Markers

Each piece of scenario context is the information you want the AI to
remember, so this format has a way to mark each piece of information.

To mark a piece of information, you put a `>` at the beginning.  
For example:
```
> You are cool.
```

#### Nested Info Marker

When you have context info that is related to another piece of info — a
sort of "sub-context" info — you add a `|` to mark info as being part
of the info above it.  
For example:
```
> You are cool.
>| You wear cool shades.
```

If you have nested info on your nested info, just put another `|` at the
end, like `>||`.  
For example:
```
> You are cool.
>| You wear cool shades.
>|| Your cool shades are made of coolium.
```

&nbsp;

### Good Practices

As an AI can always make mistakes, there are some practices for writing context
notes that I find work and may make things easier for the AI:

1. Keep each piece of information as direct and straightforward as possible.
- When an AI is fed too much text at once, its ability to keep track of
  everything at the same time starts to weaken. It's good to be safe
  instead of sorry.  
  To help the AI, keep each individual note free of details or writing that
  is unnecessary.
- If it works for you, a "caveman" strategy could work, where you just 
completely remove all uneeded words.  
  For example, here's a normal piece of NaCL:
  ```
  > Jim has green eyes and long hair.
  ```
  Here's the "caveman" version:
  ```
  > Jim green eye. Long hair.
  ```
  I wouldn't recommend this unless you have a large amount of
  memory and are worried about it being long enough for the AI to
  cut off or get confused about —
  part of the goal of NaCL is to be a combination of effective for
  scenario creators and readable by scenario players.
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
  context note is.  
  Avoid starting a note with generic pronouns that the AI could potentially
  confuse with someone else, like "she" or "her".  
  For example:
  ```
  [Mark]
  > Mark is male.
  > Mark is cool.
  > Mark is your friend.
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
  For example:
  ```
  [You]
  > You are named Jim.
  > You are cool.
  > Your hand is slightly big.
  ⠀
  [Mark]
  > Mark is friends with you.
  ```

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
  if you can.
- An ideal memory is one that a player could add to if they want to, rather
  than removing from to make things work.  
  While NaCL could be a bit more intimidating to read compared to prose, as
  some people may be intimidated by a serious format, it's still relatively
  straightforward and organized.

### Author's Notes

As the A/N section of a scenario is a set of instructions, rather than describing
something specific, there is no header or description — only details.

Authors notes use the following 4-letter keywords to convey writing information:

| Keyword 	|       Meaning       	|                Examples                	|
|:-------:	|:--------------------	|:---------------------------------------	|
|   STYL  	| Writing Style       	| verbose, talkative, romantic, arousing 	|
|   GENR  	| Genre for Story     	| comedy, romance, horror                	|
|   TONE  	| Tone of Story       	| depressing, tragic, upbeat             	|
|   RTNG  	| Rating of story     	| PG, PG-13, M, R, X-RATED               	|
|   THEM  	| Theming of Story    	| fantasy, sci-fi, western               	|
|   NOTE  	| Misc. Writing Notes 	| Literally anything                        |

See [this resource](https://justpaste.it/9ofj1) on words to use with author's
notes and their effects to get a good idea on words to use with the keywords
(while the page says it's outdated, my testing finds it still works pretty
well for AI Dungeon).

Each keyword, and the words for them, goes on its own line.

For example, let's say we want author's note for a story with the following
criteria:
- Fantasy world
- Romance story
- Potential for good NSFW content
- AI tries to be realistic and creative for the general fantasy content

Some good author's notes in NaCL format would be:
```
RTNG R-RATED.
GENR romance.
STYL verbose, talkative, romantic, arousing, inventive, realistic.
THEM fantasy.
```

An explanation of each line:
- `RTNG R-RATED.`
	- This sets the rating to an adult rating that shouldn't shy away from
	  NSFW content, if that's where the story goes. Could also use `X-RATED`
	  for a higher amount of NSFW.
- `GENR romance.`
	- This is fairly straightforward, as the genre is romance.
- `STYL verbose, talkative, romantic, arousing, inventive, realistic.`
	- This is a bit more complex:
		- "Verbose" hints for the AI to be more descriptive with more dialogue.
		- "Talkative" hints to add more dialogue, focusing on smalltalk for
		  a better "slice of life" feel to the slower portions of the story.
		- "Romantic" is straightforward, matching the genre.
		- "Arousing" is a good hint for general NSFW content, as it hints for
		  the AI to slow down during NSFW scenes and be more descriptive.
		  Normally it's like the AI might try to speedrun NSFW scenes, so this
		  helps keep their pace in line with the rest of the story.
		- "Inventive" is a good hint for stories that can have action; as the
		  word says, the AI will try to be more inventive and creative with
		  how things play out. Instead of a dodge, a character may pull a
		  dextrous maneuver using their skills.
		- "Realistic" hints to keep character actions, well, realistic and a
		  little more intelligent. Instead of rushing into a fight, the AI
		  may have them sneak around to gain advantage.
- `THEM fantasy.`
	- Straightforward; this signals that the story has a fantasy theme to it.

&nbsp;

As a note, the example author's notes clocks in at a relatively small 112
characters but conveys all of the information above to the AI in a generally
effective manner.

&nbsp;

### Full NaCL Example

If the individual examples don't give you a good grasp on how all of the NaCL
format comes together, here's a full bit of context for a scenario:
```
[You]
> You are named Jim.
> You are male.
> You are cool.
>| You have lots of friends.
> You have not watched die hard.

[Mark]
> Mark is male.
> Mark is your friend.

|Plot|
> You learned some Spanish.
> You learned some Italian.
> You are craving a Doritos Locos Taco.
```

Author's Notes:
```
GENR thriller, adventure.
STYL descriptive, creative.
```

&nbsp;

As you can see, the context is nice and organized, and you can get a decent
grasp of how the story for the scenario should work without even having to
read this hypothetical taco-ordering adventure.