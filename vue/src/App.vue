<template>
	<div id="app">
		<router-link to="/insurance/about">about</router-link>
		<router-link to="/insurance/home">home</router-link>	
		<router-link to="/insurance/">index</router-link>	
		<router-view></router-view>
		
		<!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

		<div class="container">
			<div class="row">
				<div class="col">
					<button type="button" class="btn btn-secondary btn-type-all" data-type="data-all" @click="sort">
						<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-check-all" viewBox="0 0 16 16">
							<path d="M8.97 4.97a.75.75 0 0 1 1.07 1.05l-3.99 4.99a.75.75 0 0 1-1.08.02L2.324 8.384a.75.75 0 1 1 1.06-1.06l2.094 2.093L8.95 4.992a.252.252 0 0 1 .02-.022zm-.92 5.14.92.92a.75.75 0 0 0 1.079-.02l3.992-4.99a.75.75 0 1 0-1.091-1.028L9.477 9.417l-.485-.486-.943 1.179z"/>
						</svg>
						All View
					</button>
					<button type="button" class="btn btn-primary" data-type="data-a" @click="sort">Type-A</button>
					<button type="button" class="btn btn-success" data-type="data-b" @click="sort">Type-B</button>
					<button type="button" class="btn btn-danger" data-type="data-c" @click="sort">Type-C</button>
					<button type="button" class="btn btn-info" data-type="data-d" @click="sort">Type-D</button>

					<div class="mt-4">
						<ul class="item-list row p-0 g-2">
							<li class="data-a col-12 col-md-6">
								<b-card 
									title="Card Title"
									header="Primary"
									header-bg-variant="primary"
									header-text-variant="white"
									footer="footer1"
									footer-text-variant="primary"
								>
									<b-card-text>
										This is a wider card with supporting text below as a natural lead-in to additional content.
										This content is a little bit longer.
									</b-card-text>
									<template #header>
										<small class="">header</small>
									</template>
									<template #footer>
										<small class="">footer</small>
									</template>
								</b-card>
							</li>
							<li class="data-b col-4"><div>2B</div></li>
							<li class="data-a col-4"><div>3A</div></li>
							<li class="data-b col-4"><div>4B</div></li>
							<li class="data-b col-4"><div>5B</div></li>
							<li class="data-a col-4"><div>6A</div></li>
							<li class="data-c col-4"><div>7C</div></li>
							<li class="data-c col-4"><div>8C</div></li>
							<li class="data-a col-4"><div>9A</div></li>
							<li class="data-a col-4"><div>10A</div></li>
							<li class="data-c col-4"><div>11C</div></li>
							<li class="data-d col-4"><div>12D</div></li>
						</ul>
					</div>
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
// import HelloWorld from './components/HelloWorld.vue'
import item1 from './components/item1.vue'
import modal1 from './components/modal1.vue'

export default {
	name: 'App',
	components: {
		// HelloWorld,
		item1,
		modal1
	},
	methods: {
		sort(e) {
			let ele = e.target;
			let eleDataType = ele.getAttribute('data-type');
			let dataType = document.querySelectorAll('.' + ele.getAttribute('data-type'));

			let itemList = document.querySelector('.item-list');
			let dataAll = document.querySelectorAll('.item-list > li');

			if(!itemList.classList.contains('sort')) {
				itemList.classList.add('sort');
			}

			if(eleDataType === 'data-all') {
				itemList.classList.remove('sort');
			} else {
				dataAll.forEach(function(e) {
					e.classList.remove('active')
				})
				dataType.forEach(function(e) {
					e.classList.add('active')
				})
			}
		}
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

ul.item-list li {
	list-style: none;
}

ul.item-list.sort li {
	display:none;
}
ul.item-list.sort li.active {
	display:block;
}

.card-deck {
	display: flex;
    flex-flow: row wrap;
    margin-right: -15px;
    margin-left: -15px;
}
.card-deck .card {
	flex: 1 0 0%;
    margin-right: 15px;
    margin-bottom: 0;
    margin-left: 15px;
}
</style>