<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Users</h2>
    <ul>
      <li v-for="user in users">
        {{user.firstname}} {{user.lastname}}
      </li>
    </ul>
    <div>
      <input type="text" v-model="input_val">
    </div>

    <p>{{input_val}} karaoke</p>
    <p>Input value: <span v-text='input_val'></span></p>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Karaokleiton',
      users: [
        {firstname: 'Sebastian', lastname: 'Eschweiler'},
        {firstname: 'Bill', lastname: 'Smith'},
        {firstname: 'John', lastname: 'Porter'}
      ],
      input_val: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

a {
  color: #42b983;
}
</style>
