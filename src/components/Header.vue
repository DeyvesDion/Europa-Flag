<template>
    <div class="header">
        <div class="header__flag"></div>

        <div class="header__title">
            <div class="search__wrapper">
                <form @submit.prevent="GetPaysBySearch(paysName)">
                    <input
                        v-model="paysName"
                        class="search__bar"
                        type="search"
                        id=""
                        placeholder="Chercher un pays d'Europe"
                    />
                </form>
            </div>
            <h1 class="title">Europa flag</h1>
        </div>
    </div>
</template>

<script>
export default {
    name: "Header",
    // props: ["pays"],
    data() {
        return {
            paysName: "",
        };
    },
    methods: {
        GetPaysBySearch(paysName) {
            this.$router.push({
                name: "Detail",
                params: { Np: paysName },
            });
            console.log(this.paysName);
            this.paysName = "";
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 200px;
}
.header__flag {
    height: 70vh;
    width: 100%;
    background-image: url("../assets/UE.jpg");
}
.header__title {
    height: 170px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 60vh;
    width: 70%;
    /* background-color: red; */
    box-shadow: rgba(17, 17, 26, 0.1) 0px 8px 24px,
        rgba(17, 17, 26, 0.1) 0px 16px 56px, rgba(17, 17, 26, 0.1) 0px 24px 80px;
}
.header__title:hover {
    cursor: pointer;
    transform: scale(1.01);
}
.title {
    color: #2b2c92;
    font-size: 45px;
}
.search__bar {
    border: 3px solid #2b2c92;
    border-radius: 50px;
    width: 400px;
    height: 50px;
}
.search__bar:focus {
    outline: none;
}

@media screen and (max-width: 380px) {
    .header {
        display: flex;
        justify-content: center;
        margin-bottom: 0px;
    }
    .header__flag {
        display: none;
        /* margin: 0 auto; */
    }
    .header__title {
        margin-top: 12px;
        position: relative;
        top: 0;
    }
    .title {
        font-size: 40px;
    }
}
</style>
