<template>
  <div class="home">
    <div class="sidebar">
      <button class="sidebar-button" @click="updateState(0)"> Erkam 1 </button>
      <button class="sidebar-button" @click="updateState(1)"> Erkam 2 </button>
      <button class="sidebar-button" @click="updateState(2)"> Erkam 3 </button>
      <button class="sidebar-button" @click="updateState(3)"> Erkam 4 </button>
      <button class="sidebar-button" @click="updateState(4)"> Erkam 5 </button>
      <button class="sidebar-button" @click="updateState(5)"> Zal 1 </button>
      <button class="sidebar-button" @click="updateState(6)"> Zal 2 </button>
      <button class="sidebar-button" @click="updateState(7)"> Zal 3 </button>
      <button class="sidebar-button" @click="updateState(8)"> Zal 4 </button>
      <button class="sidebar-button" @click="updateState(9)"> Zal 5 </button>
      <span>current index: {{ state }}</span>
    </div>

    <!-- Erkam -->
    <div class="main-section" v-if="state === 0">
      <NavbarTop/>
      <Navbar/>
    </div>
    <div class="main-section" v-if="state === 1">
      1
    </div>
    <div class="main-section" v-if="state === 2">
      2
    </div>
    <div class="main-section" v-if="state === 3">
      3
    </div>
    <div class="main-section" v-if="state === 4">
      4
    </div>

    <!-- Zal -->
    <div class="main-section" v-if="state === 5">
      5
    </div>
    <div class="main-section" v-if="state === 6">
      6
    </div>
    <div class="main-section" v-if="state === 7">
      7
    </div>
    <div class="main-section" v-if="state === 8">
      8
    </div>
    <div class="main-section" v-if="state === 9">
      9
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      state: 0,
    };
  },
  methods: {
    updateState(index) {
      this.state = index;
    },
  },
};
</script>

<style>
body {
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

.home {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: start;
}

.main-section {
  width: 90%;
  height: 100%;
}

.sidebar {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  width: 10%;
  height: 100%;
  border-right: 1px solid #ccc;
  background-color: beige;
}

.sidebar-button {
  margin-bottom: 10px;
  background-color: #0d080f;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.sidebar-button:hover {
  background-color: #6c6c6c;
}

.current-state {
  margin-top: 20px;
  font-weight: bold;
}


</style>