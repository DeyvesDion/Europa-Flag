<template>
    <div class="">
        <div class="flag__wrapper">
            <div @click="FlagDetail(pays.name)" class="flag__card">
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
    props: ["pays"],
    data() {
        return {
            // listePays: null,
        };
    },
    methods: {
        FlagDetail(paysName) {
            // pN: Pays name you can seen on rooter/index.js
            this.$router.push({
                name: "Detail",
                params: { Np: paysName },
            });
        },
    },
    mounted() {
        this.axios
            .get("https://restcountries.eu/rest/v2/region/europe")
            .then((response) => {
                this.listePays = response.data;
                // console.log(this.listePays);
            });
    },
};
</script>

<style scoped>
.flag__wrapper {
    display: flex;
}
.flag__card {
    height: 320px;
    width: 310px;
    margin-top: 20px;
    cursor: pointer;

    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.flag__card:hover {
    transform: scale(1.01);
}
.flag__img {
    width: 100%;
    height: 75%;
    background-size: cover;
}
.flag__description {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: #2b2c92;
    font-size: 12px;
}
</style>
