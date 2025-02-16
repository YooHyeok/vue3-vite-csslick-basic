# `Vue 3 CompositionAPI 예제 프로젝트`

# Composition API(3.1) 소개
<details>
<summary>펼치기/접기</summary>
<br>

## Composition API란?
기존 문법을 간결하게 다루게 해준다.  
vue 3.1 버전 이상에서 도입된 Composition API의 더욱 간소화된 문법을 소개한다.  
새로운 빌드 도구인 vite에서 기본 템플릿으로 제공하고 있다.  
공식 문서에서도 Composition API 사용을 권장하고 있다.  
주요 개선사항으로는 setup 기능으로 스크립트 작성 규칙을 단순화 시켰으며, 컴포넌트 관련 항목들, name, components 등 옵션등을 일일히 구분하지 않아도 된다.  
또한 export default 이하 데이터, 메소드, watch 등 또한 마찬가지로 따로 구분 필요 없이 한 곳에 작성 가능하다.  
상태 변수를 작성하는 문법이 변경되었으며, ref() 함수를 이용해 관리할 수 있다.  
라이프사이클 같은 경우도 함수로 작성하면 되며, onMounted로 이르만 변경되었다.

### 주요 개선 사항 정리
- setup 기능으로 스크립트 작성 규칙 단순화
- 옵션을 따로 구분할 필요 없이 한곳에서 작성
  - export default 이하 data, method, watch 등 구분 필요 없이 한곳에 작성 가능
- ref()로 상태변수 관리
- depfineProps로 prop 관리
### 실제 개선된 내용 코드 예시
- AS-IS
  ```vue
  <script>
    export default {
      name: 'AppComponent',
      data() {
        return {
          name: "APP",
          count: 0
        }
      },
      methods: {
        addCount() {
          count.value += 1;
        }
      },
      mounted() {
        console.log('mounted')
      },
    }
  </script>
  ```
- TO-BE
  ```vue
  <script setup>
    import { ref, onMounted } from 'vue';
    let name = ref('App');
    let count = ref(0);
    onMunted(() => {
      console.log('mounted')
    })
  </script>
  ```
</details>
<br>

# Vue3 CLI 프로젝트 설치 및 기동
<details>
<summary>펼치기/접기</summary>
<br>

## 필수 요소
- Node.js (LTS)
- IDE: VSC 등

## 터미널 
- vue/cli 설치 명령어 입력
  ```bash
  npm install -g @vue/cli
  ```
- Vue 프로젝트 생성
  ```bash
  vue create {프로젝트명}
  ```
- Vue 버전 선택 - 첫번째 Vue3 선택
  ```bash
  ? Please pic a preset: (Use arrow keys)
  > Default ( [Vue 3] babel, eslint)
    Default ( [Vue 2] babel, eslint)
    Manually select features
  ```
- 설치 완료 후 최종 터미널 통합 출력 내용
  ```bash
  Generating README.md...  

  Successfully Created project movie-info.  
  Get started with the following commands:  
  ```
- VSC 실행
  ```bash
  code .
  ```
- vue 프로젝트 node 개발서버 실행
  ```bash
  npm run serve
  ```
</details>
<br>

# Vite 빌드 툴 소개
<details>
<summary>펼치기/접기</summary>
<br>

Vue3로 넘어가면서 프로젝트를 만들고 빌드하던 기존 vue cli 대신 Vite를 사용할 수 있다.  
Vite는 FrontEnd 개발 툴로 Vue 뿐만 아니라 React등 다른 FrontEnd 개발 어디서든 사용이 가능하다.  
기존 Vue CLI와 마찬가지로 개발용 서버 기능과 배포를 위한 빌드 기능을 제공한다.  
Vite를 쓰는 이유는 배포를 위한 과정에서 코드를 통합하는 번들링 과정이 필요하며, 이때 기존과 다르게 `Naitve`(Naitve ESM based dev server) 방식으로 처리되어 구동 속도가 매우 빠르다.
![alt text](image.png)

