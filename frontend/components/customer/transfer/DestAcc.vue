<template>
  <v-layout row align-center>
    <v-flex grow>
      <v-select
        v-model="bank"
        :items="banks"
        item-value="id"
        item-text="name"
        label="Bank"
      />
      <v-text-field v-model="acc" label="Account No." />
    </v-flex>
    <v-flex shrink>
      <contact @selected="fill" />
    </v-flex>
  </v-layout>
</template>

<script>
import Contact from './Contact'

export default {
  components: {
    Contact
  },
  data: () => ({
    bank: null,
    acc: null,
    banks: [
      {
        id: 1,
        name: 'Korbboon Bank Co, Ltd.'
      }
    ]
  }),
  methods: {
    fill(val) {
      this.bank = val.bankId
      this.acc = val.acc
    }
  }
}
</script>
