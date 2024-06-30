<template>
  <div>
    <div>
      <button @click="toggleBold" class="bold-btn-style">B</button>
      <button @click="toggleUnderline" class="underline-btn-style">U</button>
      <!-- New button for changing text color -->
      <button @click="changeTextColor('#ff0000')" class="color-btn-style">Color</button>
    </div>
    <div contenteditable="true" ref="textEditor" class="text-editor"></div>
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
  methods: {
    toggleBold() {
      document.execCommand('bold', false, null);
    },
    toggleUnderline() {
      document.execCommand('underline', false, null);
    },
    // Method to change the text color
    changeTextColor(color) {
      document.execCommand('foreColor', false, color);
    }
  }
};
</script>

<style>
.text-editor {
  border: 1px solid #ccc;
  min-height: 100px;
  margin-top: 10px;
  padding: 5px;
}
.text-editor:focus {
  outline: none;
}
/* Add your button styling here */
.bold-btn-style, .underline-btn-style, .color-btn-style {
  margin-right: 5px;
}
</style>