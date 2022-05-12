<template>
<div>
  <h1>Random Gif Cat</h1>
  <form @submit.prevent="obtenerGatito">
    <div class="input">
      <label for="title">Titulo: </label>
      <input type="text" name="title" v-model="title">
    </div>
    <div class="input">
      <label for="filter">Filtro: </label>
      <select v-model="filtro"> 
        <option v-for="(filtro, index) in filtros" :key="index" :value="filtro" v-text="filtro">
        </option> 
      </select>
    </div>
    <div class="input">
      <label for="color">Color: </label>
      <select name="color" v-model="color">
        <option v-for="(color, index) in colors" :key="index" :value="color" v-text="color">
        </option>
      </select>
    </div>
    <div class="input">
      <label for="size">Tamaño: </label>
      <input type="number" name="size" v-model="size">
    </div>
    <button type="submit">Obtener mi gatito</button>
  </form>
  <img :src="url" alt="">
</div>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    url: '',
    title: '',
    filtro: 'blur',
    filtros: ['blur','mono','sepia','negative','paint','pixel'],
    color: '',
    colors: ['white', 'red', 'green'],
    size: ''
  }),
  methods: {
    obtenerGatito() {
      this.url = `https://cataas.com/cat/says/${this.title}?size=${this.size}&color=${this.color}?filter=${this.filtro}`
      console.log(this.url)
      // fetch(`https://cataas.com/cat/says/${this.title}?size=${this.size}&color=${this.color}?filter=${this.filtro}`)
      //   .then(response => response.json())
      //   .then(data => console.log(data))
    }
  }
}
</script>

<style>
.input{
  display: flex;
  gap: 10px;
  margin-bottom: 10px;
}

</style>
