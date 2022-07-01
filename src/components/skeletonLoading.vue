<template>
  <div>
    <div class="list-post">
      <template v-for="index in lengthTemp" :key="`api_${index}`">
          <div class="post-item loading !h-[280px] rounded-md">
            <span class="post-item__stt h-5">STT :</span>
            <h2 class="post-item__title h-20">Title :</h2>
            <p class="post-item__desc h-[calc(100%-100px)]">Description :</p>
          </div>
      </template>
    </div>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {
  name:"LazyLoadComponent",
  async setup() {
    const lengthTemp = ref(12);
    return {
      lengthTemp
    }
  },
};
</script>

<style>
  .list-post{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    padding: 20px 40px;
    gap: 20px;
  }
  .post-item{
    width: 100%;
    height: auto;
    word-break: break-word;
    padding: 20px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }
</style>