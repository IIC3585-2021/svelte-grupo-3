<script>
	import { Router, Link, Route } from "svelte-navigator";
	import Home from "./routes/Home.svelte";
	import Favorite from "./routes/Favorite.svelte";
  import Swal from 'sweetalert2';
  import { isCatLover } from "./store.js";

/*   Swal.fire({
      title: 'Bienvenido! \nDinos que tipo de persona eres!',
      showDenyButton: true,
      showCancelButton: false,
      confirmButtonText: `CatLover`,
      denyButtonText: `DogLover`,
  }).then((result) => {
    if (result.isConfirmed) {
      Swal.fire('Bienvenido CatLover! \n Tenemos los mejores gatitos para ti!', '', 'success');
      isCatLover.set(1);
    } else if (result.isDenied) {
      Swal.fire('Bienvenido DogLover! \n Tenemos los mejores perritos para ti!', '', 'success');
      isCatLover.set(0);
    }
  }) */
</script>

<Router>
    
	<nav>
		<Link to="/">Home</Link>
		<Link to="favorites">Favoritos</Link>
	</nav>
	<main>
		<Route path="/">
			<Home />
		</Route>
		<Route path="favorites" component={Favorite} />
	</main>
</Router>