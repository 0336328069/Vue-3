<template>
    <div class="header">
        <h2>The Coffee Shop</h2>
        <ul class="navigation">
          <li>
            <router-link :to="{name : 'home'}">Home</router-link>
          </li>
          <li>
            <router-link :to="{name : 'about'}">About</router-link>
          </li>
          <li>
            <router-link :to="{name : 'load'}">Load</router-link>
          </li>
        </ul>
    </div>
</template>

<script>
import { reactive, ref, shallowRef } from '@vue/reactivity'
export default {
    name: "Header",
    props: {

    },
    setup(props) {
        const testRef = ref({ id : 1 , name: 'Hung' , dev : 'FrontEnd Developer'})
        const testShallowRef = shallowRef({ id : 1 , name: 'Hung' , dev : 'FrontEnd Developer'});
        testRef.value.id += 1;
        testShallowRef.value.id += 1;
        // console.log(testRef.value);
        // console.log(testShallowRef.value);
        const map = reactive(new Map([['count', ref(0)]]))
        // need .value here
        // map.set('count',ref(1000));
        // console.log(map)
        const count = reactive({ data : {} });
        count.data = testRef;
        
        return {
          testRef,
          testShallowRef,
          map,
          count

        }
    }
}
</script>