</details>
<br>

# Vue3 Vite 프로젝트 설치 및 기동
<details>
<summary>펼치기/접기</summary>
<br>

## 필수 요소
- Node.js (LTS)
- IDE: VSC 등

## 터미널 
- 설치 명령어 입력
  ```bash
  vue create vite@latest
  ```
- 프로젝트명 입력
  ```bash
  √ Project name: ... vue-simple-basic
  ```
- framework 선택 : 2번째 vue 선택
  ```bash
  ? Select a framework: » - Use arrow-keys. Return to submit.
      Vanilla
  >   Vue
      React
      Preact
      Lit
      Svelte
      Solid
      Qwik
      Angular
      Others
  ```
- 사용 언어 선택
  ```bash
  ? Select a variant: » - Use arrow-keys. Return to submit.
      TypeScript
  >   JavaScript
      Official Vue Starter ↗
      Nuxt ↗
  ```

- 설치 완료 후 최종 터미널 통합 출력 내용
  ```bash
  PS C:\Programming\workspace_vs> npm create vite@latest
  Need to install the following packages:
    create-vite@6.2.0
  Ok to proceed? (y) y
  √ Project name: ... {프로젝트명}
  √ Select a framework: » Vue
  √ Select a variant: » JavaScript

  Scaffolding project in C:\Programming\workspace_vs\vue-simple-basic...

  Done. Now run:

    cd vue-simple-basic
    npm install
    npm run dev
  ```

- VSC 실행
  ```bash
  code .
  ```
- node module 패키지 설치
  ```bash
  npm install
  ```
- vue 프로젝트 node 개발서버 실행
  ```bash
  npm run dev
  ```
</details>
<br>

# Vue3 관련 Extension
<details>
<summary>펼치기/접기</summary>
<br>

- Volar (Vue Language Feature)
  - Vue
- Vue 3 snippets
  - hollowtree
</details>
<br>

# 컴포지션 API 상태변수를 다루는 2가지 방법
<details>
<summary>펼치기/접기</summary>
<br>

Vue3 Composition API를 사용할 때 상태변수를 다루는 2가지 방법이 있다.  
ref와 reactive가 있다.  

두개중 어떤것을 사용해야 할까?  
원시값에 해당하는 숫자, 문자열 등의 상태 변수를 만들기 위해서는 ref() 함수를 사용해야 하며, 객체를 만드는 경우는 ref 또는 reactive 모두 사용이 가능하다.  
ref의 경우는 숫자, 문자 타입을 자유롭게 담을 수 있으며 심지어 객체도 담을 수 있다.  

### ref
template 태그 영역에서는 변수 선언만으로 접근이 가능하다.  
그러나 script 태그 영역에서는 ref라는 객체 안에 은닉되어 있기 때문에 바로 접근할 수 없다.  
따라서 변수명 뒤에 value라는 속성을 통해 `변수명.value`와 같이 접근해야만 한다.  
변수명 뒤에 value라는 속성이 붙기 때문에 상태변수라는 것을 직관적으로 알 수 있는 장점이 있다.  

- ref 예제코드
  ```vue
  <script setup>
    import {reactive} from 'vue'
    const count = ref(0);
    const str = ref('hello');
    const obj = ref({name: 'YooHyeok'});

    console.log(count); // ref라는 객체 안에 은닉이 되어 있기 때문에 바로 접근할 수 없다.
    console.log(count.value); // 0 출력 - 항상 ref변수는 value라는 속성으로 접근해야 한다.
  </script>
  <template>
    <p>{{ count }}</p>
    <p>{{ str }}</p>
    <p>{{ obj.name }}</p>
  </template>
  ``` 

### reactive
ref변수와는 다르게 reactive는 바로 접근이 가능하다.
바로 접근이 가능하기 때문에 script 태그 영역에서 자바스크립트 순수 Object인지 Vue의 reactive에서 가져오는지 햇갈릴 수 있다.  

