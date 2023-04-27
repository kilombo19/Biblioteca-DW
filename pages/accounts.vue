<template>
    <div>
        <h1>Cuentas Creadas</h1>
        <button @click="loadAccounts">Cargar Cuentas </button>
     <ul>
        <li></li>
     </ul>
    </div>
</template>

< script lang="ts">
export default{
methods:{
    loadAccounts(){
        console.log("Cargar cuentas");
        const url="http://localhost:3000/accounts"
        this.$axios.get(url).then((response) => {
            console.log(response);
        }).catch(error =>{
            console.log(error);
        })
    }
}
}
</script>

<style>

</style>