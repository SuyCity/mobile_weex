<template>
  <div class="wrapper">
    <image :src="logo" class="logo" />
    <text class="greeting">The environment is ready!</text>
    <router-view/>
    <list class="list">
      <cell v-for="item in items">
        <div @click="clickItem(item.url)" class="card">
          <text class="title">{{item.title}}</text>
        </div>
      </cell>
    </list>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    items:[{
      title: "Page1",
      url: ""
    },
    {
      title: "Page2",
      url: ""
    }]
    return {
      logo: 'https://gw.alicdn.com/tfs/TB1yopEdgoQMeJjy1XaXXcSsFXa-640-302.png',
    };
  },
  methods: {
    clickItem: function(e) {
      let url = root.replace('index.js', e);
      if (e === 'navigation.js') {
        url += "?wx_navbar_hidden=true";
      }
      navigator.push({
        url: url,
        animated: 'true'
      }, function() {})
    }
  }
};
</script>

<style scoped>
  .wrapper {
    justify-content: center;
    align-items: center;
  }
  .logo {
    width: 424px;
    height: 200px;
  }
  .greeting {
    text-align: center;
    margin-top: 70px;
    font-size: 50px;
    color: #41B883;
  }
  .message {
    margin: 30px;
    font-size: 32px;
    color: #727272;
  }
</style>
