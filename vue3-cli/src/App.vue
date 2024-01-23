<!-- vbc + TAB 을 하면 싱글파일 컴포넌트 구조가 생성된다. -->
<template>
  <!-- 상위 컴포넌트의 data를 하위 자식에게 넘겨준다. (props 사용) -->
  <!-- v-bind:하위props이름 = "상위data이름" -->

  <!-- 하위 클릭 이벤트를 상위 컴포넌트에 전달해서 동작을 구현한다. -->
  <!-- v-on:하위 emit 이벤트 이름 = "상위 컴포넌트의 동작(메서드) 이름" -->
  <AppHeader v-bind:appTitle="message" v-on:change="changeMessage"></AppHeader>
</template>

<script>
// import 컴포넌트 이름 from './컴포넌트 경로'
import AppHeader from "./components/AppHeader.vue";

export default {
  components: {
    // '컴포넌트이름': 컴포넌트 내용
    // 'app-header': AppHeader,
    // === 'AppHeader': AppHeader
    // === AppHeader: AppHeader,
    AppHeader
  },

  // data -> vda + TAB
  data() {
    return {
      message: "앱 헤더 컴포넌트"
    };
  },
  methods: {
    changeMessage() {
      this.message = "변경됨";
    }
  }
};
</script>

<style scoped></style>
