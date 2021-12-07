<template>
	<div id="app">
		<Header></Header>
		<div class="val">{{ val2 }}</div>
		<div class="itemTitle">{{ itemTitle }}</div>
		<main id="main">
			<div class="container">
				<router-view></router-view>
				<div class="row">
					<div class="col">
						<ItemList></ItemList>
					</div>
				</div>
			</div>
		</main>
		
		<child message="부모에서 자식으로 데이터 넘겨주기" @callParent="setTxt2"></child>
		<AsideNav @getItemTitle="setTxt"></AsideNav>
	</div>
</template>

<script>
import Header from './components/header.vue'
import AsideNav from './components/asideNav.vue'
import ItemList from './components/item-list.vue'
import child from './components/child.vue'

export default {
	name: 'App',
	components: {
		AsideNav,
		ItemList,
		child,
		Header
	},
	data:() => ({
		val: '',
		val2: '',
		aaa: 'aaa',
		itemTitle: 'All View'
	}),
	methods: {
		setTxt2(title2) {
			this.val2 = title2;
			console.log('자식에게 값을 받았어요' , this.val2)
		},
		setTxt(title) {
			this.itemTitle = title;
			console.log('자식에게 값을 받았어요' , this.itemTitle)
		},
		setChange2() {
			console.log(this.aaa)
			this.aaa = 'bbb'
			console.log(this.aaa)
		}
	}
}
</script>

<style>
body,
html {
	height:100%;
}
body {
	font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji", sans-serif;
}
#app {
	display:flex;
	flex-direction: column;
	min-height:100%;

	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #212731;
	background-color: #e8eaef;
}

#main {
	flex-grow: 1;
}
</style>