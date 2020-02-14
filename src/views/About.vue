<template>
  <div class="about">
    <input type="text" v-model="msg"><br/>
    <ul>
      <li v-for="(user, index) in users" :key="index">{{ user.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'about',
  data(){
    return {
      msg: '',
      users: [
        {
          name: '快车',
          tag: '1'
        },
        {
          name: '大车',
          tag: '2'
        },
        {
          name: '小车',
          tag: '3'
        },
        {
          name: '快小车',
          tag: '4'
        }
      ]
    }
  },
  filters: {
    formatId: function(value){
      console.log(value)
    }
  }
}
</script>