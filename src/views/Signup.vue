<!-- sign up component -->

<template>

<div class="row my-5">
	<div class="col-md-6 offset-md-3">
		<div class="card">
			<div class="card-body">
				<h3 class="text-center my-4">Sign Up</h3>
				<div class="form-group">
					<input v-model="name" placeholder="name" type="text" class="form-control">
					<div class="errors" v-if="errors.name">
						<small class="text-danger" :key="error" v-for="error in errors.name">
							{{ error }}
						</small>
					</div>
				</div>
				<div class="form-group">
					<input v-model="email" placeholder="e-mail" type="text" class="form-control">
					<div class="errors" v-if="errors.email">
						<small class="text-danger" :key="error" v-for="error in errors.email">
							{{ error }}
						</small>
					</div>
				</div>
				<div class="form-group">
					<input v-model="password" placeholder="password" type="password" class="form-control">
					<div class="errors" v-if="errors.password">
						<small class="text-danger" :key="error" v-for="error in errors.password">
							{{ error }}
						</small>
					</div>
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
				password: '',
				errors: {}

			}
		},

		methods: {

			registerUser() {

				//console.log(this.name, this.email, this.password);
				Axios.post('http://laraveltestproject/api/vuejsapi', {
					name: this.name,
					email: this.email,
					password: this.password
				}).then( (response) => {


					localStorage.setItem('auth', JSON.stringify(response.data));

					this.$root.auth = response.data;

					this.$router.push('home');

					//console.log(response);
					//const {data } = response.data;

					//localStorage.setItem('auth', JSON.stringify(data))

					//this.$root.auth = data;

					

				}).then(response => {
					//console.log(response);
				}).catch( ({response})  => {
					//console.log(error);
				})


				/*.catch( ({response})  => {
					//console.log(error);

					this.errors = response.data;
				});*/
			}	
		}
	}
</script>