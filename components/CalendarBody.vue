<template>
	<div>
		<div class="calendar-date">
			<div>
				<label for v-for="field in fields" :key="field.key">{{field.label}}</label>
			</div>
			<div v-for="(date,index) in dates" :key="index">
				<calendar-date v-for="(d,index) in date" :key="index" :date="d.date" />
			</div>
		</div>
	</div>
</template>

<script>
import CalendarDate from "~/components/CalendarDate";
export default {
	props: ["year", "month"],
	components: {
		CalendarDate,
	},
	data() {
		return {
			fields: [
				{ label: "Sun", key: "sun" },
				{ label: "Mon", key: "mon" },
				{ label: "Tue", key: "tue" },
				{ label: "Wed", key: "wed" },
				{ label: "Thu", key: "thu" },
				{ label: "Fri", key: "fri" },
				{ label: "Sat", key: "sat" },
			],
			dates: [],
		};
	},
	mounted() {
		let currWeek = 0;
		let d = new Date(this.$props.year, this.$props.month - 1);
		let day = this.getDay(d);
		this.dates.push([]);
		for (let i = 0; i < day; i++) {
			this.dates[currWeek].push({ date: 0 });
		}
		while (d.getMonth() == this.$props.month - 1) {
			this.dates[currWeek].push({ date: d.getDate() });

			if (this.getDay(d) % 7 === 6) {
				this.dates.push([]);
				currWeek++;
			}
			d.setDate(d.getDate() + 1);
		}
		if (this.getDay(d) !== 0) {
			for (let i = this.getDay(d); i < 7; i++) {
				this.dates[currWeek].push({ date: 0 });
			}
		}
	},
	methods: {
		getDay(date) {
			let day = date.getDay();
			if (day == 0) day = 7;
			return day - 1;
		},
	},
};
</script>

<style lang="scss">
.calendar-date {
	display: grid;
	> div {
		display: grid;
		grid-template-columns: repeat(7, calc(100% / 7));
		place-items: center;
		> label {
			font-weight: bolder;
		}
	}
}
</style>