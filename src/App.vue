<template>
	<div id="app">
		<Title @startGame="startGame" :isStarted="isStarted" />
		<div class="container">
			<Grid v-if="isStarted" @cellClick="cellClick" :board="board" />
			<p class="gameNotStart" v-else>{{ winnerText }}</p>
			<Panel
				:currentPlayer="currentPlayer"
				:moveCounter="moveCounter"
				:score="score"
			/>
		</div>
	</div>
</template>

<script>
import Title from "./components/Title.vue";
import Grid from "./components/Grid.vue";
import Panel from "./components/Panel.vue";

export default {
	name: "App",
	components: {
		Title,
		Grid,
		Panel,
	},
	data: function() {
		return {
			winConditions: [
				[0, 1, 2],
				[3, 4, 5],
				[6, 7, 8],
				[0, 3, 6],
				[1, 4, 7],
				[2, 5, 8],
				[0, 4, 8],
				[2, 4, 6],
			],
			isStarted: false,
			winnerText: "Нажмите СТАРТ для начала игры",
			currentPlayer: "X",
			board: ["", "", "", "", "", "", "", "", ""],
			moveCounter: 0,
			score: {
				player1: 0,
				player2: 0,
			},
		};
	},
	methods: {
		startGame() {
			const started = this.isStarted;
			this.nullData();
			this.isStarted = !started;
		},
		cellClick(elem) {
			const cell = elem.getAttribute("data-cell-index");
			if (this.board[cell] != "") return;

			elem.classList.add("cell" + this.currentPlayer);
			this.board[cell] = this.currentPlayer;

			if (!this.checkWinners() && this.moveCounter == 9) {
				this.nullData();
				this.winnerText = "Нет победителей";
			}
		},
		nullData() {
			this.isStarted = false;
			this.board = ["", "", "", "", "", "", "", "", ""];
			this.currentPlayer = "X";
			this.moveCounter = 0;
		},
		checkWinners() {
			for (let i = 0; i < 7; ++i) {
				const winCondition = this.winConditions[i];
				if (
					this.board[winCondition[0]] != "" &&
					this.board[winCondition[0]] == this.board[winCondition[1]] &&
					this.board[winCondition[1]] == this.board[winCondition[2]]
				) {
					if (this.currentPlayer == "X") ++this.score.player1;
					else ++this.score.player2;
					this.winnerText = "Победитель - игрок " + this.currentPlayer;
					this.nullData();
					return true;
				}
			}
			this.currentPlayer = this.currentPlayer == "X" ? "O" : "X";
			++this.moveCounter;
			return false;
		},
	},
};
</script>

<style>
body {
	margin: 0;
	padding: 0;
	background-color: #ffcad4;
}

#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	color: #9d8189;
	margin: 0;
}

.container {
	padding: 20px;

	display: grid;
	grid-template-columns: 3fr 1fr;
}

.gameNotStart {
	text-align: center;
	margin: 20px;
	font-weight: 900;
}
</style>
