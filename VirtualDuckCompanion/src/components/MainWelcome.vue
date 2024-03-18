<script setup>
import Clock from '../components/Clock.vue'
import Login from '../components/Login.vue'
</script>

<template>
  <h1>Welcome {{ user }}</h1>
  <div>
    <Clock />
  </div>
  <Login />
</template>

<script>
export default {
  data() {
    return {
      user: 'Marlon'
    }
  }
}
</script>

<style></style>
