<template>
  <v-app>
    <v-main>
      <v-container>
        <div class="ma-12">
          <v-row>
            <v-col
              v-for="n in 1"
              :key="n"
              cols="4"
            >
              <v-card
                elevation="3"
                outlined
              >
                <v-card-title>
                  {{ n }} 위 {{ plates.data[0].name }}
                </v-card-title>
              </v-card>
            </v-col>
          </v-row>
        </div>
        <div class="mt-10 ml-10 mr-10">
          <v-row>
            <button>
              # 한식
            </button>
            <button>
              # 중식
            </button>
            <button>
              # 일식
            </button>
            <button>
              # 양식
            </button>
            <button>
              # 한식
            </button>
            <button>
              # 한식
            </button>
          </v-row>
        </div>
        <div class="pt-6 pl-10 pr-10 pb-10">
          <v-row
            class="">
            <v-col
              v-for="i in 1000"
              :key="i">
              <v-card
                height="22"
                width="auto">
                <v-title
                  style="word-break: keep-all">
                  삼겹살
                </v-title>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import * as axios from 'axios'

export default {
  data () {
    return {
      plates: []
    }
  },
  async mounted () {
    try {
      this.plates = await axios.get('http://localhost:5000/api/plates/popular')
      console.log(this.plates.data[0].name)
    } catch (e) {
      console.error(e)
    }
    // const test = await axios.get('http://localhost:5000/api/plates')
    // console.log(test)
  }

}

</script>
