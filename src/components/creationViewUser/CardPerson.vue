<template>
  <article>
    <span class="description">{{ description }}</span>
    <img class="logoUser" :src="avatar" alt="img">
    <button @click="onClickButtonShow">{{ button_caption }}</button>
    <button @click="onClickButtonHide">X</button>
  </article>
</template>



<script setup>
  import { ref } from "vue";
  import { fetchUserData } from "@/api/apiRequest.js";
  const props = defineProps({
    avatar: {
      type: String,
      required: true
    },
    description : {
      type: String,
      required: true
    },
    button_caption : {
      type: String,
      required: true
    },
    onClickButtonShow : {
      type: Function
    },
    onClickButtonHide : {
      type: Function
    }

  })
  const userData = ref([]);
  async function loadUserData() {
    try{
      const response = await fetchUserData();
      console.log(response);
      userData.value = await response;
    }catch (error){
      console.log(error);
    }
  }
</script>

<style scoped>

article{
  display: flex;
  flex-direction: column;
  align-items: center;
}
span{
  text-align: center;
}

img{
  width: 50%;
}

button{
  width: fit-content;
  border-radius: 5em;
  border-color: black;
  border-style: solid;
  background: white;
  padding : 1.5% 2% 1.5% 2%;
}

button:hover{
  background-color: grey;
}

</style>
<style scoped>

article{
  display: flex;
  flex-direction: column;
  align-items: center;
}
span{
  text-align: center;
}

img{
  width: 50%;
}

button{
  width: fit-content;
  border-radius: 5em;
  border-color: black;
  border-style: solid;
  background: white;
  padding : 1.5% 2% 1.5% 2%;
}

button:hover{
  background-color: grey;
}

</style>