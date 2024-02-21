---
title: Haunto
subtitle: AI Dungeon Guy
layout: page
callouts: home_callout
hero_link: "https://play.aidungeon.com/profile/Haunto?contentType=scenario"
hero_link_text: "AI Dungeon Page"
hero_image: /images/haunto_home_banner.jpg
hero_height: is-small
# toc: true
# menubar_toc: true
# toc_title: Title Here
---

<!-- PAGE VIEW COUNT API SCRIPT -->
{% if true %}
<script>
	var xhr = new XMLHttpRequest();
	xhr.open("GET", "https://api.countapi.xyz/hit/haunto_github/visits");
	xhr.responseType = "json";
	xhr.onload = function() {
		document.getElementById('visits').innerText = this.response.value;
	}
	xhr.send();

	console.log(this.response)
</script>
{% endif %}
<!-- END PAGE VIEW COUNT API SCRIPT -->

{% include notification.html
message="Welcome to my home page!"
icon="false"
status="is-primary" %}


&nbsp;

This website is for allowing easy access to all of the AI Dungeon resources
I've researched, seen, or developed myself.

There is a *lot* that can go into making AI Dungeon scenarios, and I want to
make sure everyone has the ability to learn as much as they can and have
access to any tools that would help make things easier.

<span id="visits">x</span> page visits