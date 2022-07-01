<template>
  <main>
    <!-- <div
      style="
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
      "
    >
      <div class="ui label big">
        ID: {{ user.id }} <br />
        Name: {{ user.name }}
      </div>
    </div> -->
    <TheRef :data="dataRef" />
    <br>
    <TheReactive :data="dataReactive.data" :id="id" :test="test"/>
    <br>
    <br>
    <to-ref :data="dataRef"   />

    <br>
    <br>
    {{test}}
  </main>
</template>

<script>
import { reactive, toRefs, watch, ref, isProxy } from "vue";
import TheRef from '../components/theRef.vue';
import TheReactive from '../components/theReactive.vue';
import ToRef from '../components/toRef.vue';
export default {
  components:{
    TheRef,
    TheReactive,
    ToRef
  },
  setup() {
    const test = ref(false);
    const id = ref({id : 1 , name : "Hung", desc: "q1321321"});
    const dataRef = reactive({
        id : 1,
        name : 'The Ref',
        description : 'Test The Ref'
      })
    const dataReactive = reactive({
      data : {
        id : 1,
        name : 'The Reactive',
        description : 'Test The Reactive'
      }
    })
    // let user = reactive({ id: 0, name: "Joe" });

    // setTimeout(() => {
    //    user = {
    //     id: 20,
    //     name: "Raja",
    //   };
    // }, 2000);

    // watch(dataRef ,(value) => {
    //   console.log(value);
    // },{deep : true})

    // watch(dataReactive ,(value) => {
    //   console.log(value);
    // },{deep : true})
    watch(id , (value) => {
      console.log(value)
    },{deep : true})
    // return toRefs(dataReactive);

    return {
      dataRef,
      dataReactive,
      id,
      test
    };
  },
};
</script>