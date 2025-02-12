<script lang="ts">
export default {
  name: "Home",
  data() {
    return {
      miArray: [
        { id: 1, name: "carlos", roles: [1, 2] },
        { id: 2, name: "Miguel", roles: [1, 2] },
        { id: 3, name: "Pepe", roles: [1, 2] },
        { id: 4, name: "Andrea", roles: [1, 2] },
        { id: 5, name: "riservi", roles: [1, 2] },
      ],
      output: "",
    };
  },
  methods: {
    imparOPar: (num: number): boolean => {
      return Boolean(num % 2);
    },
    generarSalida: function () {

      const total = this.miArray.filter(x => this.imparOPar(x.id));

      this.output = `el total de listado es: ${total.length}`

    }
  },
};
</script>

<template>
  <div id="contenedor">
    <div class="bloque1">
      <p>Este es el Bloque 1 dentro del contenedor.</p>
    </div>

    <div class="bloque2">
      <p>
        Este es el contenido del Bloque 2 dentro del contenedor, este contiene
        mas texto, por eso debe ser mas largo.
      </p>
    </div>
    <div class="clear"></div>
  </div>

  <div class="bloque1">
    <p>Este es el Bloque 1 fuera del contenedor.</p>
  </div>

  <div class="bloque2">
    <p>Este es el Bloque 2 fuera del contenedor.</p>
  </div>

  <div class="v-container" v-for="item in miArray" v-bind:key="item.id">
    <div
      v-bind:style="{
        display: imparOPar(item.id) ? 'block' : 'none',
        'background-color': imparOPar(item.id) ? '#e6e6e6' : 'inherit',
      }"
    >
      <div>{{ item.name }}</div>
      <div>{{ item.roles.join(",") }}</div>
    </div>
  </div>
  <div @click="generarSalida" class="btn">Generar</div>
  <div class="output">{{ output }}</div>
</template>

<style scoped>
#contenedor {
  min-width: 600px;
  padding: 10px;
  margin: 10px;
  border: 1px dotted gray;
}

p {
  padding: 10px;
}

.clear {
  clear: both;
}

.bloque1 {
  background-color: red;
  color: #fff;
}

.bloque2 {
  background-color: yellow;
  color: #000;
}

#contenedor .bloque1 {
  width: 100px;
  margin: 70px 5px 5px 5px;
  float: left;
}

#contenedor .bloque1 p {
  font-family: Italic;
}

#contenedor .bloque2 {
  width: 100px;
  float: left;
  margin: 5px 5px 5px 5px;
}

#contenedor .bloque2 p {
  font-weight: bold;
}
</style>
