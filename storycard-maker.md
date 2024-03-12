---
tabs: storycard-maker-tabs
---

<style>
	form  { display: table;      }
	p     { display: table-row;  }
	label { display: table-cell; }
	input { display: table-cell; }
</style>

*Note: Things with a `*` at the end can be a list of things separated with a
`/` (ex: `brown eyes/tan skin`)*

## Description

<form>
	<p>
		<label for='sc-name'>Name</label>
		<input type='text' id='sc-name' name='sc-name'>
	</p>

	<p>
		<label for='sc-race'>Race</label>
		<input type='text' id='sc-race' name='sc-race'>
	</p>
	<p>
		<label for='sc-gender'>Gender</label>
		<input type='text' id='sc-gender' name='sc-gender'>
	</p>
	<p>
		<label for='sc-age'>Age</label>
		<input type='text' id='sc-age' name='sc-age'>
	</p>
	<p>
		<label for='sc-personality'>Personality*&nbsp;</label>
		<input type='text' id='sc-personality' name='sc-personality'>
	</p>
</form>

## Appearance
*Note: Separate things with a `/` (ex: `brown eyes/tan skin`)*

&nbsp;

<form>
	<p>
		<label for='sc-features'>Features</label>
		<input type='text' id='sc-features' name='sc-features'>
	</p>

	<p>
		<label for='sc-build'>Build</label>
		<input type='text' id='sc-build' name='sc-build'>
	</p>
	<p>
		<label for='sc-outfit'>Outfit</label>
		<input type='text' id='sc-outfit' name='sc-outfit'>
	</p>
</form>

&nbsp;

<form>
	<input type='submit' value='Generate Story Card'>
</form>