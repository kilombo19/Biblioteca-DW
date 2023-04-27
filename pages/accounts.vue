<template>
  <div>
    <h1>Cuentas Creadas</h1>
    <button @click="loadAccounts">Cargar Cuentas</button>
    <ul>
      <li v-for="account in accounts" :key="account.id">
        {{ account.firstname }} {{ account.lastname }}
      </li>
    </ul>
  </div>
</template>

< script lang="ts">
export default {
  data() {
    return {
      accounts: []
    }
  },

  methods: {
    loadAccounts() {
      console.log('Cargar cuentas');
      const url = 'http://localhost:3000/accounts'
      this.$axios
        .get(url)
        .then((response) => {
          const data = response.data
          this.accounts = data
        })
        .catch((error) => {
          console.log(error)
        })
    },
  },
}
</script>

<style>
</style>