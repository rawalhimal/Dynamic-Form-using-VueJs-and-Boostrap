<template>
<div>
  Debug of Formdata:{{formData}}

  <form  >
    <template v-for="({type, name, label}) in fields">
      <label 
      :for="name"
      :key="`label-${name}`"
      >{{label}}</label>

      <input v-if="type !== 'textarea'" 
      :type="type"
       :name="name" 
      :placeholder="label" 
      v-model="formData[name]"
      :key="`field-${label}`" />

      <textarea v-if="type === 'textarea'" 
      :name="name" 
      :placeholder="label" 
      :id="name" 
      v-model="formData[name]"
      :key="`field-textarea-${label}`">
    </textarea>

    </template>

    <input type="submit" value="Add" />
  </form>

</div>
</template>
<script>
const fields = require('./fields.json').fields;
export default {
  data: () => ({
    formData: {},
    fields
  })
};
</script>
<style scoped>
input {
  width:100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
textarea{
    width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
</style>
