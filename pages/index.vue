<template>
  <v-app>
    <v-main>
      <v-container>
        <div class="ma-12">
          <v-row>
            <v-col
              v-for="n in top3plates.data"
              :key="`top_${n}`"
              cols="4"
            >
              <v-card
                elevation="3"
                outlined
              >
                <v-card-title
                  style="word-break: keep-all">
                  {{ n.name }}
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
              v-for="i in plateList.data"
              :key="`plate_${i}`">
              <v-card
                height="22"
                width="auto">
                <v-title
                  style="word-break: keep-all">
                  {{ i.name }}
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
      top3plates: [],
      plateList: []
    }
  },
  async mounted () {
    try {
      this.top3plates = await axios.get('http://localhost:5000/api/plates/popular')
    } catch (e) {
      console.error(e)
    }
    this.plateList = await axios.get('http://localhost:5000/api/plates')
    // console.log(test)
  }

}

</script>
