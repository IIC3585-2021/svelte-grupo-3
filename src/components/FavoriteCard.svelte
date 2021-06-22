<script>
	import DeleteFavorite from "../components/DeleteFavorite.svelte";
    export let favorite;
</script>

<div class="favorite-card">
	<div class="card-body">
	<div class="card-header">
		<div class="card-title">
			El {favorite.date.getDate()  + "-" + (favorite.date.getMonth()+1) + "-" + favorite.date.getFullYear() + 
			" a las "+ favorite.date.getHours() + ":" + favorite.date.getMinutes()} tu día estaba 
			<p class="card-emotion" style={favorite.style}>{favorite.emotion}</p>
		</div>
		<DeleteFavorite data = {favorite}/>
	</div>

	<div class="card-image">
    <img
    src={favorite.url}
    alt=""
      />
	</div>
	</div>
</div>

<style>
	.card-body{
		align-content: center;
	}
	.favorite-card{
		margin: 10px auto;
        padding: 15px;
		max-width: 350px;
        box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
	}
	.card-header {
        display: flex;
        justify-content: space-between;
    }
    .card-title {
        font-size: 18px;
		font-weight: 200;
        margin: 0 15px;
        text-align: left;
    }
	.card-emotion{
		margin: 10px 0;
		text-transform: uppercase;
	}
	.card-image{
		width: 100%;
		align-items: center;
	}
	img{
      max-height: 250px;
		  max-width: 350px;
		  display: block;
  		margin-left: auto;
  		margin-right: auto;
	}

</style>