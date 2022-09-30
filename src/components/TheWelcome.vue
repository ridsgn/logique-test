<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const inputName = ref(null);

const onSearch = () => {
  if (!inputName.value) return;
  router.replace({ name: "result", params: { name: inputName.value } });
};
</script>

<template>
  <!-- <pre>{{ data }}</pre> -->
  <img
    alt="Vue logo"
    class="logo"
    src="@/assets/logo-ngmusic.svg"
    width="72"
    height="83"
  />

  <input
    v-model="inputName"
    class="search-input"
    type="text"
    placeholder="Artist / Album / Title"
    @keypress.enter="onSearch"
  />

  <button @click="onSearch" class="button-search">Search</button>
</template>

<style scoped>
img.logo {
  margin: 0 103.8px 219.2px 104px;
  object-fit: contain;
}

.search-input {
  width: 280px;
  height: 40px;
  margin: 15px auto;
  padding: 13px 60px 13px 60px;
  text-align: center;
  border-radius: 20px;
  background-color: #fff;
}

.button-search {
  width: 280px;
  height: 40px;
  margin: 15px auto;
  padding: 13px 116px 11px 117px;
  border-radius: 20px;
  background-color: rgba(255, 255, 255, 0.2);
  position: absolute;
  right: 0;
  left: 0;
  bottom: 0;
  cursor: pointer;
}
</style>
