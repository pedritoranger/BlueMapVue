<template>
  <div id="app" :class="{'theme-light': appState.theme === 'light', 'theme-dark': appState.theme === 'dark'}">
    <FreeFlightMobileControls v-if="appState.controls.state === 'free'" />
    <ControlBar />
    <MainMenu :menu="appState.menu" />
  </div>
</template>

<script>
import ControlBar from "@/components/ControlBar/ControlBar";
import MainMenu from "@/components/Menu/MainMenu";
import FreeFlightMobileControls from "@/components/Controls/FreeFlightMobileControls";

export default {
  name: 'App',
  components: {
    FreeFlightMobileControls,
    MainMenu,
    ControlBar
  },
  data() {
    return {
      appState: this.$bluemap.appState,
    }
  }
}
</script>

<style lang="scss">
  @import "~@/scss/global.scss";

  #map-container {
    position: absolute;
    width: 100%;
    height: 100%;
  }

  #app {
    position: absolute;
    width: 100%;
    height: 100%;

    z-index: 100; // put over bluemap markers

    pointer-events: none;

    font-size: 1rem;
    @media (max-width: $mobile-break) {
      font-size: 1.5rem;
    }
  }
</style>
