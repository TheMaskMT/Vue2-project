<script type="text/x-template" id="dialog-template">
  <transition name="modal">
    <div class="dialog-mask">
      <div class="dialog-container">
        <div class="dialog-header">
          <slot name="header">
            Default Header
          </slot>
        </div>
        <div class="dialog-body">
          <slot name="body">
            Default Body
          </slot>
        </div>
        <div class="dialog-footer">
          <slot name="footer">
            Default Footer
          </slot>
          <button class="dialog-button" @click="$emit('close')">
            Close
          </button>
        </div>
      </div>
    </div>
  </transition>
</script>

<script>
  export default {
    name: 'Dialog',
    data() {
      return {
        show: false
      }
    },
    methods: {
      close() {
        this.show = false
      }
    }
  }
</script>

<style scoped>
  .dialog-mask {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .dialog-container {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
    width: 300px;
  }

  .dialog-header {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 10px;
  }
</style>