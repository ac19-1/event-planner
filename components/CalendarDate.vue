<template>
	<v-btn v-if="date!=='' && $props.selected" fab text class="calendar-date selected-date" @click="dateChange(date)">{{date}}</v-btn>
	<v-btn v-else-if="date!=='' && !$props.selected" fab text class="calendar-date" @click="dateChange(date)">{{date}}</v-btn>
	<v-btn v-else fab text class="calendar-date" disabled>{{date}}</v-btn>
</template>

<script>
export default {
	props: ["date", "selected"],
	methods: {
		dateChange(e) {
			this.$emit("dateChanged", e);
		},	
	},
};
</script>

<style lang="scss">
div {
	.calendar-date {
		outline: none;
		span {
			font-family: "Roboto", sans-serif !important;
			font-weight: 400;
		}
	}

	.selected-date {
		color: rgb(34, 68, 177) !important;
		background-color: rgba(173, 173, 255, 0.2) !important;
		:focus {
			color: rgb(34, 68, 177) !important;
			background-color: rgba(173, 173, 255, 0.2) !important;
		}
	}
}
</style>