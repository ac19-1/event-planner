<template>
	<v-btn fab text class="calendar-date">{{date}}</v-btn>
</template>

<script>
export default {
	props: ["date"],
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