- reactive 예제코드
  ```vue
  <script setup>
    import {reactive} from 'vue'
    const reactiveObj = reactive({name: 'YooHyeok'});

    console.log(reactiveObj); // reactive는 바로 접근이 가능하다.
  </script>
  <template>
    <p>{{ reactiveObj.name }}</p>
  </template>
  ``` 

</details>
<br>

# 02) 데이터 바인딩 - 정적 변수
<details>
<summary>펼치기/접기</summary>
<br>

데이터를 화면에 출력하는 것을 데이터 바인딩이라 하며, 데이터가 변경되었을 때 화면에 업데이트 되어야 한다.  
이런것들을 리액티브한 value값들 이라고 한다.  
Vue에서는 정적인 변수값과 리액티브한 변수값이 있을 수 있다.  

v-bind 디렉티브를 통한 데이터 바인딩으로 속성값이나, 텍스트노드 값들을 표시할 수 있다.  

특정 태그의 style등의 속성에 바인딩 하기 위해서는 v-bind를 통해 `v-bind:속성명="변수명"` 형태로 바인딩한다.  
텍스트노드의 경우 vue의 mustache 문법을 통해 `{{ 변수명 }}` 형태로 바인딩 한다.  
이는 vue2에서의 문법과 동일하다.  

vue2와의 차이점이라면 변수 선언이다.  
vue2에서는 정적 변수 선언시 export default {} 영역 바깥 상단에 변수를 선언해야 했다.  

## Vue2 예시코드
- components/Chapter02.vue
  ```vue
  <script>
    const myStyle = { color: 'red' } /* 정적 변수 */
    const title = "Chapter2" /* 정적 변수 */
    export default {
      name: "Chapter02"
    }    
  </script>
  <template>
    <h1 v-bind:style="myStyle"> <!-- style 속성에 바인딩 -->
      {{ title }} <!-- mustach 문법 활용 텍스트노드 바인딩 -->
    </h1>
  </template>
  ```

## Vue3 예시코드
- components/Chapter02.vue
  ```vue
  <script setup>
    import { ref } from 'vue';
    const myStyle = { color: 'red' } /* 정적 변수 */
    const title = "Chapter2" /* 정적 변수 */
  </script>
  <template>
    <h1 v-bind:style="myStyle"> <!-- style 속성에 바인딩 -->
      {{ title }} <!-- mustach 문법 활용 텍스트노드 바인딩 -->
    </h1>
  </template>
  ```
</details>
<br>

# 03) 데이터 바인딩 - 상태 변수
<details>
<summary>펼치기/접기</summary>
<br>

데이터 바인딩시 일반 변수를 사용하기도 하지만 값이 변했을 때 동시에 화면에 업데이트 되도록 반응성을 주기 위해서는 상태 변수를 사용해야 한다.  
일반 정적 변수와 상태 변수의 차이점에 대해 알아보자.  

먼저 일반 변수는 반응성을 갖지 않으며 값이 변경되더라도 화면이 자동으로 갱신되지는 않는다.  
예를들어 버튼을 클릭했을 때 값이 증가해서 화면에 업데이트 되는 로직을 구현해본다.  
- Chapter04.vue
  ```vue
  <script setup>
    let count = 0;
    const increment = () => {
      count++;
      alert(count)
    }
  </script>
  <template>
    <p>count: {{ count }}</p>
    <button @click="increment">Count++</button>
  </template>
  ```
일반 정적 변수는 값에 대한 추적이 발생되지 않으므로, 다시말해 vue에서 변경을 감지하지 않으므로 실제로 변경은 되지만 템플릿에는 반영되지 않는다.  


## ref 상태 변수 적용  
- Chapter04.vue
  ```vue
  <script setup>
    import { ref } from 'vue';
    const refCount = ref(0);
    const increment = () => {
      refCount.value++;
    }
  </script>
  <template>
    <p>refCount: {{ refCount }}</p>
    <button @click="increment">Count++</button>
  </template>
  ```

