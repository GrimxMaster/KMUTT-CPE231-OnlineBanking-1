<template>
  <v-app>
    <drawer v-model="drawerPannel" :items="items" :minivariant="miniVariant">
      <staff-info />
      <v-divider class="mt-1" />
    </drawer>
    <toolbar
      :dark="true"
      :color="$vuetify.theme.primary"
      :drawer.sync="drawerPannel"
      title="MANAGER - Yee Netbank"
      @toggle="setDrawer"
    ></toolbar>
    <v-content>
      <nuxt />
    </v-content>
  </v-app>
</template>

<script>
import Drawer from '@/components/Drawer.vue'
import Toolbar from '@/components/Toolbar'
import theme from './themes/manager'
import StaffInfo from '@/components/StaffInfo'

export default {
  components: {
    Drawer,
    Toolbar,
    StaffInfo
  },
  data() {
    return {
      clipped: false,
      drawerPannel: null,
      fixed: false,
      items: [
        {
          icon: 'mdi-view-dashboard',
          title: 'Overview',
          to: '/manager/overview'
        },
        {
          icon: 'account_balance_wallet',
          title: 'Customer'
        },
        {
          icon: 'mdi-clipboard-account',
          title: 'Staff'
        },
        {
          icon: 'mdi-domain',
          title: 'Balance',
          to: '/manager/balance'
        },
        {
          icon: 'mdi-bank',
          title: 'Transactions'
        },
        {
          icon: 'account_balance_wallet',
          title: 'Account',
          to: '/manager/account'
        },
        {
          icon: 'mdi-credit-card',
          title: 'Card',
          to: '/manager/card'
        },
        {
          icon: 'mdi-checkbook',
          title: 'Cheque',
          to: '/manager/cheque'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  },
  created() {
    this.$vuetify.theme = theme
  },
  methods: {
    setDrawer(value) {
      this.drawerPannel = value
    }
  }
}
</script>
