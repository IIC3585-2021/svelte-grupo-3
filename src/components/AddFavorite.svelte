<script>
    import { favorites } from "../store.js";
    export let disabled;
    export let data;
    // let date = `${actual_date.getDate()}/${actual_date.getMonth() + 1}/${actual_date.getTime()}`;
    const addToFavorite = () => {
        let new_cat_obj = {
            url: data.url,
            date: new Date(),
            emotion: data.emotion,
            style: data.style,
        }
        favorites.update(store => store = [...store, new_cat_obj]);
        disabled = true;
        
    }
</script>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<button disabled= {disabled} class="favBtn" id="Btn" on:click={addToFavorite}><i class="fa fa-heart"></i></button>
<style>
    .favBtn {
        border-radius: 50%;
        color:rgba(182, 34, 34, 0.87); 
        font-size: 20px;
        cursor: pointer;
    }
    .favBtn:hover{
        background-color: lightcoral;
        color: white;
        box-shadow: 0 14px 20px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
    }
    .favBtn:disabled{
        color: grey;
        pointer-events: none;
    }
</style>
  