<template>
  <div
    style="
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    "
  >
    <div class="ui label big">
      ID: {{ state.user.id }} <br />
      Name: {{ state.user.name }}
    </div>
    {{count}}
    <button @click="test" style="margin-bottom : 80px">TestWatchAndWatchEffect</button>
  </div>
</template>

<script>
import { reactive, ref, watch, watchEffect } from "vue";
export default {
  setup() {
    let user = { id: 0, name: "Joe" };

    let state = reactive({ user });

    setTimeout(() => {
      state.user = {
        id: 20,
        name: "Raja",
      };
    }, 2000);

    const count = ref(0);
    const count2 = ref(0);
    const state2 = reactive({ count: 0 })

    const test = () => {
      count.value += 1;
      state2.count += 1;
    }
    watchEffect(() => 
      {
        console.log(count.value);
        console.log(count2.value);
        console.log(state.user);
      }
    )
    
    watch(count2 , () => {
      console.log(count.value);
      console.log(count2.value);
    })
    // watch(count , () => {
    //   console.log(count.value);
    //   console.log(count2.value);
    // })


    /////////////type getting (using deep)
    watch(() => state2 , (curVal, oldVal) => {
      console.log(curVal);
      console.log(oldVal);
      // console.log(count2.value);
    }, {deep : true})
    return {
      state,
      count,
      count2,
      test
    };
  },
};
</script>