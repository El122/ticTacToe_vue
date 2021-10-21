<template>
	<div class="game-grid">
		<div v-for="(item, index) in board" :key="index" @click="cellClick" :data-cell-index="index" class="game-grid_cell"></div>
	</div>
</template>

<script>
export default {
	name: "Grid",
	props: ["board"],
	methods: {
		cellClick: function(e) {
			this.$emit("cellClick", e.target);
		},
	},
};
</script>

<style scoped>
.game-grid {
	margin: auto;

	display: grid;
	grid-template-columns: repeat(3, 200px);
	grid-template-rows: repeat(3, 200px);
	border: 3px solid #9d8189;
	padding: 10px;
}

.game-grid_cell {
	border: 2px solid #7a5e66;
	cursor: pointer;
}

.game-grid_cell:hover {
	background-color: #f4acb7;
}

.game-grid_cell.choosen {
	background-color: #d8e2dc;
	cursor: default;
}

.cellO {
	background-image: url("https://sun9-5.userapi.com/impg/KYsUkgJzHfWjoVS2eqp7wrb5fkXA5NZPTbTisw/8UQANkzKXfk.jpg?size=1280x576&quality=96&sign=b5b0b4f8f16fee4f28866133aac01f24&type=album");
	background-size: cover;
	background-position: center;
}

.cellX {
	background-image: url("https://sun9-88.userapi.com/impg/xTmVokmmeNFneVTEqHL1-grp7PNCZ7HGTkvo5Q/nwZqqIa3QnQ.jpg?size=1280x576&quality=96&sign=688bc5aaf2a6a2afe5b3b78b69138cc6&type=album");
	background-size: cover;
	background-position: center;
}
</style>
