<template>
  <div class="modal-bg">
    <div class="modal">
      <slot name="close"></slot>
      <header>
        <slot name="header">
          <h2>test</h2>
        </slot>
      </header>
      <div class="modal-content">
        <div class="warning">
          <slot name="warning"></slot>
        </div>
        <slot name="content"> </slot>
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal-bg {
  background-color: rgba(12, 12, 12, 0.768);
  position: fixed;
  z-index: 2;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
}
.modal {
  max-width: 640px;
  width: 90%;
  position: fixed;
  top: 20vh;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 6px;
  border: 1px solid #646464;
  background: #fff;
  overflow: hidden;
}
header {
  background: red;
  padding: 10px;
}
header h2 {
  margin: 0px;
}
.modal-content {
  padding: 20px;
}
</style>
