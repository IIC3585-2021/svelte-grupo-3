<script>
	import { Router, Link, Route } from "svelte-navigator";
	import Home from "./routes/Home.svelte";
	import Favorite from "./routes/Favorite.svelte";
  import Options from "./components/Options.svelte";
  import Swal from 'sweetalert2';
  import { isCatLover } from "./store.js";

  Swal.fire({
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
  })
</script>

<Router>
  <nav id="scanfcode" class="navbar">
    <div class="container-fluid">
      <div class="navbar-header">
        <p id="logo" class="navbar-brand">TuMood</p>
      </div>
      <div class="collapse navbar-collapse" id="myNavbar">
   
        <ul id="link" class="nav navbar-nav navbar-right">
           <li class="dropdown" id="first-link">
            <p><Link to="/">Home</Link></p>
          </li>
          <li class="dropdown" id="first-link">
            <p><Link to="favorites">Favoritos</Link></p>
          </li>
          <li class="dropdown" id="second-link">
            <p><Options /></p>
          </li>
        </ul>
      </div>
    </div>
  </nav>
	<main>
		<Route path="/">
			<Home />
		</Route>
		<Route path="favorites" component={Favorite} />
	</main>
</Router>

<style>
/* navigation bar */
#scanfcode
{
  border-radius:0px;
  background:rgb(191, 176, 206);
  padding:10px;
  font-size:17px;
}
/* logo or main heading */
#logo
{
  float: left;
  font-size:20px;
  padding-left: 20px;
  font-weight:bolder;
  color:#00004d;
  letter-spacing:2px;
}
/* navigation links*/
#link p
{
  color:#371169;
  margin:0 20px 0 10px;
  letter-spacing:1.5px;
}
/* navigation link with right border */
#first-link
{
  padding-right:6px;
  border-right:solid 1px #ccc;
}

#second-link
{
  padding-right:6px;
}

#myNavbar {
  width: 100%;
}

.container-fluid {
  width: 100%;
  text-justify: distribute;
  display:flex;
}

li{
  display:flex;
  text-decoration: none;
}

#link {
  display:flex;
  float:right;
}
</style>
