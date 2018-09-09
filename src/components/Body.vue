<template>
    <main>
        <Classic />
        <AddElement />
    </main>
</template>
<script>
    import Classic from './Classic';
    import AddElement from './AddElement';

    export default {
        name: "Body",
        components: {
            Classic,
            AddElement
        }
    }
</script>

<style scoped>
    main {
        background: #646E6E;
        padding-left: 11%;
        padding-top: 3%;
    }
</style>