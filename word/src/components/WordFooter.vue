<template>
	<div class="clearAllContainer" @click="removeAll">
		<span class="clearAllBtn">Clear All</span>
	</div>
</template>

<script>
export default{
	methods: {
		removeAll(){
			this.$emit('removeAll');
		}
	}
}
</script>

<style>
.clearAllContainer{
	width:  8.5rem;
	height: 50px;
	line-height: 50px;
	background-color: white;
	border-radius: 5px;
	margin: 0 auto;
	cursor:pointer;
}
.clearAllBtn{
	color: #e20303;
	display: black;
}
</style>