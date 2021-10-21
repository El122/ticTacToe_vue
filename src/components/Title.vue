<template>
	<header>
		<h1>Tic-Tac-Toe</h1>
		<button v-on:click="startGame">{{ !isStarted ? "Старт" : "Стоп" }}</button>
	</header>
</template>

<script>
export default {
	name: "Title",
	props: {
		isStarted: Boolean,
	},
	methods: {
		startGame: function() {
			this.$emit("startGame", true);
		},
	},
};
</script>

<style scoped>
header {
	padding: 20px;

	display: flex;
	justify-content: space-between;
	align-items: center;

	background-color: #ffe5d9;
}

h1 {
	margin: 0;
	padding: 0;
}

button {
	padding: 10px 20px;
	background-color: #f4acb7;
	border: none;

	font-size: 30px;
	color: #ffe5d9;

	cursor: pointer;
}

button:hover {
	background-color: #9d8189;
}
</style>
