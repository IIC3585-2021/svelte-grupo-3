<script>
	import AddFavorite from "../components/AddFavorite.svelte";
	import { isCatLover } from "../store.js";

	let disabledFavorite = true;
	let isCatLoverValue;
	let animal;
    isCatLover.subscribe(value => {
        isCatLoverValue = value;
        animal = isCatLoverValue == 1 ? "gatito" : "perrito";
    });

	let data = {url: "https://images.ctfassets.net/cnu0m8re1exe/7sLmeD1tcL4UoIm0BjNaLh/22a9f42a4315361db96470f50b178e86/Dog-and-Cat.jpg"};
	const getExcited = () => {
		const path = isCatLoverValue == 1 ? "https://api.thecatapi.com/v1/images/search?category_ids=4" : "https://random.dog/woof.json";
		const params = isCatLoverValue == 1 ? { headers: {"x-api-key" : "297ece98-a6ac-419d-9d86-fbe4c3ccdeac"} } : {};
		fetch(path, params)
    	.then((response) => {
      		return response.json()
    	}).then((json) => {
			if (isCatLoverValue == 0) {
				if (json.url.includes(".mp4")){
					getExcited();
					return;
				}
			} 
			data = {
				url: isCatLoverValue == 1 ? json[0].url : json.url,
				emotion: "Emocionante",
				style: "color: orange"
			}
			disabledFavorite = false;
    	});
	}
	const getSad = () => {
		const path = isCatLoverValue == 1 ? "https://api.thecatapi.com/v1/images/search?category_ids=2" : "https://random.dog/woof.json";
		const params = isCatLoverValue == 1 ? { headers: {"x-api-key" : "297ece98-a6ac-419d-9d86-fbe4c3ccdeac"} } : {};
		fetch(path, params)
        .then((response) => {
          return response.json()
        }).then((json) => {
			if (isCatLoverValue == 0) {
				if (json.url.includes(".mp4")){
					getSad();
					return;
				}
			} 
			data = {
				url: isCatLoverValue == 1 ? json[0].url : json.url,
				emotion: "Tristecillo",
				style: "color: blue"
			}
			disabledFavorite = false;
        });
	}
	const getRelax = () => {
		const path = isCatLoverValue == 1 ? "https://api.thecatapi.com/v1/images/search?category_ids=1" : "https://random.dog/woof.json";
		const params = isCatLoverValue == 1 ? { headers: {"x-api-key" : "297ece98-a6ac-419d-9d86-fbe4c3ccdeac"} } : {};
		fetch(path, params)
        .then((response) => {
          return response.json()
        }).then((json) => {
			if (isCatLoverValue == 0) {
				if (json.url.includes(".mp4")){
					getRelax();
					return;
				}
			} 
			data = {
				url: isCatLoverValue == 1 ? json[0].url : json.url,
				emotion: "Relajado",
				style: "color: purple"
			}
			disabledFavorite = false;
        });
	}
	const getIntense = () => {
		const path = isCatLoverValue == 1 ? "https://api.thecatapi.com/v1/images/search?mime_types=gif" : "https://random.dog/woof.json";
		const params = isCatLoverValue == 1 ? { headers: {"x-api-key" : "297ece98-a6ac-419d-9d86-fbe4c3ccdeac"} } : {};
		fetch(path, params)
        .then((response) => {
          return response.json()
        }).then((json) => {
			if (isCatLoverValue == 0) {
				if (json.url.includes(".mp4")){
					getIntense();
					return;
				}
			} 
			data = {
				url: isCatLoverValue == 1 ? json[0].url : json.url,
				emotion: "Intenso",
				style: "color: red"
			}
			disabledFavorite = false;
        });
	}
</script>

<main>
	<div class="card">
		<img
		src={data.url}
		alt=""
	  	/>
        <div class="card-header">
            <div class="card-title">¿Cómo estuvo tu día?</div>
            <AddFavorite data = {data} bind:disabled = { disabledFavorite }/>
        </div>
		<p class="card-subtitle">
			Tenemos un {animal} para ti
        </p>
		<div class="card-actions">
			<button on:click={getExcited} style={"color: orange"}>
			 Emocionante 
			</button>
			<button on:click={getSad} style={"color: blue"}>
			  Tristecillo
			</button>
			<button on:click={getRelax} style={"color: purple"}>
			  Relajado
			</button>
			<button on:click={getIntense} style={"color: red"}>
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
        padding: 15px;
		max-width: 500px;
        box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
	}
    .card-header {
        display: flex;
        padding: 10px;
        justify-content: space-between;
    }
	.card-title {
		font-size: 30px;
		font-weight: 200;
	}
    .card-subtitle {
        font-size: 22px;
		font-weight: 200;
        margin: 0 15px;
        text-align: left;
    }
    .card-actions {
        display: flex;
        justify-content: space-around;
        align-items: flex-end;
        margin-top: 10px;
    }
	button{
		text-transform: uppercase;
        font-weight: 300;
        border: none;
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

