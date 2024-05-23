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

<div class="container text-center mt-5">
	<h1 class="mb-4">How much is your house worth?</h1>
  
	<div class="row justify-content-center">
	  <div class="col-12 col-md-2 mb-3">
		<input type="number" class="form-control" placeholder="Lot Size" aria-label="lotSize" bind:value={lotSize}>
	  </div>
	  <div class="col-12 col-md-2 mb-3">
		<input type="number" class="form-control" placeholder="Living Space" aria-label="livingSpace" bind:value={livingSpace}>
	  </div>
	  <div class="col-12 col-md-2 mb-3">
		<input type="number" class="form-control" placeholder="Rooms" aria-label="rooms" bind:value={rooms}>
	  </div>
	  <div class="col-12 col-md-2 mb-3">
		<input type="number" class="form-control" placeholder="Year" aria-label="year" bind:value={year}>
	  </div>
	  <div class="col-12 col-md-2 mb-3">
		<input type="number" class="form-control" placeholder="PLZ" aria-label="plz" bind:value={plz}>
	  </div>
  
	  <div class="col-12 text-center">
		<button type="button" class="btn btn-primary" on:click={handleSubmit}>Price Estimation</button>
	  </div>

	  <div class="col-12 mt-3">
		<h2> Our model predicts this price: {price}</h2>
		</div>
	</div>
  </div>