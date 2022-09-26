<script >
import axios from "axios";
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increment() {
      this.count++
      axios.post('http://localhost:3000/updateCount', {
      count: this.count,
      created: []
    })
      .then(response => (this.info = response))
    }
  },
  mounted() {
    axios.get('http://localhost:3000/getCount')
      .then(response => (this.count = response.data.data.count))
  }
}
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ count }}</h1>
    <button @click="increment()">Increment</button>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
