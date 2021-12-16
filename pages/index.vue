<template>
  <div>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <div class="pa-7 white rounded-circle d-inline-block">
          <v-icon large color="blue">
            mdi-cloud-upload
          </v-icon>
        </div>
      </v-col>
    </v-row>
    <h1 style="margin-top:20px;">
      JNBC BANK
    </h1>
    <h3>MOBILE APP</h3>

    <v-form>
      <v-container>
        <v-row>
          <v-col
            cols="12"
            sm="6"
            md="4"
          >
            <v-menu transition="scroll-y-transition">
              <template #activator="{ on, attrs }">
                <v-text-field
                  v-model="user"
                  label="PLEATE ENTER USER NAME"
                  placeholder="User"
                  filled
                  rounded
                  dense
                  v-bind="attrs"
                  v-on="on"
                />
                <v-text-field
                  v-model="pass"
                  label="PLEATE ENTER YOUR PASSWORD..."
                  placeholder="Password"
                  filled
                  rounded
                  dense
                  v-bind="attrs"
                  v-on="on"
                />
                <v-dialog
                  v-model="dialog"
                  width="500"
                >
                  <v-card>
                    <v-card-title class="text-h5 grey lighten-2">
                      WELCOME LOGIN
                    </v-card-title>

                    <v-card-text>
                      SUCCEEC LOGIN {{ fname }}
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
                      LOGIN ERROR
                    </v-card-title>

                    <v-card-text>
                      USER or PASSWORD
                    </v-card-text>

                    <v-divider />
                  </v-card>
                </v-dialog>
              </template>
              <!-- <div class="box">
                <v-row>
                  <v-col class="d-flex justify-center ">
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      1
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      2
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      3
                    </v-btn>
                  </v-col>
                </v-row>

                <v-row>
                  <v-col class="d-flex justify-center ">
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      4
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      5
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      6
                    </v-btn>
                  </v-col>
                </v-row>

                <v-row>
                  <v-col class="d-flex justify-center ">
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      7
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      8
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      9
                    </v-btn>
                  </v-col>
                </v-row>

                <v-row>
                  <v-col class="d-flex justify-center ">
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="#ffd000"
                    >
                      <center><i class="far fa-trash-alt" style="color:#ffffff;" /></center>
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="primary"
                    >
                      0
                    </v-btn>
                    <v-btn
                      class="mx-2"
                      fab
                      dark
                      color="#ffd000"
                    >
                      <center><i class="fas fa-times" style="color:#ffffff;" /></center>
                    </v-btn>
                  </v-col>
                </v-row>
              </div> -->
            </v-menu>

            <v-btn class="btn1" @click="onSave">
              <span class="txt1">LOG IN</span>
            </v-btn>
            <center><i class="fas fa-university" style="color:#ffd000;" /></center>
            <p>Forgot password?</p>
            <p>New to Bank Apps? Sign Up</p>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  data: () => ({
    user: '',
    passwd: '',
    dialog: false,
    failed: false,
    fname: ''
  }),
  methods: {
    async  onSave () {
      console.log('onSave')
      const res = await fetch('http://localhost:7001/list?user=' +
      this.user + '&pass= ' + this.pass)
      const data = await res.json()
      console.log('data = ', data)
      console.log('data = ', data.data)
      console.log('status = ', data.status)
      this.fname = data.data.firstname
      if (data.status === 1) {
        console.log('Login ok')
        this.dialog = true
        setInterval(() => {
          this.dialog = false
        }, 3000)
        this.$router.push('/home')
      } else {
        console.log('Error Login')
        this.failed = true
        setInterval(() => {
          this.failed = false
        }, 3000)
        this.$router.push('/index.vue')
      }
    }

  }
}
</script>

<style>
.pa-7 {
  margin-top: 100px;
}
h3 {
  margin-bottom: 50px;
}
.txt1 {
  color: brown;
}
.btn1 {
  background: linear-gradient(to bottom,#FFEB3B,#FFC107);
  margin-bottom: 60px;
}
.box {
  background-color: white;
  padding: 5px;
  border-radius: 25px;
  font-size: 18px;
}
</style>
