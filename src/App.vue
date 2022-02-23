<template>
  <div id="app" class="container">
    <div class="row justify-content-center">
      <appointment-list :appointments="appointments" @remove="removeItem"/>
    </div>
  </div>
</template>

<script>

import axios from "axios"
import AppointmentList from "./components/AppointmentList.vue"
import _ from "lodash"

export default {
  name: "App",
  data: function () {
    return {
      appointments: [],
      aptIndex: 0
    };
  },
  components: {
    AppointmentList
  },
  mounted(){
    axios.get("./data/appointments.json")
    .then(response => (this.appointments = response.data))
  },
  methods: {
    removeItem: function(apt) {
      this.appointments = _.without(this.appointments, apt)
    }
  }
};
</script>

<style>
</style>
