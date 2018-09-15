<template>
    <header>
        <div id="nav-top" class="ui small menu">
            <a href="http://google.com" class="ui image">
                <img id="logo-img" class="ui rounded image" src="./../../public/assets/logo.png">
            </a>

            <button class="ui button top-left-labels">
                <i class="user icon"></i>
                <a class="ui circular label" style="padding:4px 10px!important">3</a>
            </button>

            <button class="ui button top-left-labels">
                <i class="snowflake icon"></i>
                <a class="ui circular label" style="padding:4px 10px!important">1</a>
            </button>

            <button class="ui button top-left-labels">
                <i class="steam icon"></i>
                <a class="ui circular label" style="padding:4px 10px!important">2</a>
            </button>

            <p class="level">
                <span>Dashboard/My Project/</span><b>Persona {{name}}</b></p>
            
            <div class="right menu">
                <div class="ui dropdown item top-left-labels">
                    <i class="folder open icon"></i>
                    <span class="hide-text-on-mobile">My organization</span> <i class="dropdown icon"></i>

                    <div class="menu">
                        <a href="#/" class="item">N/A</a>
                        <a href="#/" class="item">N/A</a>
                        <a href="#/" class="item">N/A</a>
                    </div>
                </div>

                <button class="ui button top-left-labels">
                    <i class="user icon"></i>
                    <span class="hide-text-on-mobile">Jane Doe</span>
                </button>

                <button class="ui button top-left-labels close">
                    <i class="window close icon"></i>
                </button>
            </div>
        </div>

        <div id="nav-bottom">
            <div class="nav-left">
                    <i v-if="!nameEditMode" class="big user circle icon nav-bottom-icon"></i>
                    <h2 v-if="!nameEditMode">Persona <b>{{name || "Tess"}}</b></h2>
                    <input @change="gettyping" id="typeName" type="text" class="hidden" />
                    <a id="editName" @click="editClicked"><i class="large edit icon edit-name"></i></a>
                    <a id="saveName" @click="saveNameClicked" class="hidden"><i class="large check circle icon edit-name"></i></a>
            </div>

            <div class="nav-right">
                <div id="big-header-icons">
                    <i class="big save icon nav-bottom-right-icon"></i>
                    <span>Save persona</span>
                </div>

                <div id="big-header-icons">
                    <i class="big plus square icon nav-bottom-right-icon"></i>
                    <span>Add element</span>
                </div>

                <div id="big-header-icons">
                    <i class="big share icon nav-bottom-right-icon"></i>
                    <span>Export</span>
                </div>

                <div id="big-header-icons">
                    <i class="big copy icon nav-bottom-right-icon"></i>
                    <span>Duplicate</span>
                </div>

                <div id="big-header-icons">
                    <i class="big right arrow icon nav-bottom-right-icon"></i>
                    <span>Move</span>
                </div>

                <div id="big-header-icons">
                    <i class="big question circle right icon nav-bottom-right-icon"></i>
                    <span>Help</span>
                </div>

                <div id="big-header-icons">
                    <i class="big ellipsis horizontal right icon nav-bottom-right-icon"></i>
                    <span>More Actions</span>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
    export default {
        name: "Header",
        data() {
            return {
                nameEditMode: false,
                typing: "",
                name: ""
            }
        },
        methods: {
            toggleShow() {
                document.getElementById("typeName").classList.toggle("hidden");
                document.getElementById("editName").classList.toggle("hidden");
                document.getElementById("saveName").classList.toggle("hidden");
            },
            gettyping(e) {
                this.typing = e.target.value;
            },
            editClicked() {
                this.toggleShow();
                this.nameEditMode = true;
            },
            saveNameClicked() {
                this.name = this.typing;
                document.getElementById("typeName").value = "";
                this.nameEditMode = false;
                this.toggleShow();
            }
        },
        computed: {
            getInitials() {
                return this.name.slice(0,3);
            }
        }
    }
</script>

<style scoped>
.hidden {
    display: none;
}
.edit-name {
    margin-left: 8px;
    color: #B1B6B6;
    line-height: unset!important;
}

#big-header-icons {
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    padding-top: 3px;
    margin-left: 8px;
    min-width: 75px;
}

#big-header-icons:hover, .edit-name:hover {
    opacity: .7;
    cursor: pointer;
}

