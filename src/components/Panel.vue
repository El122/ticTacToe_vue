<template>
	<div>
		<h2>Информация об игре</h2>
		<div class="line"></div>
		<div class="data">
			<div class="data-block">
				<span class="data-title">Сейчас ходит</span>
				<span class="data-info">{{currentPlayer}}</span>
			</div>
			<div  class="data-block">
				<span class="data-title">Осталось ходов</span>
				<span class="data-info">{{ 9 - moveCounter }}</span>
			</div>
			<div  class="data-block">
				<span class="data-title">Счет</span>
				<span class="data-info">{{score.player1}}:{{score.player2}}</span>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "Panel",
	props: ["currentPlayer", "moveCounter", "score"]
};
</script>

<style scope>
	.data-block {
		display: flex;
		justify-content: space-between;
		padding: 10px;
		border-bottom: 1px solid #d8e2dc;
	}

	.data-title {
		font-weight: bold;
	}
</style>