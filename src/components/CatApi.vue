<template>
<div class="container">
    <form class="card" @submit.prevent="generateGif">
        <h1 class="card__title">Random Gif<br/> Cat</h1>
        <input class="card__catTitle" placeholder="Texto" v-model="catTitle" required>
        <input class="card__catSize" placeholder="Tamaño del Texto" type="number" v-model="catSize" step="50" max="200" min="25">
        <select class="card__catFilter" v-model="catFilter">
            <option value="" selected>Sin Filtro</option>
            <option value="blur">Blur</option>
            <option value="mono">Mono</option>
            <option value="sepia">Sepia</option>
            <option value="negative">Negative</option>
            <option value="paint">Paint</option>
            <option value="pixel">Pixel</option>
        </select>
        <div class="card__catColor-indicator" :style="{'background-color': catColor,}"></div>
        <select class="card__catColor" v-model="catColor">
            <option value="" selected>Blanco</option>
            <option value="black">Negro</option>
            <option value="red">Rojo</option>
            <option value="blue">Azul</option>
            <option value="yellow">Amarillo</option>
            <option value="green">Verde</option>
            <option value="brown">Cafe</option>
        </select>
        <button class="card__catBtn" type="submit">Generar Gato</button>
    </form>
    <div class="gif"> 
        <div class="card__warning">{{loadWarning}}</div>
        <img class="catImg" :src="catImg">
    </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data: () => ({
        catTitle: '',
        catFilter: '',
        catColor: '',
        catSize: '',
        catImg: '',
        loadWarning: '',
    }),
    methods: {
        generateGif() {
        this.loadWarning = '*Esto puede demorarse un poco*'
         axios
        .get(`https://cataas.com/cat/gif/says/${this.catTitle}?size=${this.catSize}&color=${this.catColor}&filter=${this.catFilter}`)
        .then((catUrl) => {
            this.catImg = catUrl.config.url
        })
        }
    },
}
</script>

<style lang="scss" scoped>
.card {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 2.5em);
    grid-template-areas: "title cattitle catcolor"
                        "title catsize catfilter" 
                        "title catbtn catbtn";
    width: 55%;
    padding: 1em;
    background-color: #C1CFC0;
    margin-top: 2em;
    border-radius: 0.5em;
    &__title {
        grid-area: title;
    }
    &__catTitle {
        grid-area: cattitle;
    }
    &__catSize {
        grid-area: catsize;
    }
    &__catFilter {
        grid-area: catfilter;
    }
    &__catColor {
        grid-area: catcolor;
    }
    &__catColor-indicator {
        width: 20px;
        height: 20px;
        border-radius: 10px;
        transition: background-color 0.3s;
    }
    &__catBtn {
        grid-area: catbtn;
        border: 0;
        border-radius: 1em;
        color: #ffffff;
        background-color: #368B85;
        transition: background-color 0.3s;
        cursor: pointer;
    }
    &__catBtn:hover {
        background-color: #2b6e6a;
    }
    &__catBtn:active {
        background-color: #153735;
    }
    &__warning {
        margin-top: 0.5em;
        font-style: italic;
        text-align: center;
    }

}
.card * {
    text-align: center;
    margin: 0.3em 0.3em;
}
input, select {
    border: 0;

}
input:focus, select:focus {
    outline: none;
}
.gif {
    background-color: #6B7AA1;
    border-radius: 0.5em;
    width: 55%;
}
.catImg {
    display: block;
    margin: 2em auto;
}
</style>