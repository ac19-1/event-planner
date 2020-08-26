<template>
	<v-app>
		<navbar />
		<div class="time d-flex justify-content-end w-90 mx-auto">
			<label
				for
				title="Current time"
				class="numbers"
			>{{now.hour + ' : ' + now.minute + ' : ' + now.second}}</label>
		</div>
		<div
			class="calendar d-flex justify-content-center align-items-center w-90 h-80vh m-auto rounded overflow-hidden"
		>
			<div class="detail position-relative w-30 h-100 bg-white">
				<v-img
					class="month-img position-absolute top-50 left-50"
					v-if="selected.month!==''"
					:src="require(`~/assets/images/months/${selected.month.toLowerCase()}.svg`)"
					width="95%"
				></v-img>
				<div id="custom-overlay" class="position-relative w-100 h-100">
					<h1
						class="unselectable shadow-date position-absolute font-weight-bold left-50"
					>{{selected.date}}</h1>
					<h1 class="unselectable date position-absolute font-weight-bold left-50">{{selected.date}}</h1>
					<h2
						class="unselectable shadow-month position-absolute font-weight-bold left-50"
					>{{selected.month}}</h2>
					<h2 class="unselectable month position-absolute font-weight-bold left-50">{{selected.month}}</h2>
				</div>
			</div>
			<div class="days w-70 h-100 bg-light calendar-container">
				<calendar-header :year="selected.year" :month="selected.month" />
				<calendar-body class="text-center" year="2020" month="8" />
			</div>
		</div>
	</v-app>
</template>

<script>
import Navbar from "~/components/Navbar";
import CalendarBody from "~/components/CalendarBody";
import CalendarHeader from "~/components/CalendarHeader";

export default {
	components: {
		Navbar,
		CalendarBody,
		CalendarHeader,
	},
	data() {
		return {
			now: {
				second: "--",
				minute: "--",
				hour: "--",
				date: "",
				day: "",
				month: "",
				year: "",
			},
			selected: {
				date: "",
				day: "",
				month: "",
				year: "",
			},
			colors: [
				"rgba(243, 255, 15, 0.4)",
				"rgba(255, 0, 0, 0.4)",
				"rgba(148, 148, 148, 0.4)",
				"rgba(84, 255, 118, 0.4)",
				"rgba(255, 255, 84, 0.4)",
				"rgba(255, 157, 79, 0.4)",
				"rgba(79, 188, 255, 0.4)",
				"rgba(170, 255, 0, 0.4)",
				"rgba(189, 151, 0, 0.4)",
				"rgba(96, 20, 139, 0.4)",
				"rgba(232, 31, 255, 0.4)",
				"rgba(41, 218, 35, 0.4)",
			],
		};
	},
	methods: {
		setTime() {
			let now = new Date();
			this.now.second =
				now.getSeconds() < 10
					? "0" + now.getSeconds()
					: now.getSeconds();
			this.now.minute =
				now.getMinutes() < 10
					? "0" + now.getMinutes()
					: now.getMinutes();
			this.now.hour =
				now.getHours() < 10 ? "0" + now.getHours() : now.getHours();
			this.now.date =
				now.getDate() < 10 ? "0" + now.getDate() : now.getDate();
			this.now.month = this.getMonthName(now.getMonth());
			this.now.year = now.getFullYear();
			this.now.day = this.getDayName(now.getDay());
		},
		setSelected(selected) {
			this.selected.date =
				selected.getDate() < 10
					? "0" + selected.getDate()
					: selected.getDate();
			this.selected.month = this.getMonthName(selected.getMonth());
			this.selected.year = selected.getFullYear();
			this.selected.day = this.getDayName(selected.getDay());
			this.setOverlay(selected.getMonth());
		},
		setOverlay(month) {
			let custom = document.querySelector("#custom-overlay");
			custom.style.background = this.colors[month];
		},
		getMonthName(month) {
			let months = [
				"January",
				"February",
				"March",
				"April",
				"May",
				"June",
				"July",
				"August",
				"September",
				"October",
				"November",
				"December",
			];
			return months[month];
		},
		getDayName(day) {
			let days = [
				"Sunday",
				"Monday",
				"Tuesday",
				"Wednesday",
				"Thursday",
				"Friday",
				"Saturday",
			];
			return days[day];
		},
		onLoad() {
			setInterval(() => {
				this.setTime();
			});
			this.setSelected(new Date());
		},
	},
	mounted() {
		this.onLoad();
	},
};
</script>

<style>
.calendar-container {
	display: flex;
	flex-direction: column;
	padding: 1%;
}

.calendar-container > div:first-child {
	margin: 1% 0;
}

.month-img {
	transform: translate(-50%, -50%);
}

.date,
.shadow-date {
	font-size: 12rem;
}

.date {
	color: #ffffff;
	top: 15%;
	transform: translate(-50%, -15%);
}

.shadow-date {
	color: #797979;
	top: 18%;
	transform: translate(-50%, -18%);
}

.month,
.shadow-month {
	font-size: 4rem;
}

.month {
	color: white;
	top: 55%;
	transform: translate(-50%, -55%);
}

.shadow-month {
	color: #797979;
	top: 56.5%;
	transform: translate(-50%, -56.5%);
}

.unselectable {
	-webkit-user-select: none;
	-ms-user-select: none;
	user-select: none;
}
</style>