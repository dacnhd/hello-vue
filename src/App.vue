<template>
  <div id="app">
    <h1>Hello World</h1>
    <p>{{message}}</p> <!-- data -->
    <p>{{worldHello}}</p> <!-- computed -->
    <div v-if="isActive == true"> <!-- data, v-if, v-else -->
      This is Active
    </div>
    <div v-else>
      This is Deactive
    </div>
    <button @click="isActive = !isActive">IsActive</button>
    <div id="list"> <!-- data, v-for -->
      <ul>
        <li v-for="st in student">
          {{st.name}}
        </li>
      </ul>
    </div>
    <button @click="helloWorld">Click</button> <!-- methods -->
    <Student :message="message" @changeMessage="message = 'dac'"/> <!-- components -->
  </div>
</template>

<script>
import Student from './views/Student.vue' //components

export default {
  components:{ //components
    Student
  },
  data(){ //data
    return{
   
      message: 'Hello World',
      isActive: true,
      student: [
        {name: 'nguyen'},
        {name: 'huu'},
        {name: 'dac'}
      ]
    }
  },
  methods:{ //methods(cac phuong thuc duoc thuc thi khi duoc goi den)
    helloWorld(){
      this.message += ' dac',
      alert('Hello World')
    }
  },
  computed:{ //computed(khong co tham so dau vao, nen dung voi data co san trong component)
    worldHello(){
      return this.message + ' dac'
    }
  },
  watch:{   //watch message(quan sat su thay doi cua message, neu message thay doi thi thuc thi lenh)
    message(){
      alert('message changed')
    }
  }
}
</script>