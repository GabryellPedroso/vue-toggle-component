<template lang="pug">
  #app(:style="{ backgroundColor: checked ? '#F25C05' : '#1C2C40' }")
    toggle-input(
      id="toggle-input"
      toggleColorOn="#F25C05"
      toggleContainerColorOn="#F2CB05"
      toggleColorOff="#1C2C40"
      toggleContainerColorOff="#1D7373"
      :padding="8"
      :label="checked ? greeting : 'zZz'"
      :labelColor="checked ? '#F2CB05' : '#1D7373'"
      fontSize="0.9rem"
      labelPosition="bottom"
      labelMargin="10px"
      :checked="checked"
      @change="(newValue) => checked = newValue"
      :size="60")
    
    footer(:style="{ color: checked ? '#F2CB05' : '#1D7373' }")
      a(href="https://bit.ly/2RLYNhv" target="_blank")
        i.fab.fa-github
      a(href="https://bit.ly/2RL254x" target="_blank")
        i.fab.fa-twitter
</template>

<script>
import greetings from './lang'
import ToggleInput from './components/ToggleInput.vue'

const userLanguage = navigator.language.split('-')[0]

export default {
  name: 'App',
  components: {
    ToggleInput
  },
  data() {
    return {
      checked: true,
      label: {
        on: '',
        off: ''
      }
    }
  },
  computed: {
    greeting() {
      return greetings[userLanguage] || greetings['en']
    }
  }
}
</script>

<style lang="scss">
* {
  -webkit-tap-highlight-color: rgba(0,0,0,0);
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  align-items: center;
  justify-content: center;
  
  width: 100vw;
  height: 100vh;
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  transition: ease-in-out 0.2s;

  footer {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100vw;
    padding: 60px 0;
    transition: inherit;

    a {
      margin: 0 15px;
      color: inherit;
      transition: inherit;
      
      .fa-github,
      .fa-twitter {
        font-size: 1.75rem;
        color: inherit;
        transition: inherit;
      }
    }
  }
}
</style>
