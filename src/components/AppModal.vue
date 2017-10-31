<template>
  <div class="c-AppModal">
    <div class="reveal-overlay is-active">
      <div class="small reveal">
        <app-change-picture></app-change-picture>
        <button class="close-button" data-close="" aria-label="Close modal" type="button" 
                @click="closePictureModal">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import AppChangePicture from './AppChangePicture.vue';

export default {
  name: 'app-modal',
  components: {
    'app-change-picture': AppChangePicture
  },
  methods: {
    closePictureModal() {
      this.$emit('close');
    },
  },
  mounted() {
    document.addEventListener("keydown", (e) => {
      // Escape Key Code = 27
      // Source: http://keycode.info/ 
      if (e.keyCode == 27) { 
        this.closePictureModal();
      }
    });
  },
}
</script>

<style lang="scss">
.c-AppModal {

  .reveal-overlay.is-active {
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;

    .reveal {
      display: block;
      transform: translateY(-50%);
    }
  }
}
</style>
