<template>
    <div class="flag">
        <div
            v-for="(pays, index) in listePays"
            :key="index"
            class="flag__wrapper"
        >
            <div @click="FlagDetail(pays)" class="flag__card">
                <!-- <h1>{{ pays.translations.fr }}</h1> -->
                <div class="flag__img">
                    <img :src="pays.flag" alt="" class="flag__img" />
                </div>
                <div class="flag__description">
                    <h2 class="flag__name">{{ pays.translations.fr }}</h2>
                    <h2 class="flag__capital">
                        {{ pays.capital }}
                    </h2>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Flag",
    data() {
        return {
            listePays: null,
        };
    },
    methods: {
        FlagDetail(paysName) {
            // pN: Pays name you can seen on rooter/index.js
            this.$router.push({
                name: "Detail",
                params: { pN: paysName },
            });
        },
    },
    mounted() {
        this.axios
            .get("https://restcountries.eu/rest/v2/region/europe")
            .then((response) => {
                this.listePays = response.data;
                console.log(this.listePays);
            });
    },
};
</script>

<style scoped>
.flag {
    width: 90%;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 24% 24% 24% 24%;
    column-gap: 20px;
}
.flag__wrapper {
    /* display: grid;
    grid-template-rows: 25% 25% 25% 25%; */
    display: flex;
}
.flag__card {
    /* margin-top: 200px; */
    height: 320px;
    width: 310px;
    margin-top: 20px;
    cursor: pointer;

    /* background-color: red; */
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.flag__card:hover {
    transform: scale(1.01);
}
.flag__img {
    /* background-color: red; */
    width: 100%;
    height: 75%;
    background-size: cover;
}
.flag__description {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-top: 15px;
    color: #2b2c92;
}
</style>
