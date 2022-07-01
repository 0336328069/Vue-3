<template>
  <div>
      <!-- {{testComputed}}
      <button @click="handleComputed">Test Computed</button> -->
      <Suspense>
        <template #default>
            <LazyLoad />
        </template>
        <template #fallback>
          <SkeletonLoading />
        </template>
      </Suspense>
  </div>
</template>

<script>
import {computed, defineAsyncComponent, ref} from 'vue'
import SkeletonLoading from "../components/skeletonLoading.vue"
const LazyLoad = defineAsyncComponent({
  loader : () => import('../components/lazyLoad.vue'),
  loadingComponent : SkeletonLoading,
  delay : 1000,
  timeout : 1500,
  suspensible: false
})
export default {
  components: {
    LazyLoad,
    SkeletonLoading
  },
  setup() {
    const valueComputed = ref(false);
    const testComputed = computed({
      get() {
        return valueComputed.value;
      },
      set(newValue) {
        valueComputed.value = newValue;
      }
    });
    const handleComputed = () => {
      testComputed.value = true;
    }
    return{
      testComputed,
      handleComputed,
      valueComputed
    }
  },
}
</script>

<style>
  /* .fade-enter-active {
  transition: all 0.5s ease-out;
  }

  .fade-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
  }

  .fade-enter-from,
  .fade-leave-to {
    transform: translateY(30px);
    opacity: 0;
  } */
</style>