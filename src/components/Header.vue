<template>
  <header class="flex h-16 justify-center items-center text-xl bg-black text-white">
    <h1>client app vlcc</h1>
    <div class="absolute top-2 right-5">
    <button id="bnt_pubcam" class="bg-blue-500 px-4 py-2 text-white rounded-lg mr-5" @click="start(true)" v-if="this.$root.publisher">Publish Camera</button>
    <button id="bnt_pubscreen" class="bg-green-500 px-4 py-2 text-white rounded-lg" @click="start(false)" v-if="this.$root.publisher">Publish Screen</button>
    <button class="bg-red-500 px-4 py-2 text-white rounded-lg" v-on:click="joinRoom()">join room</button>
    </div>
  </header>
</template>

<script>
  export default {
    name: "Header",
  data() {
    return {
     
      joinroom: {
        roomID: "e5dfc16f-b4c7-43cb-bfd2-78b21895e148",
        adminList: "",
        userList: ["user1"],
      },
      roomjoined:false

    };
  },
    methods: {
      start(e) {
        this.$root.startPublish(e);
      }
    },
    async joinRoom() {
      var payload = this.joinroom;
      axios.patch("http://localhost:8000/joinroom/", payload);
      console.log(payload);
      this.roomjoined=true
      console.log(this.roomjoined)
    },
  }
</script>
