<template>
	<div class="inputBox shadow">
		<input type="text" v-model="newWordItem" v-on:keyup.enter="addWord" placeholder="단어를 입력하세요.">
		<span class="addContainer" v-on:click="addWord">
			<i class="addBtn fas fa-plus" aria-hidden="true"></i>
		</span>
	</div>
</template>

<script>
export default{
	data(){
		return {
			newWordItem: ''
		}
	},
	methods:{
		addWord(){
			if(this.newWordItem !== ''){
				var value = this.newWordItem && this.newWordItem.trim();
				//localStorage.setItem(value,value);
				this.$emit('addWord',value);
				this.clearInput();	
			}
		},
		clearInput(){
			this.newWordItem = '';
		}
	}
}
</script>

<style>
input:focus{
	outline: none;
}
.inputBox{
	background: white;
	height: 50px;
	line-height: 50px;
	border-radius: 5px;
}
.inputBox input{
	border-style: none;
	font-size: 0.9rem;
}
.addContainer{
	float: right;
	background: linear-gradient(to right, #6478FB, #8763FB);
	display: block;
	width: 3rem;
	border-radius: 0 5px 5px 0;
}
.addBtn{
	color: white;
	vertical-align: middle;
	cursor:pointer;
}
</style>