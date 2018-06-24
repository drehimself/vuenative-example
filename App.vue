<template>
  <app-navigation></app-navigation>
</template>

<script>
import { StackNavigator } from "vue-native-router"
import MainScreen from './Main'
import AnotherScreen from './Another'

const AppNavigation = StackNavigator(
  {
    Main: MainScreen,
    Another: AnotherScreen,
  },
  {
    initialRouteName: 'Main',
  }
)
export default {
    components: { AppNavigation }
}
</script>
