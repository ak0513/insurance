<template>
	<div id="app">
		<router-link to="/insurance/about">about</router-link>	
		<router-link to="/insurance/home">home</router-link>	
		<router-view></router-view>
		<router-link to="/insurance/"><img alt="Vue logo" src="./assets/logo.png"></router-link>	
		<HelloWorld msg="Welcome to Your Vue.js App"/>
		<div class="container">
			<div class="row">
				<div class="col-6">
					<b-card
						title="Card Title"
						img-src="https://picsum.photos/600/300/?image=25"
						img-alt="Image"
						img-bottom
						tag="article"
						class="mb-2"
					>
						<b-card-text>111</b-card-text>

						<b-button href="#" variant="primary">Go somewhere111</b-button>
					</b-card>
				</div>
			</div>
		</div>

		<div id="item1">
			<item1 msg="item1" />
		</div>
		

		<b-button v-b-modal.modal-1>Launch demo modal</b-button>
		<modal1/>
	</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import item1 from './components/item1.vue'
import modal1 from './components/modal1.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    item1,
    modal1
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
