<script>
import DataFetching from './components/DataFetching/DataFetching.vue';

export default {
    components: {
        'data-fetching': DataFetching
    }
};
</script>

<template>
    <data-fetching></data-fetching>
</template>

<style lang="scss">
html {
    height: 100vh;
    width: 100%;
    overflow: hidden;
}
body {
    height: 100vh;
    width: 100%;
    margin: 0;
    padding: 0;
    font-family: 'Open Sans', sans-serif;
}
</style>
