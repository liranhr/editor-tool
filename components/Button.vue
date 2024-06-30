<template>
    <button class="style-btn" @click="handleClickBtn">{{textButton}}</button>
</template>

<script>
export default {
    data(){
        return{
            defaultColor: "white",
            primaryColor: "#0077b6",
            successColor: "#99d98c",
            default: true
        }
    },
    props:{
        primary: Boolean,
        success: Boolean,
        circle: Boolean,
        textButton:{
            type: String,
            default: ""
        }
    },
    computed:{
        buttonColor(){
            console.log(this.primary, this.success)
            if(this.primary){
                this.default = false;
                return this.primaryColor;
            } 
            if(this.success){
                this.default = false;
                return this.successColor;
            } 
            return this.defaultColor;
        }
    },
    mounted(){
        this.$el.style.setProperty("--color-button", this.buttonColor);
        this.$el.style.setProperty("--default", this.default ? "black" : "white")
        this.$el.style.setProperty("--circle", this.circle ? "5px" : "0")
    },
    methods:{
        handleClickBtn(){
            console.log("Button clicked!")
        }
    }
}
</script>

<style>
.style-btn{
    border-color: transparent;
    font-weight: 600;
    border-radius: var(--circle);
    font-family: system-ui;
    transition: .5s;
}
.style-btn:hover::before {
  transform: scale(1.1);
  box-shadow: 0 0 15px var(--default);
}
.style-btn:hover{
    color: var(--default);
    box-shadow: 0 0 5px var(--default);
    text-shadow: 0 0 5px var(--color-button);
    background-color: var(--color-button);
}
</style>