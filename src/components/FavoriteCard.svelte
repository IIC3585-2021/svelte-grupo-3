<script>
	import DeleteFavorite from "../components/DeleteFavorite.svelte";
    export let favorite;
</script>

<div class="favorite-card">
	<div class="card-header">
		<div class="card-title">
			El día {favorite.date} tu día estaba 
			<p class="card-emotion" style={favorite.style}>{favorite.emotion}</p>
		</div>
		<DeleteFavorite data = {favorite}/>
	</div>

    <img
    src={favorite.url}
    alt=""
      />
</div>

<style>
	.favorite-card{
		margin: 10px auto;
        padding: 15px;
		max-width: 350px;
        box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.card-header {
        display: flex;
        justify-content: space-between;
    }
    .card-title {
        font-size: 22px;
		font-weight: 200;
        margin: 0 15px;
        text-align: left;
    }
	.card-emotion{
		margin: 10px 0;
		text-transform: uppercase;
	}
	img{
      	height: 250px;
		width: 90%;
		margin:auto;
		align-self: center;
		padding: 10;
	}

</style>