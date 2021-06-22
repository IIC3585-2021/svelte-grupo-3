<script>
    import { favorites } from "../store.js";
    export let cat_data;
    //let date = `${actual_date.getDate()}/${actual_date.getMonth() + 1}/${actual_date.getTime()}`;
    const addToFavorite = () => {
        let new_cat_obj = {
            url: cat_data.url,
            date: new Date(),
            emotion: cat_data.emotion
        }
        favorites.update(store => store = [...store, new_cat_obj]);
    }
</script>

<button class="fav_btn" on:click={addToFavorite}>Fav</button>
<style>
</style>
  