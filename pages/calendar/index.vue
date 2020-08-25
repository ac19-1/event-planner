<template>
  <v-app>
    <navbar/>
    <div class="time d-flex justify-content-end w-90 mx-auto">
      <label for="" title="Current time" style="font-family: Roboto">{{now.hour + ' : ' + now.minute + ' : ' + now.second}}</label>
    </div>
    <div class="calendar d-flex justify-content-center align-items-center w-90 h-80vh m-auto rounded overflow-hidden">
      <div class="detail w-30 h-100 bg-dark">
        
      </div>
      <div class="days w-70 h-100 bg-light">
        
      </div>
    </div>
  </v-app>
</template>

<script>
import Navbar from "~/components/Navbar";
export default {
  components: {
    Navbar
  },
  data() {
    return {
      now: {
        second: '',
        minute: '',
        hour: '',
        date: '',
        day: '',
        month: '',
        year: ''
      }
    }
  },
  methods: {
    setTime() {
      let now = new Date()
      this.now.second = now.getSeconds() < 10 ? '0' + now.getSeconds() : now.getSeconds()
      this.now.minute = now.getMinutes() < 10 ? '0' + now.getMinutes() : now.getMinutes()
      this.now.hour = now.getHours() < 10 ? '0' + now.getHours() : now.getHours()
      this.now.date = now.getDate() < 10 ? '0' + now.getDate() : now.getDate()
      this.now.month = now.getMonth() + 1 < 10 ? '0' + now.getMonth() + 1 : now.getMonth() + 1
      this.now.year = now.getFullYear()
      this.now.day = this.getDayName(now.getDay())
    },
    getDayName(day) {
      let days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday']
      return days[day]
    },
    onLoad() {
      setInterval(() => {
        this.setTime()
      });
    }
  },
  mounted() {
    this.onLoad()
  }
}
</script>

<style>

</style>