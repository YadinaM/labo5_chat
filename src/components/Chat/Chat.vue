<script setup>
    import {ref, reactive, onMounted} from "vue";

    let message = ref(""); //int, string, boolean= voor simpele waarden
    let user = ref("");
    let allMessages = reactive({
        data: [],
    });


    onMounted(async () => {
        try {
            const response = await fetch("https://lab5-p379.onrender.com/api/v1/messages/");
            const data = await response.json();
            allMessages.data = data.slice(-10);
        } catch (error) {
            console.error("Error fetching data:", error);
        }
    });

 const sendMessage = async  () => {
        //allMessages.data.push({ text: message.value, user: "Me" });

        const newMessage = { text: message.value, user: 'Me' };

        try {
            const response = await fetch('https://lab5-p379.onrender.com/api/v1/messages/', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
        },
      body: JSON.stringify(newMessage),
    });

    if (response.ok) {
      allMessages.data.unshift(newMessage);
    } else {
      console.error('Failed to post message to the API');
    }
    } catch (error) {
        console.error('Error posting message:', error);
    }


        message.value = "";
    }

</script>

<template>
  <div>
      <ul>
        <li v-for="m in allMessages.data" :key="m.id">
            <div class="user">{{ m.user }}</div>
            <div class="text">{{ m.text }}</div>        
        </li>      
      </ul>

      <div>
          <input v-model="message" type="text" />
          <button @click="sendMessage" > Send </button>
      </div>
  </div>
</template>

<style scoped> /* scoped is enkel over deze pagina, je moet dus niet met classes sukkelen */
    ul{
        list-style: none;
        margin-left: -2.5em;
        width: 400px;
    }
    li{
        background-color: black;
        color: white;
        padding-left: 1em;
        padding-top: 1em;
        padding-bottom: 1em;
    }
</style>
