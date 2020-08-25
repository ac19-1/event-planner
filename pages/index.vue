<template>
  <v-app>
    <div class="header position-relative h-100vh">
      <img class="calendar position-absolute left-75 top-50" src="~/assets/images/events.svg" alt="" width="30%">
      <div class="title position-absolute left-25 top-50 w-50">
        <h1 class="font-weight-bold color-salmon">Event Planner</h1>
        <h5 class="color-dark-gray">Plan <font class="color-salmon">everything</font> nicely.</h5>
        <v-btn class="text-capitalize my-3" @click="gotoAndRefresh('./calendar')" dark large>Plan Now!</v-btn>
      </div>
      <img class="wave position-absolute top-100 left-100" src="~/assets/images/wave.png" alt="" width="100%">
    </div>
  </v-app>
</template>

<script>
export default {
  methods: {
    gotoAndRefresh(url) {
      window.location.href = url
    }
  }
}
</script>

<style>
  .calendar {
    transform: translate(-75%, -50%);
    z-index: 2;
  }

  .title {
    transform: translate(-25%, -50%);
    z-index: 3;
  }

  .wave {
    transform: translate(-100%, -100%)
  }
</style>