<template>
    <button class="style-btn" @click="handleClickBtn">
        <span>{{label}}</span>
    </button>
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
        animate: Boolean,
        label: String
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
        this.$el.style.setProperty("--default-color", this.default ? "black" : "white")
        this.$el.style.setProperty("--circle", this.circle ? "5px" : "0")
        console.log(this.animate)
        this.$el.style.setProperty("--animate-rotate", this.animate ? "rotate(15deg)" : "none")
        this.$el.style.setProperty("--animate-margin", this.animate ? "1rem" : "none")

        //primary
        this.$el.style.setProperty("--background-color", this.primary ? "#bde7fc" : "none")
        this.$el.style.setProperty("--background-color", this.success ? "#ddfad7" : "none")
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
    border: 1px solid rgb(138, 138 ,138);
    border-radius: var(--circle);
    font-family: system-ui;
    transition: .5s;
    background-color: var(--background-color);
}
.style-btn:hover::before {
  transform: scale(1.1);
  box-shadow: 0 0 15px var(--default-color);
}
.style-btn:hover{
    transform: var(--animate-rotate);
    margin: var(--animate-margin);
    color: var(--default-color);
    box-shadow: 0 0 5px var(--default-color);
    text-shadow: 0 0 5px var(--color-button);
    background-color: var(--color-button);
}
</style>