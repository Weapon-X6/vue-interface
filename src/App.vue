<template>
    <div id="haupt-app" class="container">
        <h4>{{ Titel }}</h4>
        <font-awesome-icon icon="plus" class="mr-2" />
        <button class="btn btn-success">mehr Mühe geben</button> <br />
        <hr />
        <div class="row justify-content-center">
            <appointment-list
                :appointments="appointments"
                @remove="removeItem"
            />
        </div>
    </div>
</template>

<script>
import AppointmentList from "./components/AppointmentList";
import axios from "axios";
//import func from 'vue-editor-bridge';
import _ from "lodash";

export default {
    name: "hauptApp",
    data: function() {
        return {
            Titel: "New Way Home",
            appointments: [],
            aptIndex: 0,
        };
    },
    components: {
        AppointmentList,
    },
    mounted() {
        axios.get("./data/appointments.json").then(
            response =>
                (this.appointments = response.data.map(item => {
                    item.aptId = this.aptIndex;
                    this.aptIndex++;
                    return item;
                }))
        );
    },
    methods: {
        removeItem: function(apt) {
            this.appointments = _.without(this.appointments, apt);
        },
    },
};
</script>
