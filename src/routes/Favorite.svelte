<script>
    import FavoriteCard from "../components/FavoriteCard.svelte";
    import { favorites } from "../store.js";
    let favorite_cats;
    favorites.subscribe(value => {
		favorite_cats = value;
	});
</script>

<div class="favorite">
    <h1>Tus favoritos de hoy</h1>
    {#each favorite_cats as favoriteCat}
        <FavoriteCard favorite = {favoriteCat}/>
    {/each}
</div>
<style>
</style>
  