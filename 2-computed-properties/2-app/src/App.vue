<script setup>
  import { ref, computed } from 'vue'

  const newItem = ref('')
  const characterCount = computed(() => {
    return newItem.value.length
  })
  const firstName = ref('Bruce')
  const lastName = ref('Wayne')
  const fullname = computed({
    
    //accesseur
    get() {
      return firstName.value + ' ' + lastName.value
    }
  })
</script>

<template>
  <form>
    <fieldset>
      <label for="text">TextArea</label>
      <textarea maxlength="200" autofocus cols="40" rows="5" v-model="newItem" placeholder="Insert your message"></textarea>
      <p>Nombre de caractères restants : <span>{{ characterCount }} / 200</span></p>
    </fieldset>
  </form>
  <br>
  <div class="fullname">
    <p>Le nom complet est : <span>{{ firstName }} {{ lastName }}</span></p>
    <p>Le nom complet est : <span>{{ fullname }}</span> (version computed)</p>
  </div>
</template>

<style scoped>
form {
  font-family: sans-serif;
  font-size: 24px;
  padding: 24px;
}
fieldset {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  border: 1px solid grey;
  border-radius: 10px;
  padding: 24px;
}
  textarea {
    resize: none;
    font-size: 18px;
    font-family: 'Monaco', Courier, monospace;
    padding: 12px;
  }
  p {
    font-size: 14px;
    color: grey;
  }
  fieldset p span {
    font-weight: 600;
  }
  .fullname p {
    font-size: 24px;
    color: brown;
    font-family: sans-serif;
    text-align: center;
  }
  .fullname p span {
    font-weight: 800;
  }
</style>
