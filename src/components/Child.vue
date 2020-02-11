<template>
  <div class="grand-child">
    <p>子コンポ</p>
    {{ name }}
    {{ index }}
    <GrandChild
      :value="name"
      @my-input="inputPatientName"
    />
    <button @click="deletePatient">削除</button>
  </div>
</template>

<script>
import GrandChild from './GrandChild'

export default {
  components: {
    GrandChild
  },
  props: {
    name: {
      type: String
    },
    index: {
      type: Number
    }
  },
  methods: {
    inputPatientName(patientName) {
      this.$emit('my-input', {value: patientName, index: this.index})
    },
    deletePatient() {
      this.$emit('delete-patient', this.index)
    }
  }
}
</script>

<style>
.grand-child {
  width: 200px;
  height: 200px;
  background-color: aquamarine;
}
</style>
