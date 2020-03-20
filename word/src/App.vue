<template>
	<div id="app">
		<WordHeader></WordHeader>
		<WordInput v-on:addWord="addWord"></WordInput>
		<WordList v-bind:propsdata="wordItems" @removeWord="removeWord"></WordList>
		<WordFooter v-on:removeAll="clearAll"></WordFooter>
	</div>
</template>

<script>
import WordHeader from './components/WordHeader.vue' 
import WordInput from './components/WordInput.vue' 
import WordList from './components/WordList.vue' 
import WordFooter from './components/WordFooter.vue' 

export default{
	data(){
		return {
			wordItems: []
		}	
	},
	components:{
		'WordHeader' : WordHeader,
		'WordInput' : WordInput,
		'WordList' : WordList,
		'WordFooter' : WordFooter
	},
	created(){
		if(localStorage.length >0){
			for(var i=0; i<localStorage.length; i++){
				this.wordItems.push(localStorage.key(i));
			}
		}
	},
	methods:{
		addWord(wordItem){
			if(this.wordItem !== ""){
				localStorage.setItem(wordItem,wordItem);
				this.wordItems.push(wordItem);
			}
		},
		removeWord(wordItem, index){
			localStorage.removeItem(wordItem);
			this.wordItems.splice(index,1);
		},
		clearAll(){
			localStorage.clear();
			this.wordItems = [];
		}
	}
}
</script>

<style>
body{
	text-align: center;
	background-color: #F6F6F6;
}
input{
	border-style: groove;
	width: 200px;
}
button{
	border-style: groove;
}
.shadow{
	box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
}
</style>