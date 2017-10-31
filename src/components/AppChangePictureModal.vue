<template>
  <div class="c-AppChangePictureModal">
    <div class="reveal-overlay is-active">
      <div class="tiny reveal">
        <picture-input 
          ref="pictureInput" 
          @change="onChange" 
          width="200" 
          height="200" 
          margin="16" 
          accept="image/jpeg,image/png" 
          size="10" 
          buttonClass="hide"
          :removable="false"
          :customStrings="{
            upload: '<h1>Bummer!</h1>',
            drag: 'Drag a Image'
          }">
        </picture-input> 
        <div class="update-button-container" v-if="updateButtonOnPictureLoad">
          <a class="button primary" @click="updatePhoto">Update Photo</a>
        </div>
        <button class="close-button" aria-label="Close modal" type="button" 
                @click="closePictureModal">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import PictureInput from 'vue-picture-input';

export default {
  name: 'app-change-picture-modal',
  data () {
    return {
      updateButtonOnPictureLoad: false,
    }
  },
  components: {
    PictureInput
  },
  methods: {
    closePictureModal() {
      this.$emit('close');
    },
    onChange() {
      if (this.$refs.pictureInput.image) {
        this.updateButtonOnPictureLoad = true;
      }
    },
    updatePhoto() {
      // TODO: Server part and update the data into image avatar pending.
      // For now, added the close event handler
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
.c-AppChangePictureModal {

  .reveal-overlay.is-active {
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;

    .reveal {
      display: block;

      @media screen and (min-width: 40em) {
        transform: translateY(-50%);
      }
      
      // TODO: Add them with foundation sass breakpoint on actual project
      padding-top: 2rem;
      padding-bottom: 2rem;

      .update-button-container {
        text-align: center;
        margin-top: 20px;

        button {
          display: inline-block;
        }
      }
    }
  }
}
</style>
