<template>
  <el-row>
    <el-col align="center">
      <img :src="imgSrc" />
      <h1>{{ msg }}</h1>
      <el-button type="primary" @click="inCrement"> count is: </el-button>
      <br />
      <el-tag closable>
        {{ count }}
      </el-tag>
    </el-col>
  </el-row>
</template>

<script>
  import { defineComponent, computed } from 'vue'
  import { useStore } from 'vuex'
  import { key } from '../store'
  import logo from '@/assets/logo.png'

  export default defineComponent({
    name: 'HelloWorld',
    setup() {
      const store = useStore(key)
      const count = computed(() => store.state.count)

      return {
        count,
        inCrement: () => store.commit('increment')
      }
    },
    data() {
      return {
        msg: 'HelloWorld',
        imgSrc: logo
      }
    }
  })
</script>
