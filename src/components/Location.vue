<template>
    <div class="location" v-bind:style=" { backgroundColor: hexColor }">
        <div class="title">
            {{location.title}}
        </div>
        <div class="students">
            <Student :hex-color="hexColor" :opacity="0.5 + (index + 1) / (location.students.length * 2)" v-for="(student, index) in location.students" :key="index" :student="student" />
        </div>
    </div>
</template>

<script>
    import Student from "./Student.vue"
    export default {
        name: "Location",
        props: {
            location: Object,
            hexColor: {
                type: String,
                default: '#000000'
            },
        },
        components: {
            Student
        }
    }
</script>

<style scoped>
    .location {
        display: flex;
        box-sizing: content-box;
       align-items: center;
    }
    .title {
        padding: 0 10px;
        color: white;
        flex-grow: 1;
    }
    .students {

    }
</style>