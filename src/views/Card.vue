<template>

  <div>
  <div class="card" v-for="(item, index) in cards"
          :body="item.body"
          :key="item.id"
          :cardIndex="index"
          :listIndex="listIndex">
    
    <button class="close-button" @click="removeCardFromList">
      ×
    </button>
      
    <!-- <button @click="editCard">更新</button> -->
        
    <div class="body">
      {{ body }}
    </div>

    <!-- <modal name="user-modal">
      <h2>ユーザ登録</h2>
    </modal> -->

  </div>
  </div>
</template>

<script>
  export default {
    created() {
    this.cards = this.$store.state.lists.cards;
  },
    /* props: {
      body: {
        type: String,
        required: true
      },
      listIndex: {
        type: Number,
        required: true
      },
      cardIndex: {
        type: Number,
        required: true
      }
    }, */
    data() {
      return {
        cards: [],
      }
    },
    methods: {
      removeCardFromList() {
        if (confirm('本当にこのカードを削除しますか?')) {
          this.$store.dispatch('removeCardFromList', { cardIndex: this.cardIndex, listIndex: this.listIndex })
        }
      }/* ,
      editCard() {
        this.createFlag = false,
        this.$modal.show('user-modal');
      },
      showModal() {
        this.$modal.show('user-modal');
      }, */
    },
  }
</script>