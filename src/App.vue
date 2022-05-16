<template>
<section class="align">
    <h1>Random gif cat</h1>
    <form @submit.prevent="crearGif()">
        <div class="input">
            <label for="title">Título</label>
            <input class="input-value" type="text" v-model="titulo" required>
        </div>
        <div class="input">
            <label for="filter">Filtro</label>
            <select class="input-value" name="filter" v-model="filtro" required>
                <option v-for="(filtro, $index) in filtros" :key="$index" :value="filtro"> {{ filtro }}</option>
            </select>
        </div>
        <div class="input">
            <label for="color">Color</label>
            <select class="input-value" name="color" v-model="color" required>
                <option v-for="(color, $index) in colores" :key="$index" :value="color">{{ color }}</option>
            </select>
        </div>
        <div class="input">
            <label for="tamaño">Tamaño</label>
            <input class="input-value" type="text" v-model="tamaño" required>
        </div>
        <button type="submit">Obtener mi gato</button>
    </form>
    <div class="image">
        <img v-if="url" :src="url" alt="gif gato">
    </div>
</section>
</template>

<script>
export default {
    name: 'App',
    data: () => ({
        url: "",
        titulo: "",
        filtro: "blur",
        filtros: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
        color: "red",
        colores: ["red", "blue", "green", "white", "yellow"],
        tamaño: ""
    }),
    methods: {
        crearGif() {
            this.url = `https://cataas.com/cat/says/${this.titulo}?size=${this.tamaño}&color=${this.color}&filter=${this.filtro}`
        }
    }

}
</script>

<style>
button {
    height: 32px;
    margin-top: 8px;
}
.input-value {
    height: 32px;
    border-width: 1px;
    border-radius: 5px;
    width: 250px;
    padding: 0px;
}
.input {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 16px;
    margin: 8px;
    justify-content: space-between;
    
}
img {
    margin: 12px;
}
.align {
    display: flex;
    flex-direction: column;
    align-items: center;
}

</style>