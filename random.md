---
title: Random Writing Prompt Generator
override: true
sitemap: false
categories: 
    - meta
---

Your genre is: <span id="genre"></span>.

Your two wikipedia links are [here](https://en.wikipedia.org/wiki/Special:Random) and [here](https://en.wikipedia.org/wiki/Special:Random).

<script>
	var genre=["Drama", "Fable", "Fairy Tale", "Fantasy", "Folklore", "Historical Fiction", "Horror", "Humour", "Legend", "Mystery", "Mythology", "Realistic Fiction", "Science Fiction"]; 
	var random = Math.round(Math.random() * (genre.length -1));
	var selection = genre[random];

	document.getElementById("genre").innerHTML=selection;
</script>
