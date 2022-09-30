<script setup>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import { useFetch } from "../composable/fetch";
import CardItem from "./CardItem.vue";

const url = ref(`https://itunes.apple.com/search?term=json+mraz&limit=4`);

const route = useRoute();

const test = route.params.name.split(" ").join("+");

const { data } = useFetch(url);

onMounted(() => {
  url.value = `https://itunes.apple.com/search?term=${test}&limit=4`;
});
</script>

<template>
  <!-- <pre>{{ data?.results }}</pre> -->
  <div class="header">ngmusic</div>

  <div class="center">
    Search result for : <span>{{ route.params.name }}</span>
  </div>

  <div class="card-wrapper">
    <CardItem v-for="item in data?.results" :key="item">
      <template #thumbnail>
        <img
          class="image"
          :src="item.artworkUrl100"
          :alt="item.artworkUrl100"
        />
      </template>
      <div class="detail-wrapper">
        <div class="artist-name">{{ item.artistName }}</div>
        <div class="track-name">{{ item.trackName }}</div>
      </div>
      <div class="footer">
        <div class="genre-name">{{ item.primaryGenreName }}</div>
        <div class="price">
          <img src="@/assets/currency-dollar.svg" class="currency-dollar" />
          {{ item.trackPrice }}
        </div>
      </div>
    </CardItem>
  </div>
</template>

<style>
.card-wrapper {
  padding: 0 15px;
}

.header {
  height: 60px;
  text-align: center;
  padding: 18px 15px 22.2px;
  box-shadow: 0 0 6px 0 rgba(148, 77, 230, 0.75);
  background-image: linear-gradient(100deg, #712bda, #a45deb 100%);
}

.center > span {
  color: #7b34dd;
  font-weight: bold;
  font-size: 18px;
  text-transform: capitalize;
}

.artist-name {
  font-size: 10px;
  font-weight: 500;
}

.center {
  text-align: center;
  color: #334155;
  margin: 39px 0 36px 0;
}

.image {
  border-radius: 10px;
}

.detail-wrapper {
  max-width: 65%;
  flex-grow: 1;
}

.track-name {
  font-size: 14px;
  font-weight: bold;
  max-height: 45px;
  overflow: hidden;
}

.footer {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.genre-name {
  background-color: #10b981;
  font-size: 10px;
  color: white;
  font-weight: 500;
  padding: 5px 13px 4px;
  border-radius: 10em;
}

.price {
  display: flex;
  font-size: 12px;
  font-weight: bold;
  color: #f5b014;
}

.currency-dollar {
  margin-right: 6px;
}
</style>
