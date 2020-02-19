<template>
  <div class="row">
    <div class="col-3">
      <img alt="Vue logo" src="./../assets/logo.png" style="max-width:30%;">
    </div>
    <div class="col-9">
      <div class="row">
        <div class="col" v-bind:class="{ orderon: !isfinish }">
          {{content.status.type}}
        </div>
        <div class="col" v-if="!isfinish">
          預計出貨：{{content.date}}
        </div>
        <div class="w-100"></div>
        <div class="col">
          {{content.name}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // 接收父組件的參數
  props: {
    'content':Object,
    'index':Number, 
    'isfinish':Boolean
  }
}
</script>
<style>
  .orderon{
    color:green
  }
</style>