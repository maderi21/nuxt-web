<template>
	<div>
		<Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
	</div>
</template>

<script>
import axios from "axios";
import Joke from "~/components/Joke";


export default {
	components: {
		Joke
	},

data() {
	return {
		jokes: []
	};
},

async created()
{
	const config = {
		headers: {
			Accept: 'application/json'
		}
	};

try {
	const res = await axios.get("https://icanhazdadjoke.com/search", config);
	this.jokes = res.data.resutls;

} catch (err) {
console.log(err);
}


},

head() {
	return {
		title: 'Dad Jokes',
		meta: [
			{
				hid: 'despriction',
				meta: 'description',
				content: 'best place for corny dad jokes'
			}
		]
	}
}
}
</script>

<style>
</style>