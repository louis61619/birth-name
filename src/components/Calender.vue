<template>
  <div @click="childClick">
    <b-calendar v-model="value" :max="max" locale="en"></b-calendar>
  </div>
</template>

<script>
  export default {
    data() {
      const now = new Date()
      const today = new Date(now.getFullYear(), now.getMonth(), now.getDate())
      // 15th two months prior
      const maxDate = new Date(today)

      return {
        value: '',
        max: maxDate
      }
    },
    methods: {
      childClick() { //定義傳值的事件
        console.log(this.value)
        this.$emit("childByValue",this.value)
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>