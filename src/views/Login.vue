<!-- login component -->

<template>

<div class="row my-5">
	<div class="col-md-6 offset-md-3">
		<div class="card">
			<div class="card-body">
				<h3 class="text-center my-4">login</h3>
				<div class="form-group">
					<input v-model="email" placeholder="e-mail" type="text" class="form-control">
				</div>
				<div class="form-group">
					<input v-model="password" placeholder="password" type="text" class="form-control">
				</div>
				<div class="form-group text-center">
					<button @click="loginUser" class="btn btn-success form-control">login</button>
				</div>
			</div>
		</div>
	</div>
</div>

</template>

<script>

import Axios from 'axios'

export default {

	data() {

		return{
			email: "",
			password: ""
		};
	},

	methods: {
		loginUser() {
			console.log(this.email, this.password);
			/*axios.post('http://laraveltestproject/api/vuejsap/login', {
				email: this.email,
				password: this.password,
			}).then((response)) => {
				console.log(response)
			}*/
		}
	}
}

</script>