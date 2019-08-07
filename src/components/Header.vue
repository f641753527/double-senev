<template>
    <div class="header">{{title}}</div>
</template>

<script>
export default {
  data () {
    return {
      title: '情人节快乐'
    }
  }
}
</script>

<style scoped>
.header{
    background-color: #000;
    color: #fff;
    height: 1.2rem;
    width: 10rem;
    line-height: 1.2rem;
    text-align: center;
    font-size: 16px;
    font-weight: 600;
}
</style>
