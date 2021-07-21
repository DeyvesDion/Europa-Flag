<template>
    <div>
        <div class="router__link">
            <router-link to="/">Accueil</router-link>
        </div>
        <div class="detail">
            <div class="">
                <img :src="paysUnique.flag" class="detail__flag" />
            </div>
            <div class="detail__description">
                <h3 class="item">Pays : {{ paysUnique.translations.fr }}</h3>
                <h3 class="item">Capital : {{ paysUnique.capital }}</h3>
                <h3 class="item">
                    Langue :
                    <span
                        v-for="(pays, index) in paysUnique.languages"
                        :key="index"
                        >{{ pays.name }}</span
                    >
                </h3>
                <h3 class="item">
                    Population : {{ paysUnique.population }} habitants
                </h3>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Detail",
    data() {
        return {
            getFlag: this.$route.params.Np,
            paysUnique: [],
        };
    },
    mounted() {
        this.axios
            .get(`https://restcountries.eu/rest/v2/name/${this.getFlag}`)
            .then((response) => {
                this.paysUnique = response.data[0];
                console.log(this.paysUnique);
            });
    },
    computed: {
        getPaysByName() {},
    },
};
</script>

<style scoped>
.detail {
    width: 90%;
    margin: 0 auto;
    margin-top: 50px;
    margin-bottom: 50px;
    display: grid;
    grid-template-columns: 66% 30%;
    column-gap: 50px;
}
.detail__flag {
    width: 100%;
    height: 500px;
    background-size: cover;
}
.detail__description {
    width: 100%;
    height: auto;
    padding: 10px;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.item {
    margin: 10px;
}
.router__link {
    margin-left: 62px;
}

@media screen and (min-width: 10px) and (max-width: 1039px) {
    .detail {
        display: block;
        /* margin: 0 auto; */
    }
    .detail__description {
        margin-top: 30px;
    }
    .detail__flag {
        height: 400px;
    }
}

@media screen and (min-width: 10px) and (max-width: 560px) {
    .detail__flag {
        height: 200px;
    }
}
</style>