## 예외 현상
만약 정적 변수와 상태 변수 모두 템플릿에 선언한 뒤, 동일 시점의 트리거에 두 변수 모두 변경 될 경우 정적 변수도 함께 업데이트 된다.  
이는 상태변수가 변경될때 리랜더링 되면서, 정적 변수에 대한 변경된 값도 함께 반영이 되는것이다.  
단 값에대한 추적 즉, 값 변경에 대한 감지는 상태변수에만 해당된다.  
상태변수의 값 변경이 감지가 되어 리랜더링되면서, 변경된 정적 변수 값도 함께 새롭게 반영된 것이다.  

- Chapter04.vue
  ```vue
  <script setup>
    import { ref } from 'vue';
    let count = 0;
    const refCount = ref(0);
    const increment = () => {
      count++;
      refCount.value++;
      alert(count)
    }
  </script>
  <template>
    <p>count: {{ count }}</p>
    <p>refCount: {{ refCount }}</p>
    <button @click="increment">Count++</button>
  </template>
  ```

template에서 반응형 변수를 제거할 경우 Vue는 해당 변수를 더이상 추적하지 않게 된다.  
따라서 정적 count 변수는 반응형으로 동작하지 않게 된다.  
이는 Vue의 반응형 시스템이 템플릿에서 사용된 변수만 추적하기 때문이다.  
- Chapter04.vue
  ```vue
  <script setup>
    import { ref } from 'vue';
    let count = 0;
    const refCount = ref(0);
    const increment = () => {
      count++;
      refCount.value++;
      alert(count)
    }
  </script>
  <template>
    <p>count: {{ count }}</p>
    <button @click="increment">Count++</button>
  </template>
  ```
</details>
<br>

# 04_01 v-for 반복문
<details>
<summary>펼치기/접기</summary>
<br>

vue2에서 사용법과 동일하다.  
단, 특정 이벤트 트리거의 데이터 조작을 통해 목록을 구성하는 list 변수의 값 변화에 의해 리렌더링이 발생 한다면 컴포지션 API를 사용하는 vue3 에서는 상태 변수를 사용해야 한다.

- src/Chapter04_01.vue
  ```vue
  <script setup>
    const foodObjs = [
      { id: 1, name: 'apple' },
      { id: 2, name: 'banana' },
      { id: 3, name: 'mango' }
    ]
  </script>
  <template>
    <h1>반복문</h1>
    <ul>
      <li 
        v-for="(food) in foodObjs"
        :key="food.id"
      >
        {{ food.id }}: {{ food.name }}
      </li>
    </ul>
  </template>
  ```

</details>
<br>

# 04_02 v-if 조건부 렌더링
<details>
<summary>펼치기/접기</summary>
<br>

vue2에서 사용법과 동일하다.
단, 조건을 구성하는 값 변화에 의한 리랜더링을 통해 작동되기 때문에 조건에 바인딩되는 변수의 경우 컴포지션 API를 사용하는 vue3 에서는 상태 변수를 사용해야 한다.
- src/Chapter04_02.vue
  ```vue
  <script setup>
  import { ref } from 'vue';

  const isOpen = ref(true);
  const closeModal = () => {
    isOpen.value = false
  }

  </script>
  <template>
    <h1>조건부 랜더링(Conditional Redering)</h1>
    <div class="modal" v-if="isOpen">
      <h2>Notice</h2>
      <p>50% off today</p>
      <button @click="isOpen=false">close</button>
      <button @click="closeModal">close</button>
    </div>
  </template>
  <style scoped>
  .modal {
    background-color: #ccc;
    padding: 1rem;
    h2 { margin: 0; color: red; }
  }
  </style>
  ```

</details>
<br>

# 컴포넌트와 Props
<details>
<summary>펼치기/접기</summary>
<br>

