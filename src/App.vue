<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <column-list :list="list"></column-list>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/column-list.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'

const currentUser: UserProps = {
  isLogin: true,
  name: 'wuxiayu',
  id: 1
}

const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1的专栏非常有意思',
    avatar:
      'https://tse1-mm.cn.bing.net/th/id/R-C.33d0949ed1d018fbd23b9264027e58e0?rik=XYcoHb%2foHS2aFw&riu=http%3a%2f%2fwww.desktx.com%2fd%2ffile%2fwallpaper%2fscenery%2f20170120%2fdf204ebd7a4829933463e2989deb54c6.jpg&ehk=oIKu9Q7Dsgg8tGWfXQ%2fdcQBt4l%2f92jwsatz95dhd0oE%3d&risl=&pid=ImgRaw&r=0'
  },
  {
    id: 2,
    title: 'test2的专栏',
    description: '这是test2的专栏非常有意思',
    avatar:
      'https://tse1-mm.cn.bing.net/th/id/R-C.33d0949ed1d018fbd23b9264027e58e0?rik=XYcoHb%2foHS2aFw&riu=http%3a%2f%2fwww.desktx.com%2fd%2ffile%2fwallpaper%2fscenery%2f20170120%2fdf204ebd7a4829933463e2989deb54c6.jpg&ehk=oIKu9Q7Dsgg8tGWfXQ%2fdcQBt4l%2f92jwsatz95dhd0oE%3d&risl=&pid=ImgRaw&r=0'
  },
  {
    id: 3,
    title: 'test3的专栏',
    description: '这是test2的专栏非常有意思'
    // avatar:
    //   'https://tse1-mm.cn.bing.net/th/id/R-C.33d0949ed1d018fbd23b9264027e58e0?rik=XYcoHb%2foHS2aFw&riu=http%3a%2f%2fwww.desktx.com%2fd%2ffile%2fwallpaper%2fscenery%2f20170120%2fdf204ebd7a4829933463e2989deb54c6.jpg&ehk=oIKu9Q7Dsgg8tGWfXQ%2fdcQBt4l%2f92jwsatz95dhd0oE%3d&risl=&pid=ImgRaw&r=0'
  },
  {
    id: 4,
    title: 'test4的专栏',
    description: '这是test2的专栏非常有意思',
    avatar:
      'https://tse1-mm.cn.bing.net/th/id/R-C.33d0949ed1d018fbd23b9264027e58e0?rik=XYcoHb%2foHS2aFw&riu=http%3a%2f%2fwww.desktx.com%2fd%2ffile%2fwallpaper%2fscenery%2f20170120%2fdf204ebd7a4829933463e2989deb54c6.jpg&ehk=oIKu9Q7Dsgg8tGWfXQ%2fdcQBt4l%2f92jwsatz95dhd0oE%3d&risl=&pid=ImgRaw&r=0'
  }
]
export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader
  },
  setup() {
    return {
      list: testData,
      currentUser
    }
  }
})
</script>

<style></style>
