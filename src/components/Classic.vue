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
                <p>Tessa <span>(Tes)</span></p>
            </div>

            <div id="short-name" class="personal-info__el">                
                <h4>Short name</h4>
                <p>Tes</p>
            </div>
        </div>

        <div id="drag" class="elements-joined">
            <div @click="handleEditFileds" id="image" class="personal-info__el medium">
                <h4>Image</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                <div id="photo2">
                    <img 
                        id="photo-img" 
                        class="ui fluid image" 
                        src="./../../public/assets/image.png" 
                        alt="photo-placeholder" />
                </div>
            </div>
        
            <div @click="handleEditFileds(this)" id="occupation" class="personal-info__el shorter-div draggable">                
                <h4>Occupation</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                <p>Researcher</p>
            </div>

            <div @click="handleEditFileds" id="dragingEl6" class="personal-info__el shorter-div draggable">                
            <p><i>Insert element here</i></p>
                </div>

            <div @click="handleEditFileds" id="nationality" class="personal-info__el shorter-div draggable">                
                <h4>nationality</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                <p>French</p>
            </div>

            <div @click="handleEditFileds" id="maritialStatus" class="personal-info__el shorter-div draggable">                
                <h4>Mariatal Status</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                <p>---</p>
            </div>

            <div @click="handleEditFileds" id="Age" class="personal-info__el shorter-div draggable">
                <h4>Age</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                <p>28</p>
            </div>

            <div @click="handleEditFileds" id="quote" class="personal-info__el rowsNo2 draggable">                
                <h4>Quote</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
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

            <div @click="handleEditFileds" id="gender" class="personal-info__el draggable">
                <h4>Gender</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                <p>Not defined</p>
            </div>

            <div @click="handleEditFileds" id="mood-images" class="personal-info__el imgs">
                <h4>Mood Images</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>

                <div class="flexed-photos">
                    <img src="./../../public/assets/placeholder.jpeg">
                    <img src="./../../public/assets/image.png">
                    <img src="./../../public/assets/image.png">
                </div>
            </div>

            <div @click="handleEditFileds" id="description" class="personal-info__el occupation draggable">
                <h4>Description</h4><i class="fa fas fa-cog"></i><i class="fa fas fa-trash"></i>
                
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

export default {
    name: "Classic",
    methods: {
        handleDragOver(e) {
            if (e.preventDefault) e.preventDefault();
            if (e.stopPropagation) e.stopPropagation();
        },
        handleDrop(e) {
            let newel = document.querySelector("#dragingEl6");
            newel.innerHTML = "";
            newel.style.background = "white";
            newel.style.border = "none";

            newel.insertAdjacentHTML('afterBegin', ' <h4>Gender</h4><i class="fa fas fa-cog"></i><p>Not defined</p></div>');
          document.getElementById("mood-images").style.gridRow = "5";
          
            document.getElementById("description").style.gridRow = "5";
        },
        handleEditFileds(e) {
            let testni;
            console.log(e.target);
                    
            if (e.target.className == "personal-info__el")
                testni = e.target;

            else {
                testni = e.target.parentNode;

            while (testni.nodeName != "DIV") {
                testni = testni.parentNode;
            }
        }


             testni = testni.getAttribute("id");
            let niz = document.getElementsByClassName("fa-cog");
             let broj = document.getElementsByClassName("fa-cog").length;
             console.log(testni);
             console.log(broj);

             for (let i = 0; i < broj; i++) {
                    console.log(niz[i].getAttribute("id"));
        }
    }
            
           /* testni.style.display="none";*/
    },

    mounted() {
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

.fa-cog:hover {
    color: rgba(0,0,0,.7);

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

.rowsNo2 {
    grid-row: span 2;
}

.medium {
    grid-row: span 3;
    grid-column: span 1;
}

.elements-joined {
    border-radius: 0 0 2px 2px;	
    background-color: #F0F0F0;
    grid-template-rows: repeat(13, 100%);;
    display: grid;
    padding: 15px;
    grid-column-gap: 15px;
    grid-row-gap: 15px;
    grid-template-columns: 33% auto;
}

.fa-cog {
    color: #DCDCDC;
    float: right;
    margin-top: 2px;
}

#photo2 {
    margin-top: 7px;
}

#ocupation {
    align-self: start;
}

.shorter-div {
    height: 61px;
}

.elements-joined:after {
    content: "";
    display: table;
    clear: both;
    overflow:hidden;
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
