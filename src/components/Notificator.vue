<template>
  <div class="text-xs-center">
    <v-menu
      v-model="menu"
      :close-on-content-click="false"
      :nudge-width="350"
      offset-x
      open-on-hover
      close-delay="100" 
      open-delay="50"
      left
    >
    <v-btn flat icon color="red lighten-2" slot="activator">
        <v-icon>notifications</v-icon>
    </v-btn>

      <div class="notifications-container">
        <div class="notifications-header notification-list-header">
            <h2>notificaiones <span class="notifications-count">3</span></h2>
        </div>
        <v-divider></v-divider>
        <div class="notifications-list">
            <v-list two-line>
          <template v-for="(item, index) in items">
            <v-subheader
              v-if="item.header"
              :key="item.header"
            >
              {{ item.header }}
            </v-subheader>

            <v-divider
              v-else-if="item.divider"
              :inset="item.inset"
              :key="index"
            ></v-divider>

            <v-list-tile
              v-else
              :key="item.title"
              avatar
              @click=""
            >
              <v-list-tile-avatar>
                <img :src="item.avatar">
              </v-list-tile-avatar>

              <v-list-tile-content>
                <v-list-tile-title v-html="item.title"></v-list-tile-title>
                <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
              </v-list-tile-content>
            </v-list-tile>
          </template>
        </v-list>
        </div>
      </div>
    </v-menu>
  </div>
</template>
<script>
export default {
  data: () => ({
    fav: true,
    menu: false,
    message: false,
    hints: true,
    items: [
      { header: "Today" },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
        title: "Brunch this weekend?",
        subtitle:
          "<span class='text--primary'>Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend.?"
      },
      { divider: true, inset: true },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
        title: 'Summer BBQ <span class="grey--text text--lighten-1">4</span>',
        subtitle:
          "<span class='text--primary'>to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this."
      },
      { divider: true, inset: true },
      {
        avatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
        title: "Oui oui",
        subtitle:
          "<span class='text--primary'>Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?"
      }
    ]
  })
};
</script>
<style scoped>
.notifications-container {
  background-color: white;
}
.notification-list-header {
  height: 55px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: azure;
}
.notifications-header {
  font-weight: 300;
  color: #919191;
  font-size: 0.9rem;
  font-family: "Roboto";
}
.notifications-count {
  width: 25px;
  height: 25px;
  background-color: aquamarine;
  color: white;
  display: inline-block;
  border-radius: 50%;
  line-height: 25px;
  margin-left: 10px;
}
</style>
