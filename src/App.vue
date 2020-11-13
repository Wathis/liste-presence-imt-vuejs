<template>
  <div id="app">
    <Class :studentClass="studentClass"></Class>
  </div>
</template>

<script>

import Class from './components/Class.vue'
import {studentList} from './studentList'

const groupBy = (array, key) => {
    return array.reduce((result, currentValue) => {
        (result[currentValue[key]] = result[currentValue[key]] || []).push(
            currentValue
        );
        return result;
    }, {});
};

const colors = ["#F44336", "#4CAF50", "#9C27B0", "#795548", "#607D8B","#2196F3"];

export default {
  name: 'App',
  components: {
      Class,
  },
  data: function () {

      const studentsGroupedByStatus = groupBy(studentList, 'status');
      const locations = Object.keys(studentsGroupedByStatus).map((status, index) =>
          ({
              title: status,
              hexColor: colors[index % colors.length],
              students: studentsGroupedByStatus[status]
          })
      );
      console.log(locations);

      return {
          studentClass : {
              title: "FIL A3",
              locations: locations
          },
      };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  text-align: center;
}
</style>
