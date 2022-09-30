<template>
  <div class="card">
    <div class="wrapper">
      <div class="thumbnail">
        <slot name="thumbnail"></slot>
      </div>
      <div class="details">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  padding: 12px 10px;
  margin-bottom: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);
  background-color: #fff;
}

.wrapper {
  display: flex;
  color: #334155;
}

.thumbnail {
  margin-right: 12px;
}

.details {
  display: flex;
  flex-direction: column;
  flex: auto;
}
</style>
