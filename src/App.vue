<template>
    <div id="haupt-app" class="container">
        <h4>{{ Titel }}</h4>
        <font-awesome-icon icon="plus" class="mr-2" /> <button class="btn btn-success">mehr Mühe geben</button> 
        <br><hr>
        <appointment-list :appointments="appointments"></appointment-list>
    </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import AppointmentList from "./components/AppointmentList"
import axios from "axios";

export default {
    name: "hauptApp",
    data: function() {
        return {
            Titel: "New Way Home",
            appointments: []
        };
    },
    components: {
        FontAwesomeIcon,
        AppointmentList 
    },
    mounted(){     
      axios
      .get("./data/appointments.json")
      .then(response => (this.appointments = response.data));
    }
};
</script>