.nav-bottom-right-icon {
    color: #646E6E;
    margin-bottom: 2px;
}

#big-header-icons span {
    color: #646E6E;
    font-family: "Source Sans Pro";
    font-size: 13px;
}

#logo-img{
    width: 30px;
    height: 24px;
    border-radius: 2px;
    margin-right: 3px;
}

#nav-top > * {
    margin-left: 4px;
}

#nav-top{
    background-color: #3C4646;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    border-radius: 0px;
    margin-bottom: 0;
}

.top-left-labels {
    padding: 0 12px 0 8px;
    height: 24px;
    border-radius: 2px;
    background-color: #646E6E;
    color: #DCDCDC;
}

.top-left-labels i {
    padding-top: 2px;
    padding-left: 10px;
    font-size: 1.45em;
    vertical-align: bottom;
    color:white;
}
    
.top-left-labels a {
    min-width: 0!important;
    min-height: 0!important;
    background-color: #3C4646;
    color: white;
    font-weight: 600;
}

.level {
    text-transform: uppercase;
    font-weight:300;
    color: #B1B6B6;
    font-size: 12px;
    position: absolute;
    margin-left: 40%!important;
}

.level span{
    font-weight:300;
}

.close {
    padding: 0;
    color: #DCDCDC;
    padding: 2px 2px 0 0;
    display: flex;
    align-self: center;
    justify-self: center;
}

.dropdown {
    background-color: #646E6E!important;
    color: #DCDCDC!important;
}

.dropdown i {
    padding: 0;
}

.right > :nth-child(2) {
    margin-left: 6px;
    margin-right: 6px;
}

.level {
    position: absolute;
    margin-left:40%;
}

.dropdown {
    padding: 0 4px!important;
}

#nav-bottom {
    display: flex;
    padding: 1%;
    flex-wrap: wrap;
    flex-direction: row;
    background: linear-gradient(180deg, #FFFFFF 0%, #F0F0F0 100%);
}

.nav-left {
    display: flex;
    flex-flow: row nowrap;
    align-items: center;
}

.nav-left input[type="text"] {
    border-radius: 2px;
}
.nav-right {
    display: flex;
    margin-left: auto;
}

.nav-bottom-icon {
    opacity: .5;
}

h2 {
    color: #3C4646;	
    font-family: "Source Sans Pro";	
    font-size: 20px;	
    font-weight: 400;	
    line-height: 24px;
    margin: 0 10px;
}

header {
    position: fixed;
    width:100%;
    z-index: 1000;
}

@media only screen and (max-width: 965px) {
    .level {  margin-left: 35%!important;  }
    #big-header-icons { margin-left: 0;  min-width: 73px;  }
}

@media only screen and (max-width: 840px) {
    .right {  position: relative; display: block;  }
    .level {  display: none;  }
    .top-left-labels {  padding: 0 7px 0 5px;  }
    #nav-top > * {  margin-left: 2px;  }
}

@media only screen and (max-width: 810px) {
    #big-header-icons { margin-left: 0;  min-width: 47px;  }
    #big-header-icons span {  display:none }

}

@media only screen and (max-width: 618px) {
    #big-header-icons { margin-left: 0;  min-width: 44px;  }
    .hide-text-on-mobile {  font-size:0;  }
}

@media only screen and (max-width: 600px) {
    #big-header-icons {  min-width: 35px;  font-size: .8em;}
    #big-header-icons span {  display:none }
    .edit-name {  margin-left: 0px;  }
    h2 {  margin-left: 0px;  }
}
@media only screen and (max-width: 425px) {
    .right {  margin: 4px auto!important;  }
    #nav-top {  padding-top: 4px;  }
    .nav-left { margin: auto; }
    #logo-img {  margin-left: 75px;  }  
}

@media only screen and (max-width: 500px) {
    .nav-right {  margin: auto;  }
    .nav-bottom-right-icon {  margin: 0!important;  }
}

@media only screen and (max-width: 365px) {
    #logo-img {  margin-left: 48px;  }  
}

@media only screen and (max-width: 335px) {
    #logo-img {  margin-left: 25px;  }  
}

@media only screen and (max-width: 300px) {
    #logo-img {  margin-left: 20px;  }  
}
</style>
 