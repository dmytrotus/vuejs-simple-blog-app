<!-- sign up component -->

<template>

<div class="row my-5">
	<div class="col-md-6 offset-md-3">
		<div class="card">
			<div class="card-body">
				<h3 class="text-center my-4">Sign Up</h3>
				<div class="form-group">
					<input v-model="name" placeholder="name" type="text" class="form-control">
				</div>
				<div class="form-group">
					<input v-model="email" placeholder="e-mail" type="text" class="form-control">
				</div>
				<div class="form-group">
					<input v-model="password" placeholder="password" type="password" class="form-control">
				</div>
				<div class="form-group text-center">
					<button @click="registerUser()" class="btn btn-success form-control">Sign Up</button>
				</div>
			</div>
		</div>
	</div>
</div>

</template>

<script>

import Axios from 'axios';

	export default {
		data() {
			return {

				name: '',
				email: '',
				password: ''

			}
		},

		methods: {

			registerUser() {

				//console.log(this.name, this.email, this.password);
				Axios.post('https://react-blog-api.bahdcasts.com/api/auth/register', {
					name: this.name,
					email: this.email,
					password: this.password
				}).then( (response) => {

					//console.log(response)
					const {data } = response.data;

					localStorage.setItem('auth', JSON.stringify(data))

					this.$root.auth = data;

					this.$router.push('home');

				}).catch(error => {
					console.log(error);
				});
			}	
		}
	}
</script>