<template>
	<div class="home">
		<app-toolbar></app-toolbar>
		<v-carousel>
			<v-carousel-item
			v-for="(item,i) in items"
			:key="i"
			:src="item.src"
			reverse-transition="fade-transition"
			transition="fade-transition"
			></v-carousel-item>
		</v-carousel>
		<section id="cars" class="text-center">
			<v-container>
				<h3>Book a car now</h3>
				<v-row>
					<v-col cols="4"
					v-for="car in cars"
					:key="car.name"
					>
					<v-card>
						<v-img
						height="250"
						v-bind:src="car.imageurl"
						></v-img>
						<v-card-title>{{car.name}}</v-card-title>

						<v-card-text>
							<v-row
							align="center"
							class="mx-0"
							>
							<v-rating
							:value="4.5"
							color="amber"
							dense
							half-increments
							readonly
							size="14"
							></v-rating>

							<div class="grey--text ml-4">
								4.5 (413)
							</div>
						</v-row>

						<div class="my-4 subtitle-1">
							RM {{car.price}}
						</div>

						<div>{{car.description}}</div>
					</v-card-text>
					<v-divider>
					</v-divider>
					<v-card-actions>
						<v-btn
						color="deep-purple lighten-2"
						text
						v-on:click="reserve(car.name)"

						>
						Reserve
					</v-btn>
				</v-card-actions>
			</v-card>
		</v-col>

	</v-row>
</v-container>
</section>
<app-footer></app-footer>
</div>
</template>

<script>
// Step 1 : Import AppFooter and AppToolbar
import AppFooter from './AppFooter.vue';
import AppToolbar from './AppToolbar.vue';
export default {
	name: 'Apphome',
	components: {AppFooter , AppToolbar},
	methods: {
		reserve:function(name){
			this.$router.push('/booking/'+name)
		}
	},
		data () {
			return {
				cars: [
				{
					name:"Perodua Alza",
					location:"Bandar Baru Bangi",
					description:"Perodua Alza sesuai untuk 4 orang",
					price:"80 per day",
					rating:4,
					imageurl:"https://da4dkroembtou.cloudfront.net/wp-content/uploads/2019/03/Perodua-Alza-SE-1.5-01-Medium.jpg"
				},
				{
					name:"Perodua Viva",
					location:"Kajang",
					description:"Perodua Viva Putih sesuai untuk 4 orang",
					price:"80 per day",
					rating:3.5,
					imageurl:"https://upload.wikimedia.org/wikipedia/commons/4/43/Perodua_Viva_in_Malacca_%28cropped%29.JPG"
				},
				{
					name:"Proton Saga",
					location:"Bandar Baru Bangi",
					description:"Proton Saga edisi baru sesuai untuk 4 orang",
					price:"80 per day",
					rating:4,
					imageurl:"https://assets.bharian.com.my/images/articles/WhatsApp_Image_2020-07-09_at_11.49.03_AM_1594266775.jpg"
				},
				{
					name:"Preve",
					location:"Semenyih",
					description:"Preve sesuai untuk 5 orang",
					price:"80 per day",
					rating:4,
					imageurl:"https://s3.paultan.org/image/2018/04/Proton-Preve-Refinement-2018_Ext-1.jpg"
				}],
				items: [
				{
					src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
				},
				{
					src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
				},
				{
					src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
				},
				{
					src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
				},
				],

			}
		}
	}
	</script>