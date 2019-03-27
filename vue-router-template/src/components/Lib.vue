<template>
	<div class="container">
		<div class="side">
			<router-link to="/lib_tiku">题库</router-link>
			<router-link to="/lib_ziyuanku">资源库</router-link>
			<router-link to="/lib_huodongku">活动库</router-link>
		</div>
		<div class="card"><router-view /></div>
	</div>
</template>

<script>
export default {
	name: 'Lib',
	data() {
		return {
			
		};
	}
};
</script>

<style scoped>
	
	.container {
		display: flex;
		width: 90%;
		height: 90%;
		margin: 0 auto;
	    flex-direction: column;
	}
	.side {
		flex: 1 1 8%;
		display: flex;
		background-color: #fff;
		
	}
	
	.card{
		flex: 1 1 80%;
		text-align: left;
		background-color: #fff;
		margin-top: 20px;
	}
	
	
</style>
