<template lang="html">
	<div class="section section2">
		<div class="section container">
			<h1 class="title">{{album.title}}</h1>
		</div>
		<div class="section container">
			<nuxt-link to="/">Regresar</nuxt-link>
		</div>
		<div class="section">
			<div class="columns is-multiline">
				<div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
					<img src="photo.url" :alt="photo.title">
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import router from 'vue-router';
	import axios from 'axios';
	import env from '../../config/env';
	export default{
		name: 'AlbumIndvPage',
		data(){
			return{
				album:{},
				photos:[]
			}
		},
		created: async function(){
		//created(){
			//Titulo de la foto
			let albumResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`);
			this.album = albumResponse.data;
			/*axios.get(`${env.endpoint}/albums/${this.$route.params.id}`)
				.then(albumResponse=>{
					this.album = albumResponse.data;
			});]*/
			//Foto
			let photosResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`);
			this.photos = photosResponse.data;
			/*axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
				.then(photosResponse=>{
					this.photos = photosResponse.data;
			});*/
		}
	}	
</script>

<style lang="css">

</style>