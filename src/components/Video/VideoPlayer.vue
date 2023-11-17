<script setup>
import {ref, reactive, onMounted} from 'vue';

const emit = defineEmits(['update:videoDescription']);

let videoUrl = ref("");
let videos = reactive({
    data: [],
}) //reflective wnt is complexer dn een string
/*
onMounted(() => {
    fetch("https://api.jsonbin.io/v3/b/6548ef9954105e766fcc2c15")
    .then((response) => response.json())
    .then((data) => {
        videos.data = data.record.videos;
        videoUrl.value = videos.data[0].video;

        emit("update:videoDescription", videos.data[0].description);
    })
})*/

</script>

<template>
    <div>
        <video :src="videoUrl" controls autoplay muted loop> </video> <!--: is iets binden aan iets-->
    </div>
</template>

<style scoped> /* scoped is enkel over deze pagina, je moet dus niet met classes sukkelen <div></div> */

</style>