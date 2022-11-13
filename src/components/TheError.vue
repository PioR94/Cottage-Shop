<template>
  <dialog open>
    <div class="err">
      <h3>{{message}}</h3>
      <slot name="ok"></slot>
    </div>
  </dialog>
</template>

<script>
export default {
  props: ['message']
}
</script>

<style>
.err {
  display: flex;
  width: 300px;
  height: 100px;
  background-color: rgba(255, 0, 0, 0.4);
  border: 1px solid black;
  align-items: center;
  justify-content: center;
}
</style>


