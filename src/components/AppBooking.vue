<template>
	<div class="home">
		<app-toolbar></app-toolbar>
		<v-container>
			<h1>Booking information</h1>
			<v-alert
			type="success" v-if="message !=''">{{message}}
		</v-alert>
		<v-alert
		type="error" v-if="error !=''">{{error}}
	</v-alert>

	<v-card class="pa-5">
		<v-text-field
		label="name"
		v-model="name"
		></v-text-field>
		<v-row>
			<v-col cols="6">
				<v-text-field
				type="email"
				label="Email"
				v-model="email"
				></v-text-field>
			</v-col>
			<v-col cols="6">
				<v-text-field
				type="phone"
				label="Phone number"
				v-model="phone"
				></v-text-field>
			</v-col>
			<v-col cols="6">
				<v-text-field
				type="date"
				label="Waktu Ambil"
				v-model="senddate"
				></v-text-field>
			</v-col>
			<v-col cols="6">
				<v-text-field
				type="date"
				label="Waktu Hantar"
				v-model="returndate"
				></v-text-field>
			</v-col>
			<v-select
			:items="items"
			label="Lokasi ambil"
			v-model="sendplace"
			></v-select>
			<v-select
			:items="items"
			label="hantar"
			v-model="returnplace"
			></v-select>
		</v-row>
		<v-btn block color="primary" v-on:click="buttonPress" :loading="loading">Book my car</v-btn>
	</v-card>
</v-container>

<app-footer></app-footer>	
</div>
</template>

<script>
// @ is an alias to /src
import AppFooter from './AppFooter.vue';
import AppToolbar from './AppToolbar.vue';

export default {
	name: 'AppBooking',
	components: {AppFooter, AppToolbar},
	



data(){
	return {
		items:["Putrajaya", "Cyberjaya", "Bangi", "kajang" , "Puchong"],
		name:'',
		email:'',
		phone:'',
		senddate:'',
		returndate:'',
		sendplace:'',
		returnplace:'',
		message:'',
		loading:false,
		jeniskereta:this.$route.params.carname

	}
},

methods: {
	buttonPress:function(){
		console.log('ok')
		console.log(this.email)
		console.log(this.phone)
		console.log(this.sendate)
		console.log(this.returndate)
		console.log(this.sendplace)
		console.log(this.returnplace)

		let url = 'https://api.sheety.co/f6cfa922b1b5419cd79a1bacd94fb436/untitledSpreadsheet/sheet1';
		let body = {
			sheet1: {
				"name":this.name,
				"email":this.email,
				"phone":this.phone,
				"senddate":this.senddate,
				"returndate":this.returndate,
				"sendplace":this.sendplace,
				"returnplace":this.returnplace,
				"jeniskereta":this.jeniskereta
			}
		}
		this.loading = true;
		fetch(url, {
			headers:{'Content-Type': 'application/json'},
			method: 'POST',
			body: JSON.stringify(body)
		})
		.then((response) => response.json())
		.then(json => {

			if (json.sheet1){
				this.message="Succesfully booked. We will contact you"
			}
			else{
				this.error= "Something is wrong, please try again"
			}
		});
	}
}
}
</script>