<script setup>
import { ref } from 'vue';

const name = "Vue dinamico";

/* parte 1 */
const styleColor = "color:blue";
const arrayColores = ["blue", "green", "yellow"];
const active = true;
const parte1 = false;

/* parte 2 */
const parte2 = false;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];

/* parte 2.2*/
const parte2_2 = false;
const arrayFrutas2 = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
  },
];

/* parte 3 */
const parte3 = false;
const objetFruit = {
  name: "Manzana",
  price: "$1.00",
  description: "Una manzana",
  id: 1
};

  /* parte 4 v-for v-if */
  const parte4 = false;
  const arrayFrutas3 = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];

  /* parte 5 eventos*/
  const parte5 = false;

  // metodo - method
    const handleClick = (msj) => {
      alert(msj);
    }

  // parte 6 reactividad

// importar modulos de ref de la libreria de vue en la primera parte line 2

  const parte6 = false;
  
  const counter = ref(0);
  const color = ref(["red","green"]);

  const increment = () => counter.value++;
  
  const disminuir = () => counter.value--;

  const reset = () => counter.value = 0;

  // parte 7 computed
  const parte7 = true
</script>

<template>

  <h1>Hola {{ name }}</h1>
    
  <!-- parte 1 ejemplos-->
  <div v-if="parte1">
    <h2>{{ arrayColores }}</h2>
    <h2 :style="`color:${arrayColores[2]}`">Soy {{ arrayColores[2] }}</h2>
    <h3>{{ active ? "Estoy activado" : "Estoy desactivado" }}</h3>
    <p v-if="active === true">Estoy activo</p>
    <p v-else-if="active === false">Estoy inactivo</p>
    <p v-else>Estoy incomprendido XD</p>
    <h2 v-show="active">Estoy activo v-show</h2>
  </div>

  <!--Parte2 v-for-->
  <div v-if="parte2">
    <ul>
      <li v-for="(fruta, index) in arrayFrutas" :key="index">
        {{ index }} - {{ fruta }}
      </li>
    </ul>
  </div>

  <!--Parte 2.2 v-for array y objet-->
  <div v-if="parte2_2">
    <ul>
      <li v-for="fruta in arrayFrutas2" :key="fruta.name">
        {{ fruta.name }} <br />
        {{ fruta.price }} <br />
        {{ fruta.description }}
      </li>
    </ul>
  </div>

<!--parte 3-->
  <div v-if="parte3">
    {{ objetFruit }}
    <br>
    <ul>
      <li class="objectFruit" 
      v-for="(value, propiedad, index) in objetFruit"
      :key="value"
      >
        {{ index }} - {{ propiedad }}: {{ value }}
      </li>
    </ul>
  </div>

<!-- parte 4-->
  <div v-if="parte4">
  <ul>
    <template  v-for="item in arrayFrutas3" 
    :key="item.name"
    >
      <li 
        v-if="item.stock > 0"
        >
        {{ item.name }} - {{ item.price }}
      </li>
    </template>
  </ul>
  </div>

<!--parte 5-->
  <div v-if="parte5">
    <button v-on:click.right.prevent="handleClick('mensaje right')">Activame Right</button>
    <button @:click="handleClick('mensaje left')">Activame Left</button>
    <button v-on:click.middle="handleClick('mensaje middle')">Activame Middle</button>
  </div>

  <!--parte 6-->
  <div v-if="parte6">
    <h2 :style="`color: ${counter < 0 ? color[0] : color[1]} `">{{ counter }}</h2>
    <h2 :class="counter >= 0 ? 'positive' : 'negative'">
        {{ counter }}
    </h2>
    <button v-on:click="increment">Aumentar</button>
    <button v-on:click="disminuir"> Disminuir</button>
    <button v-on:click="reset"> Reset</button>
  </div>

    <!--parte 7-->
    <div v-if="parte7">
    <h2 :style="`color: ${counter < 0 ? color[0] : color[1]} `">{{ counter }}</h2>
    <h2 :class="counter >= 0 ? 'positive' : 'negative'">
        {{ counter }}
    </h2>
    <button v-on:click="increment">Aumentar</button>
    <button v-on:click="disminuir"> Disminuir</button>
    <button v-on:click="reset"> Reset</button>
  </div>
</template>

<style>
li{
  list-style: none;
}
h1 {
  color: #8c8c8c;
}
.objectFruit{
  text-transform: capitalize;
}
.negative{
  color: red;
}
.positive{
  color: green;
}
</style>
