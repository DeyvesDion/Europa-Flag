<template>
    <div class="home">
        <Header />
        <div class="flag">
            <Flag
                v-for="(pays, index) in listePays"
                :key="index"
                :pays="pays"
            ></Flag>
        </div>
    </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
import Flag from "@/components/Flag.vue";

export default {
    name: "Home",
    components: {
        Header,
        Flag,
    },
    data() {
        return {
            listePays: null,
        };
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
<style scope>
.flag {
    width: 90%;
    margin: 0 auto;
    margin-bottom: 60px;
    display: grid;
    grid-template-columns: 24% 24% 24% 24%;
    column-gap: 20px;
}
@media screen and (min-width: 670px) and (max-width: 1040px) {
    .flag {
        grid-template-columns: 33.3% 33.3% 33.3%;
        /* margin: 0 auto; */
    }
}
@media screen and (min-width: 400px) and (max-width: 670px) {
    .flag {
        grid-template-columns: 50% 50%;
        /* margin: 0 auto; */
    }
}
@media screen and (min-width: 10px) and (max-width: 400px) {
    .flag {
        grid-template-columns: 100%;
        /* margin: 0 auto; */
    }
}
</style>
