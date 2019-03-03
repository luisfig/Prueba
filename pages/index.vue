<template lang="html">
	<div class="section section2">
		<div class="container">
			<h1 class="title">Álbumns de la página</h1>
			<div class="columns is-multiline ">
				<AlbumCard :album="album" v-for="album in albums" :key="album.id"/>
			</div>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	import env from '../config/env';
	import AlbumCard from '../components/AlbumCard';
	export default{
		name: 'IndexPage',
		components:{
			AlbumCard
		},
		data(){
			return{
				albums: []
			}
		},
		created(){
			axios.get(`${env.endpoint}/albums`).then(response=>{
				this.albums = response.data;
			})
		}
	}
</script>

<style lang="css">
	/*page-enter-active, .page-leave-active {
      transition: all .30s ease-out;
    }
    .page-enter, .page-leave-active {
      opacity: 0;
      transform-origin: 50% 50%;
    }*/
</style>