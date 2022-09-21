<template>
  <div class="table-container" :class="{show: drawerShow}">aaa</div>
</template>

<script>
export default {
    name:'MySideTab',
    data() {
        return {
            drawerShow: false,
        }
    },
    methods: {
        handleVisible() {
            this.drawerShow = !this.drawerShow;
        }
    }
}
</script>

<style lang="less">
.table-container {
    position: fixed;
    right: -200px;
    top: 0;
    width: 200px;
    height: 100%;
    z-index: 99;
    transition:all 0.6s ease;
    background-color: rgba(59, 90, 158, 0.753);
}
.show {
    right: 0;
}
</style>