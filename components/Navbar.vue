<template>
  <div class="custom-navbar d-flex justify-content-between align-items-center mx-auto w-90 py-5">
    <div class="home">
      <v-btn text class="text-capitalize" @click="gotoAndRefresh('./')">Home</v-btn>
    </div>
    <ul class="d-flex justify-content-center align-items-center list-style-none m-0">
      <li class="px-3">
        <v-btn text class="text-capitalize" @click="goto('./calendar')">Calendar</v-btn>
      </li>
      <li class="px-3">
        <v-btn text class="text-capitalize" @click="goto('./events')">Events</v-btn>
      </li>
      <li class="px-3">
        <v-btn text class="text-capitalize" @click="goto('./login')">Login</v-btn>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
   methods: {
    goto(url) {
      this.$router.push(url)
    },
    gotoAndRefresh(url) {
      window.location.href = url
    }
  }
};
</script>

<style>
</style>