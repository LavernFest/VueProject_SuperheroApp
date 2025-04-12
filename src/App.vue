<script setup>

  import {ref} from 'vue'

  import axios from 'axios'

  var superheroSearch = defineModel()

  var superheroObject = ref()

  async function getSuperhero(){

    var response = await axios.get('http://localhost:8000/api/superheroes/' + superheroSearch.value )

    superheroObject.value = response.data

  }

</script>

<template>

  <h1>Superhero Api</h1>

  <input type="text" v-model="superheroSearch">

  <button @click="getSuperhero">Get Superhero</button>

  <div v-if="superheroObject">
    <table>
        <thead>
            <tr>
                <th>ID</th>
                <th>Superhero Name</th>
                <th>Real Name</th>
                <th>Universe</th>
                <th>Genre</th>
                <th>Gender</th>
            </tr>
        </thead>

        <tbody>
            <tr>
                <td>{{ superheroObject.id }}</td>
                <td>{{ superheroObject.name }}</td>
                <td>{{ superheroObject.realname }}</td>
                <td>{{ superheroObject.universo.unName }}</td>
                <td>{{ superheroObject.generolit.Type }}</td>
                <td>{{ superheroObject.genero.type }}</td>
            </tr>
        </tbody>
    </table>
  </div>

</template>