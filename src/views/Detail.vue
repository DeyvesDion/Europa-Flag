<template>
    <div>
        <div>
            <h1>{{ getFlag }}</h1>
        </div>
    </div>
</template>

<script>
export default {
    name: "Detail",
    data() {
        return {
            getFlag: this.$route.params.pN,
        };
    },
};
</script>

<style scoped></style>
