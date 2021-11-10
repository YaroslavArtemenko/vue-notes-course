<template>
  <div class="wrapper">

    <div class="wrapper-content">

      <section>
        <div class="container">
          <h1>{{ title }}</h1>

          <Message
              v-if="message"
              :message="message"
          >
          </Message>

          <!-- new note -->
          <NewNote
              :note="note"
              @addNote="addNote"
          >
          </NewNote>

          <!-- note list-->
          <Notes
              :notes="notes"
          >
          </Notes>
        </div>

      </section>

    </div>

  </div>
</template>

<script>

import Message from './components/Message.vue'
import NewNote from "./components/NewNote";
import Notes from "./components/Notes";

export default {
  components: {
    Notes,
    NewNote,
    Message
  },
  data() {
    return {
      title: 'Notes App',
      message: null,
      note: {
        title: '',
        descr: ''
      },
      notes: [
        {
          title: 'First Note',
          descr: 'Description for first note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Second Note',
          descr: 'Description for second note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Third Note',
          descr: 'Description for third note',
          date: new Date(Date.now()).toLocaleString()
        }
      ]
    }
  },
  methods: {
    addNote () {
      // console.log(this.note)
      let {title, descr} = this.note
      if (title === '') {
        this.message = 'title cant be blank'
        return false
      }
      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleString()
      })
      this.message = null
      this.note.title = ''
      this.note.descr = ''
    }
  }
}
</script>

<style>

</style>
