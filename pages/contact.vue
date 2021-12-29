<template>
	<v-container fill-height fluid grid-list-xl>
		<v-row justify="center">
			<v-col cols="12">
				<div class="my-2">
					<v-btn color="primary" dark :to="`/add-contact`">Add Contact</v-btn>
				</div>
			</v-col>
		</v-row>
		<v-row justify="center">
			<v-col cols="12">
				<v-card>
					<div class="v-data-table v-data-table--has-bottom theme--light">
						<div class="v-data-table__wrapper">
							<table class="table">
								<thead class="v-data-table-header">
									<tr>
										<th scope="col">ID</th>
										<th scope="col">salutation</th>
										<th scope="col">first_name</th>
										<th scope="col">last_name</th>
										<th scope="col">gender</th>
										<th scope="col">date_of_birth</th>
										<th scope="col">nationality</th>
										<th scope="col">mobile_phone</th>
										<th scope="col">email</th>
										<th scope="col">identity_card_number</th>
										<th scope="col">address</th>
									</tr>
								</thead>
								<tbody>
									<tr v-for="contact in contacts" :key="contact.id">
										<td class="text-start">{{ contact.id }}</td>
										<td class="text-start">{{ contact.salutation }}</td>
										<td class="text-start">{{ contact.first_name }}</td>
										<td class="text-start">{{ contact.last_name }}</td>
										<td class="text-start">{{ contact.gender }}</td>
										<td class="text-start">{{ contact.date_of_birth }}</td>
										<td class="text-start">{{ contact.nationality }}</td>
										<td class="text-start">{{ contact.mobile_phone }}</td>
										<td class="text-start">{{ contact.email }}</td>
										<td class="text-start">{{ contact.identity_card_number }}</td>
										<td class="text-start">{{ contact.address }}</td>
									</tr>
								</tbody>
							</table>
						</div>
					</div>
				</v-card>
			</v-col>
		</v-row>
	</v-container>
</template>

<script>
import axios from 'axios';
export default {
	data() {
		return {
			search: '',
			headers: [
				{
					text: 'Dessert (100g serving)',
					align: 'start',
					filterable: false,
					value: 'name',
				},
				{ text: 'Calories', value: 'calories' },
				{ text: 'Fat (g)', value: 'fat' },
				{ text: 'Carbs (g)', value: 'carbs' },
				{ text: 'Protein (g)', value: 'protein' },
				{ text: 'Iron (%)', value: 'iron' },
			],
			desserts: [
				{
					name: 'Frozen Yogurt',
					calories: 159,
					fat: 6.0,
					carbs: 24,
					protein: 4.0,
					iron: '1%',
				},
				{
					name: 'Ice cream sandwich',
					calories: 237,
					fat: 9.0,
					carbs: 37,
					protein: 4.3,
					iron: '1%',
				},
				{
					name: 'Eclair',
					calories: 262,
					fat: 16.0,
					carbs: 23,
					protein: 6.0,
					iron: '7%',
				},
				{
					name: 'Cupcake',
					calories: 305,
					fat: 3.7,
					carbs: 67,
					protein: 4.3,
					iron: '8%',
				},
				{
					name: 'Gingerbread',
					calories: 356,
					fat: 16.0,
					carbs: 49,
					protein: 3.9,
					iron: '16%',
				},
				{
					name: 'Jelly bean',
					calories: 375,
					fat: 0.0,
					carbs: 94,
					protein: 0.0,
					iron: '0%',
				},
				{
					name: 'Lollipop',
					calories: 392,
					fat: 0.2,
					carbs: 98,
					protein: 0,
					iron: '2%',
				},
				{
					name: 'Honeycomb',
					calories: 408,
					fat: 3.2,
					carbs: 87,
					protein: 6.5,
					iron: '45%',
				},
				{
					name: 'Donut',
					calories: 452,
					fat: 25.0,
					carbs: 51,
					protein: 4.9,
					iron: '22%',
				},
				{
					name: 'KitKat',
					calories: 518,
					fat: 26.0,
					carbs: 65,
					protein: 7,
					iron: '6%',
				},
			],
		};
	},
	async asyncData() {
		const contacts = await axios
			.get('http://127.0.0.1:8000/contact')
			.then((res) => res.data)
			.catch((err) => console.log(err));
		return {
			contacts,
		};
	},
};
</script>
