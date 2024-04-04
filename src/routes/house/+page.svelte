<script>
    import { PUBLIC_BASE_URL } from '$env/static/public';
 	import axios from "axios";


	let rooms;
	let lotSize;
	let livingSpace;
	let year;
	let plz;
	let price = '...'
	function handleSubmit() {
		let url =
            PUBLIC_BASE_URL +
            "/api/prediction/house?plz=" +
            plz +
            "&lotsize=" +
            lotSize +
            "&livingspace=" +
            livingSpace +
			"&rooms=" +
            rooms +
			"&year=" +
            year;
        console.log(url);
        axios.get(url).then((response) => {
            price = 'CHF ' + response.data;
        });
	}
</script>
<div class="container text-center">

	<h1>How much is your house worth? Our model predicts this price: {price}</h1>

	<div class="row justify-content-md-center">
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="Lot Size" aria-label="lotSize" bind:value={lotSize}>
	  </div>
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="Living Space" aria-label="livingSpace" bind:value={livingSpace}>
	  </div>
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="rooms" aria-label="rooms" bind:value={rooms}>
	  </div>
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="year" aria-label="year" bind:value={year}>
	  </div>
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="plz" aria-label="plz" bind:value={plz}>
	  </div>

	  <div class="col-md-auto">
		<button type="button" class="btn btn-primary" on:click={handleSubmit}>price estimation</button>
	  </div>
	</div>
  </div>