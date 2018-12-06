<template>
  <view class="container">
    <text :style="{color: 'green', fontSize: 20}">Myyy Vue Native App</text>
    <text>{{ myInput }}</text>
    <image
      :style="{width: 50, height: 50}"
      :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}"
    />
    <text-input
      :style="{height: 40, width: 150, borderColor: 'gray', borderWidth: 1}"
      v-model="myInput"
    />
    <touchable-opacity
      :on-press="handleButton"
      :style="{backgroundColor: 'red', padding: 10}"
    >
      <text :style="{color: 'white'}">My Button</text>
    </touchable-opacity>
    <!-- <button
      :on-press="handleButton"
      title="My Button"
      color="#841584"
      accessibility-label="Learn more about this purple button"
      :style="{backgroundColor: 'red'}"
    /> -->

    <!-- <flat-list
        :data="countries"
        :render-item="({item}) => renderList(item)"
    /> -->

    <view :style="{borderTopWidth: 1, borderTopColor: 'gray', width: '100%'}"></view>


    <scroll-view :style="{width: '100%'}">
    <view class="border" v-for="(post, index) in posts" :key="index">
      <touchable-opacity class="flex-container" :on-press="() => handleListTap(post)">
        <image
          :style="{width: 40, height: 40, borderRadius: 25, marginRight: 8}"
          :source="{uri: post.data.thumbnail}"
        />
        <text>{{ post.data.title }}</text>
      </touchable-opacity>
    </view>
    </scroll-view>

  </view>
</template>

<script>


export default {
  props: {
    navigation: {
      type: Object
    }
  },
  mounted() {
    fetch('https://reddit.com/r/aww.json?raw_json=1')
      .then(response => response.json())
      .then(data => {
        this.posts = data.data.children
      })
  },
  data() {
    return {
      message: 'Hello, world!',
      myInput: '',
      posts: [],
      countries: [
        { name: "Australia", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/au.png" },
        { name: "Belgium", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/be.png" },
        { name: "Bulgaria", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/bg.png" },
        { name: "Canada", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ca.png" },
        { name: "Switzerland", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ch.png" },
        { name: "China", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/cn.png" },
        { name: "Czech Republic", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/cz.png" },
        { name: "Germany", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/de.png" },
        { name: "Spain", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/es.png" },
        { name: "Ethiopia", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/et.png" },
        { name: "Croatia", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/hr.png" },
        { name: "Hungary", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/hu.png" },
        { name: "Italy", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/it.png" },
        { name: "Jamaica", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/jm.png" },
        { name: "Romania", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ro.png" },
        { name: "Russia", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ru.png" },
        { name: "United States", imageSrc: "https://play.nativescript.org/dist/assets/img/flags/us.png" },
      ],
    }
  },
  methods: {
    handleButton() {
      this.myInput = 'Button clicked'
      this.navigation.navigate("Another");
    },
    handleListTap(post) {
      this.navigation.navigate('Another', {
        imageSrc: post.data.preview.images[0].source.url
      })
    }
    // renderList: (item) => {
    //   return (<Text>{item.name}</Text>)
    // }
  }
}
</script>


<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  font-size: 20;
  color: blue;
}

.border {
  border-bottom-width: 1;
  border-color: gray;
  width: 100%;
  padding: 15;
}

.flex-container {
  flex-direction: row;
  align-items: center;
}
</style>
