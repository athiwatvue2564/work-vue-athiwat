<template>
  <div class="rounded-xl white text-center">
    <p class="txt1">
      Sign up your bank account
    </p>
    <center>
      <v-form>
        <v-container>
          <v-text-field
            v-model="username"
            label="Your Name"
            placeholder="Your Name"
            outlined
            dense
            class="text-green"
          />
          <v-text-field
            v-model="bacount"
            label="Bank Account"
            outlined
            dense
            class="text-green"
          />
          <v-text-field
            v-model="mobile"
            label="Mobile phone number"
            outlined
            dense
            class="text-green"
          />
          <v-text-field
            v-model="email"
            label="Email"
            outlined
            dense
            class="text-green"
          />
          <v-text-field
            v-model="passwd"
            label="Password"
            outlined
            dense
            class="text-green"
          />
          <p class="txt2">
            Use 6 characters with a mix of numbers
            and letters
          </p>
          <!-- <v-checkbox
          label="By signing up, you agree to
Bank’s Term of Use & Privacy Policy."
          color="info"
          value="red darken-3"
          class="black-label"
        /> -->
          <v-dialog
            v-model="dialog"
            width="500"
          >
            <v-card>
              <v-card-title class="text-h5 grey lighten-2">
                SUCCEES
              </v-card-title>

              <v-card-text>
                Register OK
              </v-card-text>

              <v-divider />
            </v-card>
          </v-dialog>

          <v-dialog
            v-model="failed"
            width="500"
          >
            <v-card>
              <v-card-title class="text-h5 grey lighten-2">
                REGISTER ERROR
              </v-card-title>

              <v-card-text>
                USER or PASSWORD
              </v-card-text>

              <v-divider />
            </v-card>
          </v-dialog>

          <input type="checkbox" name="checkbox" m-model="chk" value="checkbox">
          <label class="lbl">By signing up, you agree to
            Bank’s Term of Use & Privacy Policy</label>
        </v-container>
        <v-row>
          <v-col md="12">
            <v-btn
              small
              class="btn1"
              @click="Save"
            >
              <span class="txt3">SIGN UP </span>
            </v-btn>
            <span class="txt3">or </span>
            <v-btn
              small
              outlined
              color="indigo"
              onclick="Clear"
            >
              <span class="txt3">CANCEL </span>
            </v-btn>
          </v-col>
        </v-row>
      </v-form>
      <p style="color:#000;margin-top:20px;">
        Already signed up?
        <nuxt-link to="/signup">
          Log in
        </nuxt-link>
      </p>
    </center>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data: () => ({
    username: '',
    bacount: '',
    mobile: '',
    email: '',
    passwd: '',
    chk: '',
    dialog: false,
    failed: false
  }),
  methods: {
    async Save () {
      const std = {
        username: this.username,
        bacount: this.bacount,
        mobile: this.mobile,
        email: this.email,
        passwd: this.passwd,
        chk: this.chk
      }
      console.log('user:', std)
      const res = await axios.post('http://localhost:7001/save', std)
      console.log(res.data)
      try {
        if (res.data.status === 1) {
          console.log('SUCCEES OK')
          this.dialog = true
          setInterval(() => {
            this.dialog = false
          }, 3000)
          this.$router.push('/test_signup')
        } // if
      } /* try */ catch (error) {
        if (res.data.status === 0) {
          console.log('Error Register')
          this.failed = true
          setInterval(() => {
            this.failed = false
          }, 3000)
          this.$router.push('/test_signup')
        } // if
      } // catch
    }

  }
}

</script>
<style>
.btn1{
   background: linear-gradient(to bottom,#FFEB3B,#FFC107);
}
.txt1{
    color: #5462ff;
    padding-top: 20px;
}
.txt2{
    color: #5462ff;
    font-size: 8px;
}
  .v-text-field--outlined fieldset {
    color: #A6A6A4 !important;
    height: 40px;
  }
  .text-green input {
        color: #A6A6A4 !important;
  }
 .black--text /deep/ label {
      color: black;
  }
  .v-text-field{
      width: 250px;
}
  .txt3{
    color: #411F1F;
  }
  .rounded-xl{
    padding-bottom:35px;
  }
  .black-label label {
    color: rgba(0, 0, 0) !important;
    font-size: 12px;
}
.lbl{
  color:black;
  font-size: 12px;
}
</style>
