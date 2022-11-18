<script setup>
const props = defineProps({
  show: Boolean
})
</script>

<template>
  <Transition name="modal">
    <div v-if="show" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">Instruction</slot>
          </div>

          <div class="modal-body">
            <slot name="body">
              <ul>
                <li>Write in the field what you want to do</li>
                <li>Choose which category it belongs to</li>
                <li>Click "Add todo"</li>
                <li>Click on the circle of the created task to cross it out</li>
                <li>Click "delete" to delete the created task</li>
                <li>You can click on the created task to edit it</li>
              </ul>
            </slot>
          </div>

          <div class="modal-footer">
            <slot name="footer">
              <b>Good luck!</b>
              <button
                class="modal-default-button"
                @click="$emit('close')"
              >OK</button>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 600px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header h2 {
  margin-top: 0;
  color:mediumslateblue;
}

.modal-body {
  margin: 10px 0;
}

.modal-body li {
  padding-bottom: 5px;
}

.modal-default-button {
  float: right;
}

.modal-footer b{
  color: mediumslateblue;
}

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>