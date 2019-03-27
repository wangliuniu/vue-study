<template>
	
		<div class="container">
			<h2>消息</h2>
			 {{msg}}
		
	</div>
</template>

<script>
	
	export default{
		 name:'Index',
		 data(){
			 return{
				 msg:'这是消息'
			 };
		 }
	};
</script>

<style scaoped>
</style>
