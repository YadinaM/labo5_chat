<script setup>
import VideoPlayer from "./components/Video/VideoPlayer.vue";
import VideoDetails from "./components/Video/VideoDetails.vue";
import Chat from "./components/Chat/Chat.vue";

import {ref} from "vue";
let newDescription = ref("default");

const updateVideo = (description) => {
  newDescription.value = description;
}

</script>

<template>
  <div class="tiktok">
    <div>
      <VideoPlayer @update:video-description="updateVideo" />
    </div>
    <div class="info">
      <VideoDetails :description = "newDescription" />
      <Chat />
    </div>
  </div>
</template>

<style scoped> /* scoped is enkel over deze pagina, je moet dus niet met classes sukkelen      <div></div>*/
  .tiktok{
    display: grid;
    grid-template-columns: 1fr 1fr;
    background-color: black;
  }
  .info{
    margin-left: 1em;
  }
</style>
