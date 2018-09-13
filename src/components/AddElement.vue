<template>
    <div id="add-element-container">
        <div id="add-top">
            <h3>Add element</h3>
            <button>&#10799</button>
        </div>

        <div id="add-main">
            <h2 id="add-header">Add element to persona</h2>
            <p>Click or drag & drop one of the element types below to add it to the persona.<br />
                Click on the <span><i class="fa fas fa-cog"></i></span> icon of the each element to edit it's settings.<br />
                You can reorder the elements by dragging them.
            </p>
            <Elements />
        </div>
    </div>
</template>

<script>

import Elements from './Elements';

export default {
    name: "AddElement",
    components: {
        Elements
    }
}
</script>

<style>
#add-element-container {
    width: 350px;
    background: white;
    position: fixed;
    height: 78vh;
    overflow-y: scroll;
    top: 130px;
    right: 0;
}

h3 {
    color: #646E6E;	
    font-size: 12px;	
    font-weight: 600;	
    letter-spacing: 0.8px;	
    line-height: 13px;
    text-transform: uppercase;
    margin: 0px 0px 0px 24px;
}

#add-top {
    display: grid;
    grid-template-columns: auto 10%;
    align-items: center;
    border-radius: 2px 0 0 0;	
    background-color: #DCDCDC;
}

#add-close {	
    border-radius: 1px;	
    color: #646E6E;
    font-weight: 300;
}

#add-top button {
    border-top:none;
    border-right: none;
    border-bottom: none;
    font-size: 22px;
    padding: 20% 25% 20% 25%;
    background-color: #DCDCDC;
    color:#646E6E;
    border-left: 1px solid white;
    font-family: serif;
}

#add-main {
    background-color: #F0F0F0;
    display: grid;
    grid-template-rows: auto;
}

p {
    margin-bottom: 0;
}

#add-main > p {
    background-color: #F0F8FC;	
    box-shadow: inset 0 1px 3px 0 rgba(0,0,0,0.1);
    color: #646E6E;	
    font-family: "Source Sans Pro";	
    font-size: 14px;	
    font-style: italic;	
    line-height: 22px;
    padding: 4.5% 24px;
}

#add-header {
    color: #3C4646;	
    font-size: 24px;	
    font-weight: 100;	
    line-height: 31px;
    font-family: "Source Sans Pro";
    margin: 0px!important;
    padding: 20px 0 20px 24px;
}

p > span {
    margin: 0 3px;
    color: #646E6E;
}

@media only screen and (max-width: 782px) { 
    #add-element-container {  width: 280px;  top: 100px;  right: 12px  }
}

@media only screen and (max-width: 635px) { 
    #add-element-container {  width: 265px;  margin-left: 2%;  top: 100px;  right: 12px  }
}

@media only screen and (max-width: 600px) { 
    #add-element-container {  width: 93.5vw;  margin-left: 2%;  position: relative;  top: 20px;  }
}

@media only screen and (max-width: 424px) { 
    #add-element-container {  width: 92vw;  margin-left: 3%;  top: 10px;  }
}
</style>