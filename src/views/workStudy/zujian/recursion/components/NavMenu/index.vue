<template>
  <el-menu
    default-active="2"
    class="el-menu-vertical-demo"
    background-color="#545c64"
    text-color="#fff"
    router
    active-text-color="#ffd04b">
    <template v-for="item in menu">
      <el-menu-item v-if="item.name === 'layout'" :key="item.name" :index="item.path">
        <i :class="['iconfont', item.meta.icon]" v-if="item.meta && item.meta.icon"></i>
        <span>{{ item.meta.title }}</span>
      </el-menu-item>
      <el-submenu v-else :key="item.name" :index="item.path">
        <template slot="title">
          <i :class="['iconfont', item.meta.icon]" v-if="item.meta && item.meta.icon"></i>
          <span>{{ item.meta.title }}</span>
        </template>
        <template v-for="child in item.children">
          <v-nav-menu :key="child.name" v-if="child.children && child.children.length > 0" :menu="item.children"></v-nav-menu>
          <el-menu-item :key="child.name" v-else :index='item.path + "/" + child.path'>{{ child.meta.title }}</el-menu-item>
        </template>
      </el-submenu>
    </template>
  </el-menu>
</template>

<script>
  export default {
    name: 'vNavMenu',
    props: {
      menu: {
        type: Array
      }
    }
  }
</script>
