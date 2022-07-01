<template>
  <div>
    <div class="list-post">
      <template v-for="(item,index) in data" :key="`api_${index}`">
          <div class="post-item">
            <span class="post-item__stt">STT : {{index++}}</span>
            <h2 class="post-item__title">Title : {{item.title}}</h2>
            <p class="post-item__desc">Description : {{item.body}}</p>
          </div>
      </template>
    </div>
  </div>
</template>

<script>
import { onMounted, ref } from '@vue/runtime-core';
export default {
  name:"LazyLoadComponent",
  setup() {
    const data = ref(null);
    onMounted(async () => {
        const res = await fetch('https://jsonplaceholder.typicode.com/posts');
          data.value = await res.json();
    })
    return {
      data
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