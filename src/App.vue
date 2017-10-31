<template>
  <div id="app">
    <div class="grid-x grid-padding-x align-center-middle text-center" style="height: 200px;">
      <div class="cell small-6">
        <a class="button primary radius" @click="changePicture">Change Picture</a>
      </div>
    </div>
     <transition>
      <app-change-picture-modal v-if="showChangePictureModal" @close="removeChangePictureModal"></app-change-picture-modal>
    </transition>
  </div>
</template>

<script>
import AppChangePictureModal from './components/AppChangePictureModal.vue';

export default {
  name: 'app',
  components: {
    'app-change-picture-modal': AppChangePictureModal,
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
    removeChangePictureModal() {
      this.showChangePictureModal = false;
    }
  }
}
</script>

<style lang="scss">
</style>