## 컴포넌트란? 
재활용 가능한 레고 블럭 같은 것이다.  
홈페이지에서 헤더나 푸터 같이 공통적으로 사용하는 영역은 컴포넌트로 만든다.  
vue3에서는 이런 컴포넌트를 쉼게 만들 수 있으며 뿐만아니라 props를 통해 부모와 자식 컴포넌트 간의 데이터를 주고 받을 수도 있다.  

## Props
부모와 자식 컴포넌트 간에 데이터를 전달할때 사용하는 속성이다.

### 예제1) 컴포넌트화(분리) 및 참조

초기 컴포넌트는 아래와 같다.  
- Chapter05.vue
  ```vue
  <template>
    <header>
      <h1>Header</h1>
    </header>
    <h1>Content</h1>
  </template>
  ```

header 태그 영역을 Header.vue라는 컴포넌트로 컴포넌트화 한다.  
- Header.vue
  ```vue
  <template>
    <header>
      <h1>Header</h1>
    </header>
  </template>
  ```

Header.vue 컴포넌트를 기존 Chapter05.vue 컴포넌트에서 컴포넌트를 참조한 뒤 template 태그 영역에 import한 자식 태그를 선언한다.  
이때 참조하는 컴포넌트는 부모가 되고, 참조되는 컴포넌트는 자식이 된다.  
- Chapter05.vue
  ```vue
  <script setup>
    import Header from './Header.vue'

  </script>
  <template>
    <Header />
    <h1>Content</h1>
  </template>
  ```
  
### 예제2) 부모-자식 컴포넌트 관계에서 props 전달
부모 컴포넌트에서 자식 컴포넌트로 props를 넘기는것은 vue2와 동일하다.  
컴포넌트 태그에 넘기려는 속성의 속성명을 입력하고, 쌍따옴표 안에 값을 채운다.  
변수 값을 바인딩 하려면 v-bind를 속성 앞에 적용하여 `v-bind:속성명="변수명 "` 문법 형태로 적용한다.
- Chapter05.vue
  ```vue
  <script setup>
    import Header from './Header.vue'
  </script>
  <template>
    <Header title="header component" />
    <h1>Content</h1>
  </template>
  ```

부모 컴포넌트로부터 넘겨받은 props를 자식 컴포넌트에서 받는 vue3의 컴포지션 API 문법은 vue2와는 조금 다르다.  
vue 전역 패키지로부터 defineProps() 함수를 import 하여 함수를 호출하며 변수에 할당한다.  
해당 함수의 매개변수로 부모컴포넌트에서 넘긴 속성을 객체 리터럴 형태의 문법과 유사하게 선언한다.  
이때 `{ props속성명: 타입 }` 형태로 타입을 지정해준다.  
선언이 완료되면, script태그와 template태그에서 자유롭게 사용이 가능해진다.  
단, 값의 변경은 자식컴포넌트에서는 불가능하다. (객체타입은 가능...)
- Header.vue
  ```vue
  <script setup>
    import { defineProps } from 'vue'
    const props = defineProps({
      title: String;
    })
  </script>
  <template>
    <header>
      <h1>{{ props.titie }}</h1>
    </header>
  </template>
  ```

</details>
<br>

# 이벤트와 v-model
<details>
<summary>펼치기/접기</summary>
<br>

Event란 주로 사용자 인터페이스에서 사용자와의 상호작용. 예를들어 클릭이나 입력 등이 발생했을 때  
이를 처리하기 위해 이벤트를 발생시키고 필요한 기능을 동작시키고 하는 것을 의미한다.  

#### 버튼을 클릭하면 카운터를 증가시키는 앱을 만들어본다.  

