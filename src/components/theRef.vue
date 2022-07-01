<template>
  <div class="customStyle">
    The Ref <br> 
    ID : {{dataProps.id}}
    <br>
    Name : {{dataProps.name}}
    <br>
    Description : {{dataProps.description}}
    <br>
    <button @click="onChange">Change Value</button>
  </div>
</template>

<script>
import { ref,watch } from 'vue';
export default {
  props: {
    data: {
      type : Object,
      default : {}
    }
  },
  setup(props) {
    const dataProps = ref(props.data);
    const onChange = () => {
      dataProps.value.id += 1;
    }

    watch(dataProps , (curVal,oldVal) => {
      console.log(curVal)
    },{deep:true})
    return{
      dataProps,
      onChange
    }
  },
  
};
</script>

<style scoped>
.customStyle{
  width: 100%;
  font-size: 24px;
  text-align: center;
}
</style>