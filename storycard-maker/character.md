---
tabs: storycard-maker-tabs
---

<style>
	form  { display: table;      }
	p     { display: table-row;  }
	label { display: table-cell; }
	input { display: table-cell; }
</style>

*Note:*  
*Things with a `*` at the end can be a list of things separated with a
`/` (ex: `brown eyes/tan skin`)*

&nbsp;

**Only fill in what you need to.**  
**Unnecessary details can waste space and hurt the AI.**

## Description

<form>
	<p>
		<label for='sc-name'>Name</label>
		<input type='text' id='sc-name' name='sc-name' required placeholder='required'>
	</p>

	<p>
		<label for='sc-race'>Race</label>
		<input type='text' id='sc-race' name='sc-race' required placeholder='required'>
	</p>
	<p>
		<label for='sc-gender'>Gender</label>
		<input type='text' id='sc-gender' name='sc-gender' required placeholder='required'>
	</p>
	<p>
		<label for='sc-age'>Age</label>
		<input type='text' id='sc-age' name='sc-age' required placeholder='required'>
	</p>
	<p>
		<label for='sc-personality'>Personality*&nbsp;</label>
		<input type='text' id='sc-personality' name='sc-personality'>
	</p>
	<p>
		<label for='sc-traits'>Notable Traits*&nbsp;</label>
		<input type='text' id='sc-traits' name='sc-traits'>
	</p>
</form>

## Appearance

<form>
	<p>
		<label for='sc-features'>Features*&nbsp;</label>
		<input type='text' id='sc-features' name='sc-features'>
	</p>

	<p>
		<label for='sc-build'>Build*&nbsp;</label>
		<input type='text' id='sc-build' name='sc-build'>
	</p>
	<p>
		<label for='sc-outfit'>Outfit*&nbsp;</label>
		<input type='text' id='sc-outfit' name='sc-outfit'>
	</p>
</form>

## Relationships

<form>
	<p>
		<label for='sc-friends'>Friends*&nbsp;</label>
		<input type='text' id='sc-friends' name='sc-friends'>
	</p>

	<p>
		<label for='sc-family'>Family*&nbsp;</label>
		<input type='text' id='sc-family' name='sc-family'>
	</p>
	<p>
		<label for='sc-allies'>Allies*&nbsp;</label>
		<input type='text' id='sc-allies' name='sc-allies'>
	</p>
	<p>
		<label for='sc-enemies'>Enemies*&nbsp;</label>
		<input type='text' id='sc-enemies' name='sc-enemies'>
	</p>
</form>

## Miscellaneous

<form>
	<p>
		<label for='sc-powers'>Powers*&nbsp;</label>
		<input type='text' id='sc-powers' name='sc-powers'>
	</p>
	<p>
		<label for='sc-inventory'>Inventory*&nbsp;</label>
		<input type='text' id='sc-inventory' name='sc-inventory'>
	</p>
	<p>
		<label for='sc-accent'>Accent&nbsp;</label>
		<input type='text' id='sc-accent' name='sc-accent'>
	</p>
	<p>
		<label for='sc-diet'>Diet*&nbsp;</label>
		<input type='text' id='sc-diet' name='sc-diet'>
	</p>
	<p>
		<label for='sc-likes'>Likes*&nbsp;</label>
		<input type='text' id='sc-likes' name='sc-likes'>
	</p>
	<p>
		<label for='sc-hates'>Hates*&nbsp;</label>
		<input type='text' id='sc-hates' name='sc-hates'>
	</p>
	<p>
		<label for='sc-hobbies'>Hobbies*&nbsp;</label>
		<input type='text' id='sc-hobbies' name='sc-hobbies'>
	</p>
	<p>
		<label for='sc-other'>Other*&nbsp;</label>
		<input type='text' id='sc-other' name='sc-other'>
	</p>
</form>

&nbsp;

<form>
	<input type='button' value='Generate Story Card' onclick='generateCard()'>
	<input type='button' value='Reset' onclick='resetInputs()'>
</form>

<textarea id='output-area' readonly disabled rows=20 cols=70 wrap='soft'>
</textarea>

<script>
function resetInputs() {
	const inputs = document.getElementsByTagName('form')

	for (const form of inputs) {
		form.reset()
	}
}

function generateCard() {
	const inputData = {
		name: '', race: '', gender: '', age: '', personality: '',
		traits: '', features: '', build: '', outfit: '',
		friends: '', family: '', allies: '', enemies: '',
		powers: '', inventory: '', accent: '', diet: '', likes: '',
		hates: '', hobbies: '', other: ''
	}
	for (const dataType in inputData) {
		inputData[dataType] = document.getElementById(`sc-${dataType}`).value
	}

	const x = inputData

	// These fields are required
	if (!x.name || !x.race || !x.gender || !x.age) { return }


	let result = `[${x.name}]\n> ${x.race}/${x.gender}/${x.age}.`

	document.getElementById('output-area').value = result
}
</script>