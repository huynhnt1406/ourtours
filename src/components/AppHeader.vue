<template>
    <div class="header">
        <h3>Our Tours</h3>
        <button @click="$emit('open-add-tour')">Add</button>
        <button @click="$emit('close-add-tour')">Close</button>
    </div>
</template>

<script>
export default {

}
</script>

<style>
button{
  margin:10px;
  padding:6px;
  background-color: transparent;
  border:none;
  border-radius: 20px;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.5);
  font-size: smaller;
  outline: none;
}
.header{
  height: 40px;
  background-color: white;
  display:flex;
  align-items: center;
  padding:10px;
  font-family: "Poppins",sans-serif;
  box-shadow: 0 2px 2px rgba(0,0,0,.5);
  letter-spacing: 5px;
}
</style>