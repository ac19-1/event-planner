<template>
	<v-btn v-if="date!==''" fab text class="calendar-date" @click="dateChange(date)">{{date}}</v-btn>
	<v-btn v-else fab text class="calendar-date" disabled>{{date}}</v-btn>
</template>

<script>
export default {
	props: ["date"],
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
}
</style>