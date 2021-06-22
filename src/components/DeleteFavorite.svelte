<script>
    import { favorites } from "../store.js";
    export let data;
    // let date = `${actual_date.getDate()}/${actual_date.getMonth() + 1}/${actual_date.getTime()}`;
    const deleteFavorite = () => {
        let index = null;
        let auxStore;
        favorites.subscribe( value => {
            auxStore = value;
        });
        auxStore.forEach((elem) => {
            if (elem === data) {
                index = auxStore.indexOf(elem);
            }
        });
        auxStore.splice(index, 1);
        favorites.update(store => store = auxStore);       
    }
</script>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<button class="delBtn" on:click={deleteFavorite}><i class="fa fa-trash"></i></button>
<style>
    .delBtn {
        border-radius: 50%;
        height: 40px;
        color:blue; 
        font-size: 20px;
        cursor: pointer;
    }
    .delBtn:hover{
        background-color: rgba(173, 200, 230, 0.822);
        color: black;
        box-shadow: 0 14px 20px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
    }
</style>
  