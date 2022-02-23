<template>
  <div id="app" class="container">
    <div class="row justify-content-center">
      <appointment-list :appointments="appointments"/>
    </div>
  </div>
</template>

<script>

import axios from "axios"
import AppointmentList from "./components/AppointmentList.vue"

export default {
  name: "App",
  data: function () {
    return {
      title: "Appointment List",
      appointments: []
    };
  },
  components: {
    AppointmentList
  },
  mounted(){
    axios.get("./data/appointments.json")
    .then(response => (this.appointments = response.data))
  }
};
</script>

<style>
</style>
