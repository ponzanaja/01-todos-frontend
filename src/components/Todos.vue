<template>
  <div>
    <div v-for="(todo, index) in todos" :key="todo.title" v-if="visibility === 'all' ">
      <b-field class="is-pulled-left">
        <b-checkbox size="is-large" @input="changeComplete({index,completed:$event})" :value="todo.completed">
          <strike v-if="todo.completed">{{ todo.title }}</strike>
          <div v-else>{{ todo.title }} </div>
        </b-checkbox>
      </b-field>
      <a class="delete is-pulled-right" @click="removeTodo(index)"></a>
      <div class="is-clearfix"></div>
    </div>

    <div v-for="(todo, index) in todos" :key="todo.title" v-if="visibility === 'active' ">
      <div v-if="todo.completed === false ">
        <b-field class="is-pulled-left">
        <b-checkbox size="is-large" @input="changeComplete({index,completed:$event})">
          <strike v-if="todo.completed">{{ todo.title }}</strike>
          <div v-else>{{ todo.title }} </div>
        </b-checkbox>
      </b-field>
      <a class="delete is-pulled-right" @click="removeTodo(index)"></a>
      <div class="is-clearfix">
        
      </div>
      </div>
      
    </div>

    <div v-for="(todo, index) in todos" :key="todo.title" v-if="visibility === 'completed' ">
     <div v-if="todo.completed === true ">
      <b-field class="is-pulled-left">
        <b-checkbox size="is-large" @input="changeComplete({index,completed:$event})" :value="true">
          <strike v-if="todo.completed">{{ todo.title }}</strike>
          <div v-else>{{ todo.title }} </div>
        </b-checkbox>
      </b-field>
      <a class="delete is-pulled-right" @click="removeTodo(index)"></a>
      <div class="is-clearfix"></div>
      </div>
    </div>
<button class="button" @click="deleteComplete()"> Delete Completed </button>
  </div>
 
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  computed: {
    ...mapGetters(['todos', 'visibility'])
  },
  methods: {
    ...mapActions(['removeTodo', 'changeComplete', 'deleteComplete'])
  }
}
</script>
