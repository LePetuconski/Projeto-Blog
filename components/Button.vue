<template>
  <div>
    <button :class="_class" :data-target="'#'+ id" data-toggle="modal"
      style="background-color: #9545ed; border-color: #9545ed;">
      <slot></slot>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    _class: { required: true }, //campos obrigatórios
    id: { required: true }
  }
}
</script>

