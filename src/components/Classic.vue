<template>
    <div class="main-content">
        <div class="personal-info">
            <div id="photo">
                <img 
                    id="photo-img" 
                    class="ui fluid image" 
                    src="./../../public/assets/photo.png" 
                    alt="photo-placeholder" />
            </div>

            <div id="persona-name" class="personal-info__el">
                <h4>Persona name</h4>
                <p>{{personaName}} <span>({{getInitials}})</span></p>
            </div>

            <div id="short-name" class="personal-info__el">                
                <h4>Short name</h4>
                <p>{{getInitials}}</p>
            </div>
        </div>

        <div id="drag" class="elements-joined">
            <div @click="handleEditFields" id="image" class="personal-info__el medium">
                <h4>Image</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <section id="photo2">
                    <img 
                        id="photo-img" 
                        class="ui fluid image" 
                        src="./../../public/assets/image.png" 
                        alt="photo-placeholder" />
                </section>
            </div>
        
            <div @click="handleEditFields" id="occupation" class="personal-info__el draggable">                
                <h4>Occupation</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <p>Researcher</p>
            </div>

            <div @click="handleEditFields" id="dragingEl6" class="personal-info__el draggable">                
                <p>
                    <i>Insert element here</i>
                </p>
            </div>

            <div @click="handleEditFields" id="nationality" class="personal-info__el draggable">                
                <h4>nationality</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <p>French</p>
            </div>

            <div @click="handleEditFields" id="maritalStatus" class="personal-info__el draggable">                
                <h4>Mariatal Status</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <p>---</p>
            </div>

            <div @click="handleEditFields" id="Age" class="personal-info__el draggable">
                <h4>Age</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <p>28</p>
            </div>

            <div @click="handleEditFields" id="quote" class="personal-info__el draggable">                
                <h4>Quote</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <section class="text-formating">
                    <section class="ui icon buttons">
                        <button class="ui basic button"><i class="bold icon"></i></button>
                        <button class="ui basic button"><i class="italic icon"></i></button>
                        <button class="ui basic button"><i class="underline icon"></i></button>
                        <button class="ui basic button"><i class="align left icon"></i></button>
                        <button class="ui basic button"><i class="align center icon"></i></button>
                        <button class="ui basic button"><i class="align right icon"></i></button>
                        <button class="ui basic button"><i class="align justify icon"></i></button>
                    </section>
                </section>
                <p>"Life may not be the party  we hoped for, but while we're here, we should dance."</p>
            </div>

            <div @click="handleEditFields" id="gender" class="personal-info__el draggable">
                <h4>Gender</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                <p>Not defined</p>
            </div>

            <div @click="handleEditFields" id="mood-images" class="personal-info__el imgs">
                <h4>Mood Images</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>

                <section class="flexed-photos">
                    <img src="./../../public/assets/placeholder.jpeg">
                    <img src="./../../public/assets/image.png">
                    <img src="./../../public/assets/image.png">
                </section>
            </div>

            <div @click="handleEditFields" id="description" class="personal-info__el occupation draggable">
                <h4>Description</h4>
                <i class="fa fas fa-cog"></i>
                <i @click="trashTheDiv" class="fa fas fa-trash"></i>
                
                <section class="text-formating">
                    <section class="ui icon buttons">
                        <button class="ui basic button"><i class="bold icon"></i></button>
                        <button class="ui basic button"><i class="italic icon"></i></button>
                        <button class="ui basic button"><i class="underline icon"></i></button>
                        <button class="ui basic button"><i class="align left icon"></i></button>
                        <button class="ui basic button"><i class="align center icon"></i></button>
                        <button class="ui basic button"><i class="align right icon"></i></button>
                        <button class="ui basic button"><i class="align justify icon"></i></button>
                    </section>
                </section>

                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis congue efficitur rutrum. 
                    Aliquam viverra condimentum molestie. Duis id ipsum imperdiet, vehicula justo eu, 
                    elementum metus.</p>
                <p>Suspendisse est nibh, consectetur maximus congue id, mattis vel nunc. Phasellus 
                    sollicitudin sed urna eu blandit. Phasellus sit amet ante sed lorem finibus efficitur. 
                    </p>
                <p><b>Phasellus luctus vitae urna at lobortis. Praesent malesuada sit amet nibh et 
                    faucibus.</b></p>
            </div>
        </div>
    </div>
</template>

