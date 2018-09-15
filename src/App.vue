<template>
    <div @click="originalDivs">
        <Header @nameSaved="saveName" />
        <Body :personaName="personaName"/>
    </div>
</template>

<script>
    import axios from 'axios';
    import Header from "./components/Header";
    import Body from "./components/Body";

    export default {
        name: "App",
        data() {
            return {
                personaName: "Tessa"
            }
        },

        methods: {
            originalDivs(e) {
                if (document.getElementById('drag').contains(e.target)){
                    return;             
                } 

                else{
                    let newArray = document.getElementsByClassName("personal-info__el");

                    for (let i = 2; i < newArray.length; i++) {
                        newArray[i].style.transform = "scale(1)";
                    }
                }
            },

            saveName(temp){
                this.personaName = temp;
            },

            handleScroll() {
                let scrolling;

                window.clearTimeout(scrolling);
                scrolling = setTimeout(function() {
                    document.getElementById("header").style.boxShadow = "none";
                }, 200);

                document.getElementById("header").style.boxShadow = "2px 5px 8px #E7E7E7";
            }
        },

        mounted() {
            axios.get("https://private-anon-ff5c715acc-smaplypersonastest.apiary-mock.com/personas/personaId/fields")
                .then(response => console.log(response));
        },

        components: {
            Header,
            Body
        },

        created () {
            window.addEventListener('scroll', this.handleScroll, false);
        },

        destroyed () {
            window.removeEventListener('scroll', this.handleScroll, false);
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
    h4 {  font-size: 11px;  }
    p {  font-size: 14px;  }
}
</style>
