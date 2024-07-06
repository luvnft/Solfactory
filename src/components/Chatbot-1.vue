<template>
  <div class="chatbot">
    <div class="messages">
      <div v-for="(message, index) in messages" :key="index" class="message">
        <strong>{{ message.user ? 'You' : 'Bot' }}:</strong> {{ message.text }}
      </div>
    </div>
    <input v-model="input" @keyup.enter="sendMessage" placeholder="Type your message" />
    <button @click="sendMessage">Send</button>
  </div>
</template>

<script>
const axios = require('axios');
console.log('API Key:', process.env.OPENAI_API_KEY); 
require('dotenv').config();


// Define the prompt
const prompt = `Hello`;

// Make the API call
axios.post('https://api.openai.com/v1/completions', {
    prompt: prompt,
    max_tokens: 1024,
    temperature: 0.5
  },
  {
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${process.env.OPENAI_API_KEY}`
    }
  }
)
.then(response => {
    // Extract the generated text from the API response
    const generatedText = response.data.choices[0].text;
    console.log(generatedText)
  })
  .catch(error => {
    console.log(error);
  });



  
</script>

<style scoped>
.chatbot {
    position: fixed;
    bottom: 0;
    right: 50%;
    left: 45%;
    width: 300px;
    background: #fff;
    border: 1px solid #ccc;
    padding: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .1);
    border-radius: 12px 12px 0px 0px;
}

.messages {
  max-height: 200px;
  overflow-y: auto;
  margin-bottom: 10px;
}

.message {
  margin-bottom: 5px;
}
</style>