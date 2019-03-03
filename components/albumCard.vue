<template lang="html">
	<div class="box column is-one-quarter is-primary">
		<h3 class="subtitle">{{album.title}}</h3>
		<nuxt-link :to="`/albums/${album.id}`" class="button is-primary">Ver álbum</nuxt-link>
	</div>
</template>

<script>
	export default{
		name:'AlbumCard',
		props:{
			album:Object
		}
	}
</script>

<style lang="css">
	h3{
		min-height: 5em;
	}
</style>