<template>
  <div>
    <nav class="navbar is-fixed-top" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="">
          <img src="@/assets/imgs/AngkorW-WeChat.jpg" width="60" height="60">
        </a>
        <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-start">
          <a class="navbar-item">
            ABP
          </a>
          <a class="navbar-item">
            文档
          </a>

          <div class="navbar-item has-dropdown is-hoverable">
            <a class="navbar-link">
              更多
            </a>
            <div class="navbar-dropdown">
              <a class="navbar-item">
                <router-link to="/about">关于</router-link>
              </a>
              <a class="navbar-item">
                <router-link to="/news">
                  动态
                </router-link>
              </a>
              <a class="navbar-item">
                Contact
              </a>
              <hr class="navbar-divider">
              <a class="navbar-item">
                <span class="field-label">切换主题 <el-switch v-model="theme" /></span>
              </a>
            </div>
          </div>
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <a class="button is-primary">
                <strong>注册</strong>
              </a>
              <a class="button is-light">
                <router-link to="/login">
                  <b>登录</b>
                </router-link>
              </a>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <section class="hero is-medium is-primary is-bold">
      <transition name="fade" mode="out-in">
        <router-view>
        </router-view>
      </transition>
      <div>
        <el-row :gutter="20">
          <el-col :span="5" v-for="(item, index) in items" :key="item.id">
            <el-card :body-style="{ padding: '0px' }" shadow="always">
              <img src="@/assets/imgs/hello.jpg" class="image">
              <div style="padding: 14px;">
                <span>{{item.name}}</span>
                <div class="bottom clearfix">
                  <time class="time">{{ item }}</time>
                  <el-button type="text" class="button">发表见解</el-button>
                </div>
              </div>
            </el-card>
          </el-col>
        </el-row>
      </div>
    </section>
  </div>
</template>

<script>
  import { toggleClass } from '@/utils'
  import { mapActions, mapState, mapMutations, mapGetters } from "vuex";
  import '@/assets/custom-theme/index.css' // the theme changed version element-ui css
  export default {
    name: 'home',
    beforeRouteEnter(to, from, next) {
      // 在渲染该组件的对应路由被 confirm 前调用
      // 不！能！获取组件实例 `this`
      // 因为当守卫执行前，组件实例还没被创建
      next(vm => {


      });
    },
    computed: {
      ...mapState(["blogging/blog/count"]),
      ...mapGetters({
        items: 'blogging/blog/items'
      })
    },
    beforeRouteUpdate(to, from, next) {
      // 在当前路由改变，但是该组件被复用时调用
      // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
      // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
      // 可以访问组件实例 `this`
      next();
    },
    beforeRouteLeave(to, from, next) {
      // 导航离开该组件的对应路由时调用
      // 可以访问组件实例 `this`
      next();
    },
    data() {
      return {
        theme: false
      }
    },
    beforeCreate: () => {

    },
    created: () => {

    },
    beforeMount: () => {


    },
    mounted: () => {


    },
    beforeUpdate: () => {

    },
    updated: () => {


    },
    beforeDestroy: () => {

    },
    destroyed: () => {


    },
    activated: () => {

    },
    deactivated: () => {


    },
    errorCaptured: () => {


    },
    serverPrefetch: () => {


    },
    watch: {
      theme() {
        toggleClass(document.body, 'custom-theme')
      },
      '$route'(to, from) {
        const toDepth = to.path.split('/').length;
        const fromDepth = from.path.split('/').length
      }
    }
  }
</script>

<style scoped>

  .field-label {
    vertical-align: middle;
  }

  .block {
    padding: 30px 24px;
  }

  .tag-item {
    margin-right: 15px;
  }

  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 25%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }

  .clearfix:after {
    clear: both
  }
</style>
