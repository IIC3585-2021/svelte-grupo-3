<script>
    import FavoriteCard from "../components/FavoriteCard.svelte";
    import { favorites } from "../store.js";
    let favorite_cats;
    favorites.subscribe(value => {
		favorite_cats = value;
	});
</script>

<div class="favorite">
    <h1>Tus favoritos</h1>
    <div class= "favPanel">
        {#each favorite_cats as favoriteCat}
        <FavoriteCard favorite = {favoriteCat}/>
    {/each}
    </div>

</div>
<style>
h1{
    width: 100%;
    font-size:20px;
    text-align: center;
}
.favPanel{
    display: flex;
    flex-wrap: wrap;
}
</style>
  