초기값이 0인 상태변수 count를 추가하고 button 태그에 이벤트를 추가하도록 한다.  
`v-on:이벤트명` 문법 혹은 축약문법인 `@이벤트명`으로 count변수를 증가시키는 실행문을 속성에 등록한다.
- Chapter06.vue
  ```vue
  <script setup>
    import { ref } from 'vue'
    const count = ref(0); // 상태변수 추가

  </script>
  <template>
    <button @click="count++">{{ count }}</button> <!-- button태그 추가 및 실행문 바인딩 -->
  </template>
  ```

#### 사용자의 입력을 받는 input요소를 만들어 본다.

초기값이 null인 상태변수 inputValue를 추가하하고 text type의 input 태그에 이벤트를 추가하도록 한다.  
text type의 input 태그를 선언한 뒤 `v-on:이벤트명` 문법 혹은 축약문법인 `@이벤트명`으로 입력 받은 내용을 inputValue에 초기화하는 handleInput() 함수를 @이벤트 속성에 등록한다.
- Chapter06.vue
  ```vue
  <script setup>
    import { ref } from 'vue'
    const count = ref(0);
    const inputValue = ref(''); // 상태변수 추가
    const handleInput = (e) => { // 이벤트 바인딩 함수 추가
      inputValue.value = e.target.value
    }
  </script>
  <template>
    <button @click="count++">{{ count }}</button>
    <br>
    <p>{{ inputValue }}</p>
    <input type="text" @input="handleInput" /> <!-- input 태그 추가 및 함수 바인딩 -->
  </template>
  ```
이렇게 까지만 하면 기능은 정상적으로 작동되지만 단방향으로 데이터가 전달된다.  
양방향으로 데이터가 전달되도록 하기 위해서는 input 태그에 상태변수 inputValue를 꼭 바인딩 해줘야만 한다.
위 방식은 js의 일반적인 텍스트 입력 필드에서 사용하는 input 이벤트와 핸들러 방식과 동일하다.  

vue에서는 이 방식 말고 v-model이라는 디렉티브를 사용하면 더 간단하게 다룰 수 있다.  

#### v-model을 적용해본다.

사용 문법은 vue2와 동일하다.
`<input type="text" v-model="상태변수명">` 과 같이 v-model에 상태변수만 바인딩해주면 된다

- Chapter06.vue
  ```vue
  <script setup>
    import { ref } from 'vue'
    const count = ref(0);
    const inputValue = ref('');
    const handleInput = (e) => {
      inputValue.value = e.target.value
    }
    const modelValue = ref(''); // 상태변수 추가
  </script>
  <template>
    <button @click="count++">{{ count }}</button>
    <br>
    <p>inputValue: {{ inputValue }}</p>
    <input type="text" @input="handleInput" />
    <br>
    <p>modelValue: {{ modelValue }}</p>
    <input type="text" v-model="modelValue" /> <!-- input 태그 추가 및 v-model 상태변수 바인딩 -->
  </template>
  ```

</details>
<br>

# Lifecycle Hooks
<details>
<summary>펼치기/접기</summary>
<br>

라이프사이클은 컴포넌트가 `생성`되고 `업데이트`되며 `제거`되는 과정을 의미한다.  
vue에서컴포넌트는 각 단계마다 특정 이벤트를 검사하는데 이를 통해 개발자는 컴포넌트가 동작하는 특정 시점에서 필요한 코드를 실행할 수 있다.  
주로 사용하는 라이프사이클 훅 두가지가 있다.

onMounted는 컴포넌트가 DOM에 마운트된 후 실행되는 함수이다.  
보통 서버에서 데이터를 가져오는 사전 작업에서 사용한다.  

onUnmounted는 컴포넌트가 제거될 때 실행되는 이다.  
보통 타이머라고 하는 setInterval같이 주기적으로 프로그램을 실행하는 처리문들은 메모리에서 계속 동작을 하기 때문에 컴포넌트가 종료되는 시멎에서 메모리를 초기화하는 시점에서 사용할 수 있다.  

### onMounted
  - 컴포넌트가 DOM에 마운트된 후 실행되는 함수
  - 서버에서 데이터를 가져오는 작업등에 사용
