<template>
  <div class="parent">
    <p>親コンポ</p>
    <p>データ：{{ patients }}</p>
    <button @click="addPatientData">追加</button>
    <div>
      <Child
        v-for="(patient, index) in patients"
        v-bind:key="patient.index"
        :name="patient.name"
        :index="index"
        @my-input="inputPatientName"
        @delete-patient="deletePatient"
      />
    </div>
  </div>
</template>

<script>
import Child from '@/components/Child'

export default {
  components: {
      Child
  },
  data() {
    return {
      patients: [{name: ''}]
    }
  },
  methods: {
    addPatientData() {
      const addData = {
        name: ''
      }
      this.patients.push(addData)
    },
    deletePatient(id) {
      this.patients.splice(id, 1)
    },
    inputPatientName(e) {
      console.log(e)
      this.patients[e.index].name = e.value
    }
  }
}
</script>

<style>
.parent {
  height: 400px;
  width: 400px;
  background-color: aqua;
}
</style>