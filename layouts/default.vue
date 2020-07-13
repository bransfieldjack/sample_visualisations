<template>
  <v-app id="inspire">

    <v-navigation-drawer
      :width="100"
      app
    >

      <v-container>
        <v-row v-for="(item, index) in routes">
          <v-col cols="12" :key="item">

            <v-hover v-slot:default="{ hover }">
              <v-card flat :elevation="hover ? 12 : 2" :class="{ 'on-hover': hover }">
                <nuxt-link :to="item.src" style="text-decoration: none;">
                  <v-img :src="item.image" max-width="100"/>
                  <p style="text-align: center; color: #889096; font-size: 13px;">{{item.name}}</p>
                </nuxt-link>
              </v-card>
            </v-hover>

          </v-col>
        </v-row>
      </v-container>

    </v-navigation-drawer>

    <v-main>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col class="text-center">
            
            <Nuxt/>

          </v-col>
        </v-row>
      </v-container>
    </v-main>

  </v-app>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      routes: [
        {name: " ", src: "/sunburst", image: "/pie.png"},
        {name: " ", src: "/scatter", image: "/scatter.png"},
        // {name: "Atlas", src: "/", image: "/atlas_icon.png"},
      ]
    }),
  }
</script>