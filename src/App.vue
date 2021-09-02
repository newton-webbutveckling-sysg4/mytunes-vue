<template>
	<header>
		<h1> MyTunes </h1>
	</header>

	<div class="search">
		<input type="text" value="" placeholder="Search title..."
			v-on:keyup="onSearchChange" />
	</div>

	<main>
		<div class="card" v-for="song in filteredSongs"
			v-bind:key="song.title + song.artist">
			<h3> {{ song.title }} </h3>
			<span> {{ song.artist }} </span>
			<span> {{ song.album }} </span>
			<span> {{ song.release }} </span>
			<span> {{ song.genre }} </span>
		</div>
	</main>
</template>


<script>
export default {
	name: 'App',
	components: { },
	data() {
		return {
			searchText: '',
			songs: [
				{
					title: 'Africa',
					artist: 'Toto',
					album: 'Toto IV',
					release: '1982',
					genre: 'pop'
				},
				{
					title: 'I want to hold your hand',
					artist: 'The Beatles',
					album: 'Meet the Beatles!',
					release: 1964,
					genre: 'rock'
				},
				{
					title: 'No line on the horizon',
					artist: 'U2',
					album: 'No line on the horizon',
					release: 2009,
					genre: 'alternative rock'
				}
			]
		}
	}, // data
	methods: {
		onSearchChange(event) {
			this.searchText = event.target.value
		}
	}, // methods
	computed: {
		filteredSongs() {
			const search = this.searchText.toLowerCase()
			return this.songs.filter(song => song.title.toLowerCase().includes(search))
		}
	}
}
</script>




<style>
body {
	margin: 0px;
}
header {
	background: #A4C7E2;
}
header h1 {
	margin: 0px;
	padding: 0.5em 2em;
}

.search {
	padding: 2em;
	text-align: center;
	border-bottom: 2px solid lightgray;
}
.search > input {
	font-size: 1.5em;
}

main {
	padding: 2em;
	display: grid;
	grid-template-columns: 1fr 1fr;
}
.card {
	display: flex;
	flex-direction: column;
	border: 1px solid black;
	padding: 0.5em;
	margin: 0.3em;
}
.card > :nth-child(1) {
	font-weight: bold;
}
.card h3 {
	margin: 0em;
}

</style>
