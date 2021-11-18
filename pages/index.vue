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
      KNN BANK
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
            <v-text-field
              label="PLEATE ENTER YOUR PASSWORD..."
              placeholder="Password"
              filled
              rounded
              dense
            />
            <v-btn class="btn1">
              <span class="txt1">LOG IN</span>
            </v-btn>
            <p>Forgot password?</p>
            <p>New to Bank Apps? Sign Up</p>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </div>
</template>

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
</style>
