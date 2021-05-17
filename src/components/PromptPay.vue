<template>
  <div class="container">
    <div class="row" v-if="qrCODE">
      <div class="col-sm"></div>
      <div class="col-sm">
        <center>
          <vue-qrcode v-bind:value="this.qrCODE" />
        </center>
      </div>
      <div class="col-sm"></div>
    </div>
    <div class="row">
      <div class="col-sm"></div>
      <div class="col-sm">
        <div class="mb-3">
          <label for="promptpayID" class="form-label"
            >เลขพร้อมเพย์</label
          >
          <input
            type="text"
            placeholder="0628888888"
            class="form-control"
            id="promptpayID"
            required
            autofocus
            v-model="PromptPayID"
            :readonly="status"
          />
        </div>
        <div class="mb-3">
          <label for="amount" class="form-label">จำนวนเงิน</label>
          <input
            type="number"
            min="1"
            placeholder="100"
            class="form-control"
            id="amount"
            required
            v-model="Amount"
            :readonly="status"
          />
        </div>
        <div class="d-grid gap-2">
          <button type="submit" class="btn btn-primary" v-on:click="getPromptPay()">สร้าง QR CODE</button>
        </div>
      </div>
      <div class="col-sm"></div>
    </div>
    <div class="row">
      <p>Created by <a href="https://github.com/RNCAT" target="_blank" style="">RennyCat</a></p>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import VueQrcode from 'vue-qrcode'
export default {
  name: "PromptPay",
  components: {
    VueQrcode,
  },
  data() {
    return {
      PromptPayID: '',
      Amount: null,
      qrCODE: '',
      status: false,
      apiURL: 'https://rncat-promptpay.herokuapp.com/promptpay'
    }
  },
  methods: {
    async getPromptPay() {
      const result = await axios.post(this.apiURL, {
          'promptpay_id': this.PromptPayID,
          'amount': Number(this.Amount)
      })

      this.qrCODE = result.data.PromptPay
      this.status = true
    }
  }
}
</script>

<style scoped>

label {
  float: left;
}

p {
  margin-top: 10px;
  text-align: center;
}
a {
  color: black;
  font-weight: bold;
  text-decoration: none;
}
</style>
