<template>
  <div class="home">
    <h1>Home</h1>
    <Map />
  </div>
</template>

<script>
import Map from "@/components/Map.vue";
export default {
  name: "Home",
  components: { Map },
};
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
