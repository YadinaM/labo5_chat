<script setup>
    import {ref, reactive, onMounted} from "vue";

    let message = ref(""); //int, string, boolean= voor simpele waarden
    let user = ref("");
    let allMessages = reactive({
        data: [],
    });

    const sendMessage = () => {
        allMessages.data.push({ text: message.value, user: user.value });
        message.value = "";
    }

</script>

<template>
  <div>
      <ul>
          <li v-for="m in allMessages.data" >{{ m }}</li>  <!--zoals foreach bij php-->
      </ul>

      <div>
          <input v-model="message" type="text" />
          <button @click="sendMessage" > Send </button>
      </div>
  </div>
</template>

<style scoped> /* scoped is enkel over deze pagina, je moet dus niet met classes sukkelen */

</style>
