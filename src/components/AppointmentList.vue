<template>
    <div>
        <div v-for="(item, i) in appointments" v-bind:key="i">
            {{ item.petName }}
            <p>{{ item.aptNotes }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "AppointmentList",
    props: ["appointments"]
}
</script>

