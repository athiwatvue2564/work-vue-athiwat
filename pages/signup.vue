<template>
  <div>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6" />
    </v-row>
    <div class="box">
      <p style="color : rgb(70, 70, 226);font-size:15px">
        Sign up your bank account
      </p>

      <v-form>
        <v-container>
          <v-row>
            <v-col
              cols="12"
              sm="6"
              md="3"
            >
              <v-text-field
                label="Outlined"
                placeholder="Placeholde1111"
                outlined
              />
            </v-col>
          </v-row>
        </v-container>
      </v-form>
    </div>
  </div>
</template>

<style>
.box {
  background-color: white;
  padding: 5px;
  border-radius: 25px;
  font-size: 18px;
}

.v-text-field--outlined fieldset {
  color: #222020 !important;
}
</style>
