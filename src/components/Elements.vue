<template>
    <div id="add-element-options" class="add-element-options">
        <div class="el draggingEl" id="draggingEl1" draggable="true"> 
            <h1>Abc</h1>
            <p class="description">short text</p>
        </div>

        <div class="el draggingEl" id="draggingEl2" draggable="true">
            <p class="long-text-paragraph">Lorem ipsum dolor sit amet, consectetur adipiscing elit, 
                sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad 
                minim veniam.</p>
            <p class="description">long text</p>
        </div>

        <div class="el draggingEl" id="draggingEl3" draggable="true">
            <i class="fa far fa-3x fa-image el-img"></i>
            <p class="description">image</p>
        </div>

        <div class="el draggingEl" id="draggingEl4" draggable="true">
            <i class="images outline icon el-img"></i>
            <p class="description">image gallery</p>
        </div>

        <div class="el draggingEl" id="draggingEl5" draggable="true">
            <h1>123</h1>
            <p class="description">number</p>
        </div>
    </div>
</template>

<script>
let hoverBorder = "1px dashed #999";
let normalBorder = "1px solid white";
let draggingElement;
let newDiv;

//  THE EVENT LISTENERS

let handleDragStart = (e) => {
    draggingElement = e.target;
    e.target.style.border = hoverBorder;
    e.target.style.transform = "scale(0.9)";
    newDiv = document.getElementById("dragingEl6");
    newDiv.style.display = "initial";

}

let handleDragEnd = (e) => {
    if (newDiv.childNodes.length == 1)
        newDiv.style.display = "none";

    e.target.style.opacity= "1";
    e.target.style.border = normalBorder;
    draggingElement.style.transform = "scale(1)";
    console.log(newDiv.childNodes.length);
  
}

let handleDragOver = (e) => {
    if (e.preventDefault) e.preventDefault();
    if (e.stopPropagation) e.stopPropagation();
    e.target.style.opacity = "0.4";
    e.target.style.border = hoverBorder;
}

let handleDragEnter = (e) => {
    e.target.style.border = hoverBorder;
}

let handleDragLeave = (e) => {
    e.target.style.border = normalBorder;
    e.target.style.opacity= "1";
}

let handleDrop = (e) => {

    e.target.style.border = normalBorder;
    e.target.style.opacity= "1";
    if (e.target.id == draggingElement.id) 
        return;
    else {
        let dropEl;

        if (e.target.tagName == "P" || e.target.tagName == "H1") 
            dropEl = e.target.parentNode;
        else
            dropEl = e.target;
        
        let dragEl = draggingElement;
        let temp = dropEl;

        document.querySelector("#" + dropEl.id).appendChild(dragEl.childNodes[0]);
        document.querySelector("#" + dropEl.id).appendChild(dragEl.childNodes[0]);
 
        document.querySelector("#" + dragEl.id).appendChild(temp.childNodes[0]);
        document.querySelector("#" + dragEl.id).appendChild(temp.childNodes[0]);
    }
}

//  EVENT HANDLERS - end

const elements = () => {
    let els = new Array();
    const elementsNo = document.getElementsByClassName("draggingEl").length;

    for (let i = 1; i <= elementsNo ; i++) {
        els.push(document.querySelector(`#draggingEl${i}`));

        els[i-1].addEventListener("dragstart", handleDragStart, false);
        els[i-1].addEventListener("dragend", handleDragEnd, false);
        els[i-1].addEventListener("dragover", handleDragOver, false);
        els[i-1].addEventListener("dragenter", handleDragEnter, false);
        els[i-1].addEventListener("dragleave", handleDragLeave, false);
        els[i-1].addEventListener("drop", handleDrop, false);
    }
}

export default {
    name: "Elements",
    mounted() {
        elements.call(this)
    }
}
</script>

<style scoped>
.add-element-options {
    display: grid;
    grid-template-columns: 47.5% 47.5%;
    grid-column-gap: 5%;
    grid-row-gap: 15px;
    margin: 0 24px;
    padding: 20px 0;
}

.add-element-options > div {
    background:white;
}

.el {
    display: grid;
    grid-template-rows: 4.5rem 3rem;
    align-items: center;
    justify-items: center;
    border-radius: 2px;
    border:1px solid white;
    transition: transform 0.2s ease-out;
}

h1 {
    margin-bottom: 0px;
    align-self: end;
    color: #646E6E;
}
.fa-cog, .fa-trash {
    color: #DCDCDC;
    float: right;
    margin-top: 2px;
}

.fa-trash {
    display: none;
}

.fa-cog:hover, .fa-trash:hover {
    color: rgba(0,0,0,.6);
    cursor: pointer;
}
.description {
    color: #646E6E;	
    font-family: "Source Sans Pro";	
    font-size: 12px;	
    font-weight: bold;	
    line-height: 8px;	
    text-align: center;
    text-transform: uppercase;
    letter-spacing: .02em;
}

.long-text-paragraph {
    color: #646E6E;	
    font-size: 9px;
    font-weight: 200;
    line-height: 8px;
    text-align: center;
    align-self: end;
    padding: 0 9px;
}

.el-img {
    align-self: end;
    color: #646E6E;
}

.outline {
    font-size:40px;
    height:30px;
    margin: 0;
}

#dragingEl6 {
    border: 1px dashed #9CDBFB;
    border-radius: 2px;
    background-color: #F0F8FC;
    display:flex;
    justify-content: center;
    align-items: center;
    display: none;
}

#dragingEl6 p {
    color: #646E6E;
    font-size: 14px;
}

@media only screen and (max-width: 782px) { 
    .long-text-paragraph {  color: #646E6E; font-size: 8px; line-height: 7px; padding: 0 7px;  }
}
</style>