<script>
    import Sortable from 'sortablejs';
    import axios from 'axios';

    export default {
        name: "Classic",
        data() {
            return {
                toRemove: ""
            }
        },

        props: {
            personaName: String
        },

        methods: {
            adjustStyles(a, b) {
                a.addEventListener("mouseover", function() {
                    this.style.color = "rgba(0,0,0,.6)";
                    this.style.cursor = "pointer";
                });

                a.addEventListener("mouseout", function() {
                    this.style.color = "#DCDCDC";
                });

                b.addEventListener("mouseover", function() {
                    this.style.color = "rgba(0,0,0,.6)";
                    this.style.cursor = "pointer";
                });

                b.addEventListener("mouseout", function() {
                    this.style.color = "#DCDCDC";
                });
            },

            handleDragOver(e) {
                if (e.preventDefault) e.preventDefault();
                if (e.stopPropagation) e.stopPropagation();
            },

            handleDrop(e) {
                let newel = document.querySelector("#dragingEl6");
                newel.addEventListener("click", this.handleEditFields, false);
                newel.innerHTML = "";
                newel.style.background = "white";
                newel.style.border = "none";

                let template = `
                            <h4>Testing</h4>
                            <i id="dinSettings" class='fa fas fa-cog'></i>
                            <i id="dinTrash" @click="trashTheDiv" class='fa fas fa-trash' style='display:none; color:#DCDCDC; float: right;margin-top: 2px;'></i>
                            <p>Not defined</p>
                        `;

                newel.insertAdjacentHTML('afterBegin', template);

                let dinSettings = document.getElementById("dinSettings");
                let dinTrash = document.getElementById("dinTrash");
                this.adjustStyles(dinSettings, dinTrash);

                newel.children[2].addEventListener("click", function(){
                    newel.remove();
                });
            },

            handleEditFields(e) {
                if (e.target.className.slice(0,17) == "personal-info__el") 
                    this.toRemove = e.target;

                else {
                    this.toRemove = e.target.parentNode;
                    while (this.toRemove.nodeName != "DIV") {
                        this.toRemove = this.toRemove.parentNode;
                    }
                }

                let newArray = document.getElementsByClassName("personal-info__el");

                for (let i = 2; i < newArray.length; i++) {
                    if (this.toRemove.id == newArray[i].id) {
                        newArray[i].children[1].style.display = "none";
                        newArray[i].children[2].style.display = "initial";
                        newArray[i].style.transform = "scale(1.05)";
                        newArray[i].style.transition = "transform 0.2s ease-in";

                    }

                    else {
                        if (newArray[i].children[1])
                            newArray[i].children[1].style.display = "initial";
                        if (newArray[i].children[2])
                            newArray[i].children[2].style.display = "none";

                        newArray[i].style.transform = "scale(1)";
                        newArray[i].style.transition = "transform 0.2s ease-out";
                    }
                }
            },

            trashTheDiv(e) {
                setTimeout(() => {
                    e.target.parentNode.remove();
                },100);
                clearTimeout();
            }
        },

        computed: {
            getInitials() {
                return this.personaName.slice(0,3);
            }
        },

        mounted() {
            axios.get("https://private-anon-ff5c715acc-smaplypersonastest.apiary-mock.com/personas/personaId/columns")
                .then(response => console.log(response));

            const el = document.getElementById('drag');
            
            Sortable.create(el, {
                sort: true,
                disabled: false,
                animation: 150,
                draggable: ".draggable"
            })

            const element = document.getElementById("dragingEl6");

            element.addEventListener("dragover", this.handleDragOver, false);
            element.addEventListener("drop", this.handleDrop, false);
        }
    }
</script>

<style scoped>
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

#dragingEl6 {
    border: 1px dashed #9CDBFB;
    border-radius: 2px;
    background-color: #F0F8FC;
    display:flex;
    justify-content: center;
    align-items: center;
    display: none;
    grid-row: span 1;
    grid-column: span 2;
}

#dragingEl6 p {
    color: #646E6E;
    font-size: 14px;
}

#mood-images {
    grid-row: span 5;
    grid-column-start: 1;
    grid-column: span 1;
}

.buttons {
    display: initial;
}

#description p {
    margin-bottom: 12px;
}

.flexed-photos {
    display: flex;
    flex-direction: column;
}

.flexed-photos img {
    margin-top: 10px;
}

.flexed-photos img:first-child{
    height: 65px;
}

.flexed-photos img:first-child:hover{
    border-radius: 4px;
    border: 1px dashed #666;
    transform: scale(0.95);
}

.main-content {
    width: 55%;
}

.personal-info {
    display: grid;
    grid-template-columns: 56px minmax(75px, 70%) 95px;
    grid-template-rows: 56px;
    grid-column-gap: 15px;
    padding: 15px;
    border-radius: 2px 2px 0 0;	
    background-color: #DCDCDC;
}

#description {
    grid-column-start: 2;
    grid-column: span 2;
}

.personal-info__el {
    padding: 10px;
    background: white;
}

.personal-info__el span{
    display: none;
}

#photo {
    background-color: #F05A50;	
    background: linear-gradient(180deg, rgba(255,255,255,0.2) 0%, rgba(240,240,240,0) 100%);
}

#photo-img {
    max-height: 100%;
}

.text-formating {
    padding: 5px 0;
    opacity: .6;
}

#image {
    grid-row: span 3;
    grid-column: span 1;
}

#occupation, #nationality, #maritalStatus {
    grid-row: span 1;
    grid-column: span 2;
    grid-column-start: 2;
    grid-column-end: 4;
}

#age {
    grid-row: span 1;
    grid-column: span 1;
    grid-column-start: 1;
}

#quote {
    grid-row: span 3;
    grid-column: span 2;
    grid-column-start: 2;
    grid-column-end: 4;
}

.elements-joined {
    border-radius: 0 0 2px 2px;	
    background-color: #F0F0F0;
    grid-template-rows: repeat(13, 100%);;
    display: grid;
    padding: 15px;
    grid-column-gap: 15px;
    grid-row-gap: 15px;
    grid-template-columns: 1fr 1fr 1fr;
    grid-auto-flow: dense;
}

.fa-cog {
    color: #DCDCDC;
    float: right;
    margin-top: 2px;
}

#photo2 {
    margin-top: 7px;
}

@media only screen and (max-width: 670px) {
    .personal-info {  grid-template-columns: 56px minmax(75px, auto); padding: 10px; grid-column-gap: 10px;  }
    .personal-info__el span {  display:initial;  }
    #short-name {  display: none;  }
}

@media only screen and (max-width: 900px) { 
    .main-content {  width: 52vw; margin-left: 1%;  }
}

@media only screen and (max-width: 782px) { 
    .main-content {  margin-left: 1%;  }
}

@media only screen and (max-width: 730px) {  
    .main-content {  margin-left: 1%; width: 50vw;  }
}

@media only screen and (max-width: 600px) { 
    .main-content {  width: 93.5vw; margin-left: 2%;  }
}

@media only screen and (max-width: 424px) { 
    .main-content {  width: 92vw; margin-left: 3%;  }
}
</style>
