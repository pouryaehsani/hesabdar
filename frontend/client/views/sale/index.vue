<template>
  <transition>
    <b-tabs type="is-boxed" v-model="activeTab">
        <b-tab-item>
            <template slot="header">
                <span> لیست </span>
                <b-icon icon="list" />
            </template>
            <template>
              <sales-list ref="salesList"></sales-list>
            </template>
        </b-tab-item>
        <b-tab-item>
            <template slot="header">
                <span> جدید </span>
                <b-icon icon="plus" />
            </template>
            <template>
              <new-deal @onSuccess="newDealAdded"></new-deal>
            </template>
        </b-tab-item>
    </b-tabs>
  </transition>
</template>

<script>
  import { CardModal, Modal } from 'vue-bulma-modal'
  import List from './../../templates/List'
  import NewDeal from './New'
  import SalesList from './List'
  import DealItemList from './../deal/dealItem/List'
  import DealPayment from './../deal/payment/index'
  import DealerSelect from './../dealer/Select'
  
  export default {
    components: {
      List,
      CardModal,
      NewDeal,
      SalesList,
      Modal,
      DealItemList,
      DealPayment,
      DealerSelect
    },
    data () {
      return {
        newModalVisible: false,
        deleteModalVisible: false,
        editModalVisible: false,
        isPublic: true,
        editId: null,
        activeTab: 0
      }
    },
    methods: {
      newDealAdded (deal) {
        this.$refs['salesList'].loadAsyncData(this.$refs['salesList'].table)
        this.activeTab = 0
      }
    }
  }
</script>
