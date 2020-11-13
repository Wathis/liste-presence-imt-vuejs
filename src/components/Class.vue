<template>
    <div class="classe">
        <div class="title">{{studentClass.title}}</div>
        <div class="locations">
            <Location v-for="location in studentClass.locations" :key="location.name" :location="location" :hex-color="location.hexColor" />
        </div>
    </div>
</template>

<script>
    import Location from './Location.vue'
    export default {
        name: "Class",
        props: {
            name : String,
            studentClass : Object,
        },
        components: {
            Location
        }
    }
</script>

<style scoped>
    .classe {
        color: white;
        display: inline-flex;
        align-items: center;
        background-color: #607D8B;
    }
    .locations {

    }
    .title {
        padding: 0 20px;
        text-align: center;
        flex-grow: 1;
    }
</style>