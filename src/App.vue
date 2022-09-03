<template>
  <h1>Iron Contacts</h1>
  <button @click="getRandomElem">Add Random Contact</button>
  <button>Sort by popularity</button>
  <button @click="sortByName">Sort by name</button>
  <table style="width: 100%">
    <thead>
      <tr>
        <th>Picture</th>
        <th>Name</th>
        <th>Popularity</th>
        <th>Won Oscar</th>
        <th>Won Emmy</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in contacts" :key="item.id">
        <td>
          <img :src="item.pictureUrl" alt="contact Image" />
        </td>
        <td>{{ item.name }}</td>
        <td>{{ item.popularity.toFixed(2) }}</td>
        <td>
          <img
            v-if="item.wonOscar == true"
            src="./assets/trofeo.png"
            id="trofeo"
            alt=""
          />
        </td>
        <td>
          <img
            v-if="item.wonEmmy == true"
            src="./assets/trofeo.png"
            id="trofeo"
            alt=""
          />
        </td>
        <td><button @click="removecontact(contact)">Delete</button></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import contacts from "./contacts.json";

export default {
  name: "App",
  data() {
    return {
      contacts,
      fiveContacts: [],
    }
  },
  created() {
    for (let i = 0; i < 5; i++) {
      this.fiveContacts.push(this.contacts.shift())
    }
  },
method: {
  sortByName() {
    this.fiveContacts.sort((a,b) => a.name > b.name ? 1 : -1);
  }
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  width: 40%;
  height: auto;
}

#trofeo {
  width: 3%;
  height: auto;
}
</style>
