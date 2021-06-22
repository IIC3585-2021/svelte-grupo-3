<script>
    export let favorite;

</script>

<div class="favorite-card">
    <div class="card-title">
        El día {favorite.date} tu día estaba {favorite.emotion}
    </div>
    <img
    src={favorite.url}
    alt=""
      />
</div>

<style>
	.favorite-card{
		margin: auto;
		border: solid;
		max-width: 500px;
	}
	.card-title {
		font-size: 30px;
		font-weight: 100;
	}
	button{
		text-transform: uppercase;
	}
	img{
      	height: 300px;
		width: 90%;
		margin:auto;
		align-self: center;
		padding: 10;
	}
</style>