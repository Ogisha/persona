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
                <p>Tes</p></div>
        </div>
        <div class="elements-joined">
            <div id="image" class="personal-info__el">
                <h4>Image</h4><i class="fa fas fa-cog"></i>
                <div id="photo2">
                        <img 
                            id="photo-img" 
                            class="ui fluid image" 
                            src="./../../public/assets/image.png" 
                            alt="photo-placeholder" />
                    </div>
            </div>
        
                    <div id="occupation" class="personal-info__el shorter-div">                
                        <h4>Occupation</h4><i class="fa fas fa-cog"></i>
                        <p>Researcher</p></div>
                        <div id="Age" class="personal-info__el shorter-div">
                                <h4>Age</h4><i class="fa fas fa-cog"></i>
                                <p>28</p>
                            </div>
                
                            <div id="nationality" class="personal-info__el shorter-div">                
                                <h4>nationality</h4><i class="fa fas fa-cog"></i>
                                <p>French</p></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Classic"
    }
</script>

<style scoped>

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

    .elements-joined {
        border-radius: 0 0 2px 2px;	
        background-color: #F0F0F0;
        grid-template-rows: auto;
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
        .personal-info {
            grid-template-columns: 56px minmax(75px, auto);
            padding: 10px;
            grid-column-gap: 10px;
        }

        .personal-info__el span{
            display:initial;
        }


    
        #short-name {
            display: none;
        }
    }
</style>
