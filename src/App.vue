<template>
  <div class="container">
    <h1 class="app-title">{{ upperCaseTitle }}</h1>
    <div class="row">
      <div class="counter">
        Counter: <span>{{ counter }}</span> | Double counter: <span>{{ doubleCounter }}</span>
      </div>
      <div class="buttons">
        <button class="btn" @click="add">Add 1</button>
        <button class="btn" @click="addF">Add 5</button>
        <button class="btn" @click="incrementAsync({ value: 5, delay: 500 })">Add 5 Async</button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapMutations, mapActions } from 'vuex'

export default {
  name: 'App',
  computed: {
    ...mapGetters(['upperCaseTitle']),
    ...mapGetters('count', ['counter', 'doubleCounter'])
  },
  methods: {
    ...mapMutations({ add: 'count/increment' }),
    ...mapActions('count', ['incrementAsync']),
    ...mapMutations({
      addFive: 'count/add'
    }),
    addF () {
      this.addFive({ value: 5 })
    }
  }
}
</script>

<style>
</style>
