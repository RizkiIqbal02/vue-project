<template>
    <v-sheet width="300" class="mx-auto" style="background-color: #191919; color: white;">
      <v-form fast-fail @submit.prevent>
        <v-text-field 
          v-model="namaLengkap"
          label="Nama Lengkap"
          :rules="namaLengkapRules"
        ></v-text-field>
  
        <v-text-field
          v-model="nim"
          label="NIM"
          :rules="nimRules"
        ></v-text-field>
        

        <v-text-field
          v-model="ipk"
          label="IPK"
          :rules="ipkRules"
        ></v-text-field>
  
        <v-btn @click="setData" block class="mt-2 mb-10" style="background-color: #323232; color: white;">Submit</v-btn>
      </v-form>
    </v-sheet>

    <v-row justify="space-around">
    <v-col cols="auto">
      <v-dialog
        transition="dialog-bottom-transition"
        width="auto"
      >
        <template v-slot:activator="{ props }">
          <v-btn
            color="primary"
            v-bind="props"
          >Show Data Mahasiswa</v-btn>
        </template>
        <template v-slot:default="{ isActive }">
          <v-card>
            <v-toolbar
              color="primary"
              title="Data Mahasiswa"
            ></v-toolbar>
            <v-card-text>
              <div class="text-h5 pa-12">Nama : {{ mahasiswa.namaLengkap }}</div>
              <div class="text-h5 pa-12">NIM : {{ mahasiswa.nim }}</div>
              <div class="text-h5 pa-12">IPK : {{ mahasiswa.ipk }}</div>
            </v-card-text>
            <v-card-actions class="justify-end">
              <v-btn
                variant="text"
                @click="isActive.value = false"
              >Close</v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>
    </v-col>
  </v-row>

  </template>

<script>
export default {
  data: () => ({
    mahasiswa: {
        namaLengkap: '',
        nim: '',
        ipk: '',
    },
    
    namaLengkap: '',
    namaLengkapRules: [
      value => {
        if (value?.length > 0 && value?.length > 3) return true

        return 'Masukan nama yang valid'
      },
    ],
    
    nim: '123',
    nimRules: [
      value => {
        // if (/[^0-9]/.test(value)) return true
        if (/[^a-zA-Z]/.test(value) && value?.length > 7) return true;


        return 'Masukan format NIM yang valid.'
      },
    ],
    
    ipk: '0',
    ipkRules: [
      value => {
        if (/[^a-zA-Z]/.test(value) && value <= 4 && value >= 0) return true;


        return 'Masukan format NIM yang valid.'
      },
    ],
  }),
  methods: {
    setData()
    {
        this.mahasiswa.namaLengkap = this.namaLengkap,
        this.mahasiswa.nim = this.nim,
        this.mahasiswa.ipk = this.ipk
    }
  }
}
</script>