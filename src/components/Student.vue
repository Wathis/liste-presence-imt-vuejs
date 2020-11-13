<template>
    <div class="student" >
        <div class="fullNameContainer" v-bind:style="{backgroundColor: hexToRgbaCss(hexColor, opacity)}">
            <!--<span class="button">-->
                <!--<content-copy-icon />-->
            <!--</span>-->
            <span class="button">
                <a class="mailto" :href="'mailto:' + student.email"><email-icon /></a>
            </span>
            <span class="fullName">{{`${student.firstName} ${student.lastName}`}}</span>
        </div>
    </div>
</template>

<script>
    import EmailIcon from "vue-material-design-icons/Email";
    export default {
        name: "Student",
        methods: {
            hexToRgb(hex) {
                var result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
                return result ? {
                    r: parseInt(result[1], 16),
                    g: parseInt(result[2], 16),
                    b: parseInt(result[3], 16)
                } : null;
            },
            hexToRgbaCss(hex, opacity) {
                return `rgba(${this.hexToRgb(hex).r},${this.hexToRgb(hex).g},${this.hexToRgb(hex).b},${opacity})`
            },
        },
        props: {
            student: Object,
            hexColor: {
                type: String,
                default: '#000000'
            },
            opacity: {
                type: Number,
                default: 1
            },
        },
        components: {
            EmailIcon,
        },
    }
</script>

<style scoped>
    .student {
        text-align: left;
        width: 200px;
        background-color: white;
    }
    .fullNameContainer {
        display: flex;
        align-items: center;
        padding: 10px;
    }
    .button {
        cursor: pointer;
    }
    .mailto {
        text-decoration: none;
        color: white;
    }
    .fullName {
        padding-left: 5px;
    }
</style>