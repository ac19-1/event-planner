<template>
	<div>
		<div class="calendar-date">
			<div>
				<label for v-for="field in fields" :key="field.key">{{field.label}}</label>
			</div>
			<div v-for="(date,i) in dates" :key="i">
				<calendar-date v-for="(d,idx) in date" :selected="selections[i][idx]" :key="idx" :date="d.date" @dateChanged="dateChange"/>
			</div>
		</div>
	</div>
</template>

<script>
import CalendarDate from "~/components/CalendarDate";
export default {
	props: ["selected","year", "month"],
	components: {
		CalendarDate,
	},
	watch: {
		year: function (newVal, oldVal) {
			this.setCalendarBody()
		},
		month: function (newVal, oldVal) {
			this.setCalendarBody()
		},
		selected: function(newVal, oldVal) {
			this.setCalendarBody()
		}
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
			selections: []
		};
	},
	mounted() {
		this.setCalendarBody()
	},
	methods: {
		getDay(date) {
			let day = date.getDay();
			if (day == 0) day = 7;
			return day;
		},
		setCalendarBody() {
			console.log('ehheh')
			this.dates = []
			this.selections = []
			let currWeek = 0;
			let d = new Date(this.$props.year, this.$props.month - 1);
			let day = this.getDay(d);
			this.dates.push([]);
			this.selections.push([]);
			if(day != 7) {
				for (let i = 0; i < day; i++) {
					this.dates[currWeek].push({ date: '' });
					this.selections[currWeek].push(false);
				}
			}
			while (d.getMonth() == this.$props.month - 1) {
				this.dates[currWeek].push({ date: d.getDate() });
				
				if (d.getDate() == this.$props.selected ){
					this.selections[currWeek].push(true);
				}
				else {
					this.selections[currWeek].push(false);
				}

				if (this.getDay(d) % 7 === 6) {
					this.dates.push([]);
					this.selections.push([])
					currWeek++;
				}
				d.setDate(d.getDate() + 1);
			}
			if (this.getDay(d) !== 0) {
				for (let i = this.getDay(d); i < 7; i++) {
					this.dates[currWeek].push({ date: '' });
					this.selections[currWeek].push(false);
				}
			}
		},
		dateChange(e) {
			this.$emit("dateChanged", e);
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