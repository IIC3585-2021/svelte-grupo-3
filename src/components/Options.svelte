<script>
  import Swal from 'sweetalert2';
  import { isCatLover } from "../store.js";

  const changeTypeOfPerson = () => {
    Swal.fire({
        title: 'Dinos que tipo de persona eres!',
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
    }
</script>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<button class="configBtn" on:click={changeTypeOfPerson}><i class="fa fa-cog"></i></button>

<style>
.configBtn {
    border: none;
    color:blue; 
    background-color: transparent;
    font-size: 20px;
    cursor: pointer;
}
</style>
