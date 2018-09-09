<template>

    <div id="add-element-options" class="add-element-options">
        <div class="el nonempty" dragable="true"> 
            <h1>Abc</h1>
            <p class="description">short text</p>
        </div>

        <div class="el nonempty">
            
                <p class="long-text-paragraph">Lorem ipsum dolor sit amet, consectetur adipiscing elit, 
                    sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad 
                    minim veniam.</p>
                <p class="description">long text</p>

        </div>

        <div class="el nonempty">
            <i class="fa far fa-3x fa-image el-img"></i>
            <p class="description">image</p>
        </div>

        <div class="el nonempty">
            <i class="images outline icon el-img"></i>
            <p class="description">image gallery</p>
        </div>

        <div class="el nonempty">
            <h1>123</h1>
            <p class="description">number</p>
        </div>
    </div>
</template>

<script>

    export default {
        name: "Elements"
}
</script>

<style scoped>
    
    .add-element-options {
        padding: 20px 0;
    }

    h1 {
        margin-bottom: 0px;
        align-self: end;
        color: #646E6E;
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
        line-height: 10px;
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

    .empty {

    }

</style>
