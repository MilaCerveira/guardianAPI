<template>
  <div>
    <NewsList />
  </div>
</template>

<script>
import NewsList from "./components/NewsList";

export default {
  name: "App",

  components: {
    NewsList: NewsList,
  },
};
</script>

