<template>
  <div class="container mx-auto mt-10 flex flex-col items-center">
    <h1 class="text-4xl mb-10 text-sky-700">Random Gif Cat</h1>
    <div class="grid grid-cols-4 sm:grid-cols-2 gap-6">
      <div>
        <input class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm w-4/5" type="text" v-model="title" placeholder="Titulo" />
      </div>
      <div>
        <select v-model="filtro" class="italic text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm w-4/5">
          <option value="">Sin filtro</option>
          <option
            v-for="(filtro, index) in filtros"
            :key="index"
            :value="filtro"
            v-text="filtro"
          ></option>
        </select>
      </div>
      <div>
        <input type="number" v-model="size" placeholder="Tamaño texto" class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm w-4/5" />
      </div>
      <div class="flex flex-row items-center justify-between">
        <select name="color" v-model="color" class="italic text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm w-4/5">
          <option value="white">Color</option>
          <option
            v-for="(color, index) in colors"
            :key="index"
            :value="color"
            v-text="color"
          ></option>
        </select>
        <div class="circulo border-2 rounded-full bg-red-400 w-6 h-6" :style="{ 'background-color': `${this.color}` }"></div>
      </div>
    </div>
    <button @click="getGif" class="my-10 inline-block px-6 py-2.5 bg-sky-700 text-white font-medium text-xs leading-tight uppercase rounded shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out">Obtener mi gatito</button>
    <img :src="gif" alt="" width="400" height="400" />
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    title: "",
    filtro: "",
    filtros: ["blur", "mono", "sepia", "negative", "paint"],
    color: "white",
    colors: ["white", "red", "green", "blue", "yellow"],
    size: "",
    gif: "",
  }),
  methods: {
    getGif(){
      this.gif = `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filtro}&color=${this.color}&size=${this.size}&type=or`
    },
  },
};
</script>

<style>
* {
  font-family: 'Raleway', sans-serif;
}
</style>
