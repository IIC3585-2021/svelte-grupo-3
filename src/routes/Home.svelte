<script>
	import AddFavorite from "../components/AddFavorite.svelte";
	import { isCatLover } from "../store.js";

	let isCatLoverValue;
	isCatLover.subscribe(value => {
		isCatLoverValue = value;
	});

	let data= {
		url: "", 
		emotion: ""
	};
	const getExcited = () => {
		const path = isCatLoverValue == 1 ? "https://api.thecatapi.com/v1/images/search?category_ids=4" : "https://api.thedogapi.com/v1/images/search?category_ids=4";
		const key = isCatLoverValue == 1 ? "297ece98-a6ac-419d-9d86-fbe4c3ccdeac" : "a372dd1f-6009-4104-a808-062d5637dca8";
		fetch("https://api.thedogapi.com/v1/images/search?category_ids=1", { headers: {"x-api-key" : key} })
    .then((response) => {
      return response.json()
    }).then((json) => {
			console.log(json)
      data = {
				url: json[0].url,
				emotion: "Emocionante"
			}
    });
	}
	const get_sad_cat = () => {
		fetch("https://api.thecatapi.com/v1/images/search?category_ids=2", 
        {headers: {"x-api-key" : key}})
        .then((response) => {
          return response.json()
        }).then((json) => {
			cat_data = {
				url: json[0].url,
				emotion: "Tristecillo"
			}
        });
	}
	const get_relax_cat = () => {
		fetch("https://api.thecatapi.com/v1/images/search?category_ids=1", 
        {headers: {"x-api-key" : key}})
        .then((response) => {
          return response.json()
        }).then((json) => {
			cat_data = {
				url: json[0].url,
				emotion: "Relajado"
			}
        });
	}
	const get_intense_cat = () => {
		fetch("https://api.thecatapi.com/v1/images/search?mime_types=gif", 
        {headers: {"x-api-key" : key}})
        .then((response) => {
          return response.json()
        }).then((json) => {
			cat_data = {
				url: json[0].url,
				emotion: "Intenso"
			}
        });
	}
</script>

<main>
	
	<div class="card">
		<img
		src={data.url}
		alt=""
	  	/>
		<AddFavorite cat_data = {data}/>
		<div class="card-title">¿Cómo estuvo tu día?</div>
		<div class="card-subtitle">
			Tenemos un gatito para ti
		</div>
		<div class="card-actions">
			<button on:click={getExcited}>
			 Emocionante 
			</button>
			<button on:click={get_sad_cat}>
			  Tristecillo
			</button>
			<button on:click={get_relax_cat}>
			  Relajado
			</button>
			<button on:click={get_intense_cat}>
			  Intenso
			</button>
		  </div>
	</div>
</main>
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	.card{
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
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

