<template>
  <div>
    <div>
        <button @click="toggleBold" class="bold-btn-style">B</button>
        <button>/</button>
        <button @click="toggleUnderline" class="underline-btn-style">U</button>
    </div>
    
    <textarea name="" id="" cols="30" rows="10"></textarea>
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
    data() {
        return {
            bold: false,
            underline: false
        };
    },
    methods:{
        toggleBold(){
            this.bold = !this.bold;
            console.log(this.bold)
        },
        toggleUnderline(){
            this.underline = !this.underline;
        }
    
    }
};
</script>

<style scoped>
    .bold-btn-style {
        font-weight: bold;
    }
    .underline-btn-style {
        text-decoration: underline;
    }
</style>