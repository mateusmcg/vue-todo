<template>
	<div class="hello">
		<h1>{{ msg }}</h1>
		<h2>Essential Links</h2>
		<ul>
			<li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
			<li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
			<li><a href="https://gitter.im/vuejs/vue" target="_blank">Gitter Chat</a></li>
			<li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
			<br>
			<li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
		</ul>
		<h2>Ecosystem</h2>
		<ul>
			<li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
			<li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
			<li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
			<li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
		</ul>
    <h2>Elementos</h2>
		<button v-on:click="loadTodos">Me clique</button>
    <input type="text" v-model="inputTeste"/>
    <span>{{ inputTeste }}</span>
    <h2>Condições e Loops</h2>
    <input type="checkbox" v-model="visible">
    <span v-if="visible">Now you see me</span>
    <ul>
      <li v-for="todo in todos">
        <input type="checkbox" v-model="todo.completed">
        <span>{{todo.title}}</span>
        <input type="button" v-on:click="removeTodo(todo)" value="Remover todo.id">
      </li>
    </ul>
	</div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      inputTeste: '',
      visible: '',
      todos: []
    }
  },
  mounted: function(){
    this.loadTodos();
  },
  methods: {
    callAlert: callAlert,
    removeTodo: removeTodo,
    loadTodos: loadTodos
  }
}

function loadTodos() {
  // GET /someUrl
  this.$http.get('https://jsonplaceholder.typicode.com/todos').then((response) => {
    console.debug(response);
    this.todos = response.data;
  }, (response) => {
    console.error(response);
  });
}

function callAlert() {
  this.inputTeste = "Valor do model !";
}

function removeTodo(todo){
  console.debug(todo);
  this.todos.pop();
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h1,
	h2 {
		font-weight: normal;
	}
	
	ul {
		list-style-type: none;
		padding: 0;
	}
	
	li {
		margin: 0 10px;
	}
	
	a {
		color: #42b983;
	}
</style>