### onUmMounted
  - 컴포넌트가 DOM에서 언마운트 될 때 실행되는 함수
  - 타이머 해제, setInterval로 주기적인 작업을 처리하고 컴포넌트가 언마운트될 때 이를 중지해야한다.
  - 기타 컴포넌트가 종료될 때 메모리 초기화가 필요한 경우 사용

## Modal 컴포넌트 조건부 렌더링 예제

먼저 부모컴포넌트에 출력될 Modal.vue 컴포넌트를 생성한다.
- Modal.vue
  ```vue
  <script setup>
  </script>
  <template>
    <div class="modal">
      <h2>Modal</h2>
      <p>모달입니다.</p>
    </div>
  </template>
  ```

다음으로 부모 컴포넌트에 Modal 컴포넌트를 적용하고, 토글 버튼 태그에 조건부 렌더링을 적용할 상태 변수값을 click이벤트로 반전 초기화 되도록 적용한 뒤 Modal 컴포넌트를 해당 값을 통해 조건부 렌더링 되도록 v-if 디렉티브를 적용하여 컴포넌트를 구현한다.
- Chapter07.vue
  ```vue
  <script setup>
  import Modal from './Modal.vue';
  import { ref } from 'vue';

  const isModal = ref(true)
  </script>
  <template>
    <div>
      <Modal v-if="isModal"/>
      <button @click="isModal=!isModal">toggle</button>
    </div>
  </template>
  <style scoped>
    .modal {
      background: #ccc;
      padding: 1rem;
    }
  </style>
  ```

Modal이 출력되는것은 Modal 컴포넌트가 Mount된것이다.
그리고 토글버튼을 클릭하여 Modal이 사라지는것은 UnMount된것이다.

이는 라이프사이클 훅으로 확인이 가능하다.
훅이 걸리면 우리가 원하는 추가할수 있게 된다.

## Modal 컴포넌트 훅 적용

- Modal.vue
  ```vue
  <script setup>
  import { onMounted, onUnmounted } from 'vue';
  onMounted(() => {
    console.log("Mounted")
  })
  onUnmounted(() => {
    console.log("Unmounted")
  })

  console.log("setup")
  </script>
  <template>
    <div class="modal">
      <h2>Modal</h2>
      <p>모달입니다.</p>
    </div>
  </template>
  ```

위와같이 onMounted, onUnmounted 훅을 적용하고 콜백 함수에 해당 라이프사이클인 경우 로직일 실행할 수 있도록 출력 로그를 작성해본다.

***참고로 vue2의 created훅은 vue3에서 setup함수로 대체된다.***
</details>
<br>

# 컴포넌트간 양방향 데이터 전달
<details>
<summary>펼치기/접기</summary>
<br>

## 방법 01 - Emit(defineEmit)
<details>
<summary>펼치기/접기</summary>
<br>

사용법은 vue2와 동일하다.  
다만 컴포지션 API 방식을 사용할때 자식컴포넌트에서 문법이 조금 수정되었다.  
기존 this.$emit()으로 어디서나 접근이 가능하던 문법은 사용이 불가능하며, defineProps라는 내장 함수로 제공한다.  
부모 컴포넌트에서 `@emit이름=함수` 로 정의하였다면  
자식 컴포넌트에서는 `const emits = defineEmits(['emit이름'])` 과 같이 사용한다.  

### 부모컴포넌트
- appendix/Parent01
  ```vue
  <script setup>
  import { ref } from 'vue';
  import Child01 from './Child01.vue';

  let title = ref('title')
  </script>
  <template>
    <h1>Parent</h1>
    <p>ref: {{ title }}</p>
    <Child01 
      :title="title"
      @onInput="(value) => { title = value } /* emit 이름: onInput */" 
    />
  </template>
  ```
