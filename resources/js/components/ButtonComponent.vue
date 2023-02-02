<template>
  <button :class="'btn btn-' + tombol + ' text-white'" @click="emitFungsi(id)"><i class="class"></i> {{ nama }}</button>
</template>

<script>
export default {
    props: ['tombol','nama', 'class'],
    methods: {
      emitFungsi(index){
        this.$emit("fungsiEmit", index)
      }
    }
}
</script>

<style>

</style>