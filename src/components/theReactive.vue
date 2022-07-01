<template>
  <div class="customStyle">
    The Reactive <br>
    Boolean : {{testDataProps}} <br>
    ID : {{dataProps.id}}  - {{dataIdProps.id}}
    <br>
    Name : {{dataProps.name}} - {{dataIdProps.name}}
    <br>
    Description : {{dataProps.description}} - {{dataIdProps.desc}}
    <br>
    <button @click="onChange">Change Value</button>
  </div>
</template>

<script>
import { reactive,toRef,watch, toRefs, ref, watchEffect } from 'vue';
export default {
  props: {
    data: {
      type : Object,
      default : {}
    },
    id: {
      type : Number,
      default : 0
    },
    test:{
      type: Boolean,
      default: false
    }
  },
  setup(props) {
    const testDataProps = ref(props.test);
    const dataIdProps = ref(props.id);
    console.log(dataIdProps)
    const dataProps = reactive(props.data);
    // const {data: dataProps} = toRefs(props, "data");
    const onChange = () => {
      dataIdProps.value.id = dataIdProps.value.id + 1;
      dataProps.id += 1;
      testDataProps.value = !testDataProps.value;
    }
    watch(dataIdProps , (value) => {
      console.log(value);
    },{deep : true})
    // watch(dataProps , (curVal,oldVal) => {
    //   console.log(curVal)
    // },{deep:true})
    return{
      dataProps,
      onChange,
      dataIdProps,
      testDataProps
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