### 자식컴포넌트
- appendix/Child01
  ```vue
  <script setup>
  import { ref, defineProps, defineEmits } from 'vue';
    const props = defineProps( {title: String} );
    const emits = defineEmits( ['onInput'] ); /* emit 이름: onInput */
  </script>
  <template>
    <h2>Child</h2>
    <p>props: {{ props.title }}</p>
    <input 
      type="text" 
      :value="props.title" 
      @input=" 
        inputText = $event.target.value;
        emits('onInput', inputText)
      "
    >
  </template>
  ```

## Object 타입 props 프로퍼티 직접 수정  
vue2와 동일하게 Object 타입의 props의 프로퍼티에 직접 접근하여 수정이 가능하다.  
하지만 template영역에서 v-model로만 수정이 가능하며, script영역에서는 value로 접근하더라도 부모영역에 갱신되지 않는다.
### 부모컴포넌트
- appendix/Parent02
  ```vue
  <script setup>
  import { ref } from 'vue';
  import Child from './Child02.vue';

  let title = ref({title: 'title'})
  </script>
  <template>
    <h1>Parent ref: {{ title.title }}</h1>
    <Child :title="title"/>
  </template>
  ```
### 자식컴포넌트
- appendix/Child02
  ```vue
  <script setup>
  import { defineProps } from 'vue';
    const props = defineProps({
      title: Object
    });
    console.log(props.title.title)
    props.title.title="멍충아" /* 부모 ref 갱신 불가 */
    props.title.title.value="멍충아" /* 부모 ref 갱신 불가(오류발생) */
  </script>
  <template>
    <h2>Child02</h2>
    <input type="text" v-model="props.title.title"> <!-- 부모 ref 갱신 가능 -->
  </template>
  ```
</details>
<br>

## 방법 02 - v-model(defineModel)
<details>
<summary>펼치기/접기</summary>
<br>

vue3에 새로운 방법이 추가되었다.  
부모 컴포넌트에서 v-model로 ref를 바인딩한다.  
자식 컴포넌트에서는 defineModel이라는 내장함수를 통해   

### 부모컴포넌트
- appendix/Parent03
  ```vue
  <script setup>
  import { ref } from 'vue';
  import Child02 from './Child02.vue';

  let title = ref('title')
  </script>
  <template>
    <h1>Parent02</h1>
    <p>ref: {{ title }}</p>
    <Child02 v-model="title" />
  </template>
  ```
### 자식컴포넌트
- appendix/Child03
  ```vue
  <script setup>
  import { defineModel } from 'vue';
    const model = defineModel();
  </script>
  <template>
    <h2>Child02</h2>
    <p>props: {{ model }}</p>
    <input 
      type="text" 
      v-model="model"
    >
  </template>
  ```

defineModel에 의해 반환되는 값은 ref이다.  
다른 ref처럼 value 속성을 통해 접근하여 값을 변경할 수 있고, 부모 값과 로컬 값 사이의 양방향 바인딩으로 작동하게 된다.  
vue2에서 props는 primitive한 값에 대해서는 직접 수정이 되지 않았으나, Object 타입의 props를 전달받아 해당 객체의 프로퍼티를 수정하는것은 부모에도 반영이 되었었다.  
vue3에서는 해당 기능으로 primitive한 값 조차도 수정할 수 있게 제공해준다.  
물론 공식 문서에서 이를 직접 설명해준다. 지양하라는 경고조차 없다!  
### 자식컴포넌트
- appendix/Child01
  ```vue
  <script setup>
  import { defineModel } from 'vue';
    const model = defineModel();
    model.value="메롱" // 부모 컴포넌트의 v-model로 바인딩 된 ref에 반영이 된다.
  </script>
  <template>
    <h2>Child02</h2>
    <p>props: {{ model }}</p>
    <input 
      type="text" 
      v-model="model"
    >
  </template>
  ```
</details>
<br>

</details>
<br>

# 템플릿
<details>
<summary>펼치기/접기</summary>
<br>

</details>
<br>
