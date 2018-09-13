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
        padding-top: 150px;
    }
    @media only screen and (max-width: 900px) { 
        main {
        padding: 0;
        padding-top: 130px;
    }  
}

        @media only screen and (max-width: 782px) { 
        main {
        padding-top: 100px;
    }  
}

    @media only screen and (max-width: 600px) { 
        main {
        padding-top: 95px;
    }  
}

    @media only screen and (max-width: 424px) { 
        main {
        padding-top: 135px;
    }  
}
</style>