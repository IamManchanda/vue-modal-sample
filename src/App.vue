<template>
  <div id="app">
    <div class="grid-x grid-padding-x align-center-middle text-center" style="height: 200px;">
      <div class="cell small-6">
        <a class="button primary radius" @click="changePicture">Change Picture</a>
      </div>
    </div>
     <transition>
      <app-modal v-if="showChangePictureModal" @close="removeChangePicture"></app-modal>
    </transition>
  </div>
</template>

<script>
import AppModal from './components/AppModal.vue';

export default {
  name: 'app',
  components: {
    'app-modal': AppModal,
  },
  data() {
    return {
      showChangePictureModal: false, 
    };
  },
  methods: {
    changePicture() {
      this.showChangePictureModal = true;
    },
    removeChangePicture() {
      this.showChangePictureModal = false;
    }
  }
}
</script>

<style lang="scss">
</style>
