<template>
    <div class="home">
        <Header />
        <Flag />
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
};
</script>
