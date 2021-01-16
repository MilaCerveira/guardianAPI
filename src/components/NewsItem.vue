<template>
  <div>
    <li v-for="newsItem in news" :key="newsItem.id">
      {{ newsItem.webTitle }}
    </li>
  </div>
</template>

<script>
export default {
  props: ["news"],
};
</script>