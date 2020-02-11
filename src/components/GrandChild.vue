<template>
  <div class="child">
    <p>孫コンポ</p>
    <input
      :value="value" @input="inputText"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String
    }
  },
  methods: {
    inputText(e) {
      this.$emit('my-input', e.target.value)
    }
  }
}
</script>

<style>
.child {
  width: 100px;
  height: 100px;
  background-color: beige;
}
</style>