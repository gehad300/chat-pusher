<template>
  <div class="input-group">
    <input
      id="btn-input"
      type="text"
      name="message"
      class="form-control input-sm"
      placeholder="Type your message here..."
      v-model="newMessage"
      @keyup.enter="sendMessage"
    />
    <span class="input-group-btn">
      <button class="btn btn-primary btn-sm" id="btn-chat" @click="sendMessage">
        Send
      </button>
    </span>
  </div>
</template>
<script>
export default {
  //Takes the "user" props from <chat-form> … :user="{{ Auth::user() }}"></chat-form> in the parent chat.blade.php.
  props: ["user"],
  data() {
    return {
      newMessage:""
    };
  },
  methods: {
    sendMessage() {
      this.$emit("messagesent", {
        user: this.user,
        message: this.newMessage,
      });
      //Clear the input
      this.newMessage = "";
    },
  },
};
</script>
