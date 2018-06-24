<template>
  <view>
    <text>Another Screen</text>
    <image
      :style="{width: '100%', height: '100%'}"
      :source="{uri: navigation.getParam('imageSrc')}"
    />
    <button title="go back" :on-press="() => navigation.goBack()" />
  </view>
</template>

<script>
export default {
  props: {
    navigation: {
      type: Object
    }
  }
}
</script>

