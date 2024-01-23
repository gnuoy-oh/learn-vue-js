<template>
  <form action="" @submit.prevent="submitForm">
    <div>
      <!-- v-model: 뷰의 디렉티브 중 하나로, 값을 받아와서 동기화 시킬 수 있는 디렉티브  -->
      <label for="userId">ID: </label>
      <input type="text" id="userId" v-model="username" />
    </div>
    <div>
      <label for="password"> PW: </label>
      <input type="text" id="password" v-model="password" />
    </div>
    <!-- @click 이벤트를 넣어도 되지만, form 요소에서 제어해도 된다. -->
    <button type="submit">로그인</button>
  </form>
</template>

<script>
import axios from "axios";
import { ref } from "vue";

export default {
  // Compositon API (맨 아래 선언한 기존 data,methods 와 동일한 의미이다.)
  setup() {
    // data와 정확하게 같은 의미이다.
    const username = ref("");
    const password = ref("");

    //methods
    const submitForm = () => {
      axios
        .post("https://jsonplaceholder.typicode.com/users", {
          // .value 붙이는 이유: Composition API의 특징임
          // ref 지정한 안의 value가 원하는 값이다.
          username: username.value,
          password: password.value
        })
        .then(response => {
          console.log(response);
        });
    };

    return { username, password, submitForm };
  }

  // data() {
  //   return {
  //     username: "",
  //     password: ""
  //   };
  // },
  // methods: {
  //   submitForm() {
  //     // 상위 디렉티브에서 이벤트 제어를 할 수 있음 (@click.prevent="submitForm")
  //     // event.preventDefault();

  //     const data = {
  //       username: this.username,
  //       password: this.password
  //     };

  //     axios
  //       .post("https://jsonplaceholder.typicode.com/users", data)
  //       .then(response => {
  //         console.log(response);
  //       });
  //   }
  // }
};
</script>

<style scoped></style>
