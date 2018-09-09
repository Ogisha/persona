<template>
    <div>
        <Header />
       <!-- <Body />-->
    </div>
</template>

<script>
    import Header from "./components/Header";
    import Body from "./components/Body";

    export default {
        name: "App",
        components: {
            Header,
            Body
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        font-family: "Source Sans Pro"!important;
    }

    h4 {
        color: #B1B6B6;	
        font-family: "Source Sans Pro";	
        font-size: 12px;	
        font-weight: bold;	
        line-height: 15px;
        text-transform: uppercase;
        display: inline;
    }

    p {	
        color: #3C4646;	
        font-family: "Source Sans Pro";	
        font-size: 16px;	
        line-height: 22px;
    }

    @media only screen and (max-width: 600px) {
        h4 {
            font-size: 11px;
        }

        p {
            font-size: 14px;
        }
    }
</style>

