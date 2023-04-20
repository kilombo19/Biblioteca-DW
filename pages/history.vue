<template>
  <v-container fluid>
    <v-row style="background: #d92525; color: white">
      <v-col>
        <v-card
          d-flex
          style="
            background: #d92525;
            color: white;
            display: flex;
            align-items: center;
            justify-content: space-between;
          "
        >
          <v-card-title>
            <h1>Historial de Reservas</h1>
          </v-card-title>
          <v-card-title>
            <h1>@ahorasoykevin</h1>
          </v-card-title>
        </v-card>
      </v-col>
    </v-row>

    <!--------------------------------------------------------------------------------------->
    <v-row style="height: 80vh">
      <v-card fluid>
        <v-list style="width: 1000vh">
          <v-subheader>LIBROS</v-subheader>
          <v-list-item-group>
            <h1>La Insoportable Levedad del Ser</h1>
            <h1>La Guia del Autoestopista Galactico</h1>
            <h1>Como Matar un Ruiseñor</h1>
            <h1>Juan Salvador Gaviota</h1>
            <h1>Miedo en el Monte</h1>
            <h1>El Péqueño Lord</h1>
            <h1>La Insoportable Levedad del Ser</h1>
            <h1>La Guia del Autoestopista Galactico</h1>
            <h1>Como Matar un Ruiseñor</h1>
            <h1>La Insoportable Levedad del Ser</h1>
          </v-list-item-group>
        </v-list>
      </v-card>
    </v-row>
    <!--------------------------------------------------------------------------------------->

    <v-row style="background: #d92525; color: white">
      <v-col>
        <v-card
          d-flex
          style="
            background: #d92525;
            color: white;
            display: flex;
            align-items: center;
            justify-content: space-around;
          "
        >
          <v-btn depressed> REGRESAR </v-btn>
          <v-btn depressed> SALIR </v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
export default {
  layout: 'blank',
}
</script>