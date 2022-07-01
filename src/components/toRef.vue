<template>
  <div class="customStyle">
    The To Ref <br>
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
import { toRef,watch, toRefs, ref, reactive } from 'vue';
export default {
  props: {
    data: {
      type : Object,
      default : {}
    },
    id: {
      type : Number,
      default : 0
    }
  },
  setup(props) {
    // const dataProps = toRef(props,"data");
    // const sourceObject = reactive(props.data);
    const dataProps = toRefs(props).data;
    

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