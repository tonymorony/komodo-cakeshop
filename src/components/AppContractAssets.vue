<template>
<div>
  <AppDiceTable v-on:new-table="newTable" />
  <v-tabs
    dark
    color="cyan"
    show-arrows
  >
    <v-tabs-slider color="yellow"></v-tabs-slider>

    <v-tab
      v-for="i in contracts"
      :href="'#tab-' + i.name"
      :key="i.name"
    >
      CC {{ i.name }} 
    </v-tab>

    <v-tabs-items>
      <v-tab-item
        v-for="i in contracts"
        :id="'tab-' + i.name"
        :key="i.name"
      >

        <v-card flat>
          <v-card-text>{{ i.description}}</v-card-text>

  <v-data-table
    :headers="headers"
    :items="desserts"
    :loading="true"
    class="elevation-1"
  >
    <v-progress-linear slot="progress" color="blue" indeterminate></v-progress-linear>
    <template slot="headerCell" slot-scope="props">
      <v-tooltip bottom>
        <span slot="activator">
          {{ props.header.text }}
        </span>
        <span>
          {{ props.header.text }}
        </span>
      </v-tooltip>
    </template>
    <template slot="items" slot-scope="props">
      <td class="text-xs-right">{{ props.item.name }}</td>
      <td class="text-xs-right">{{ props.item.minbet }}</td>
      <td class="text-xs-right">{{ props.item.maxbet }}</td>
      <td class="text-xs-right">{{ props.item.maxodds }}</td>
      <td class="text-xs-right">{{ props.item.timeout}}</td>
      <td class="text-xs-right">{{ props.item.funds}}</td>
      <td class="text-xs-right">{{ props.item.txid}}</td>
    </template>
  </v-data-table>


        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </v-tabs>
</div>
</template>
<script>
import AppDiceTable from './AppDiceTable.vue'
  export default {
    components: {
	AppDiceTable
    },
    data () {
      return {
        contracts: [
          { 
            name: 'Faucet',
            description: 'Faucet contract is ...'
          },
          { 
            name: 'Dice',
            description: 'Dice contract is ... '
          },
          { 
            name: 'Rewards',
            description: 'Rewards contract is ...'
          },
          {
            name: 'Assets',
            description: 'Assets contract is ...'
          }
        ],
        getinfo: "yo",


        headers: [
          { text: 'Table', sortable: false, align: 'left', value: 'name' },
          { text: 'min bet', value: 'minbet' },
          { text: 'max bet', value: 'maxbet' },
          { text: 'max odds', value: 'maxodds' },
          { text: 'timeout', value: 'timeout' },
          { text: 'funds', value: 'funds' },
          { text: 'txid', value: 'txid' }
        ],
        desserts: [
          {
            name: 'Frozen Yogurt',
            name: 159,
            minbet: 6.0,
            maxbet: 24,
            maxodds: 24,
            timeout: 4.0,
            funds: 4.0,
            txid: '1%'
          },
          {
            name: 'Ice cream sandwich',
            name: 237,
            minbet: 9.0,
            maxbet: 37,
            maxbet: 24,
            maxodds: 4.0,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Eclair',
            name: 262,
            maxbet: 24,
            maxodds: 4.0,
            minbet: 16.0,
            maxbet: 23,
            maxodds: 6.0,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Cupcake',
            name: 305,
            minbet: 3.7,
            maxbet: 67,
            maxodds: 4.3,
            maxbet: 24,
            maxodds: 4.0,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Gingerbread',
            name: 356,
            maxbet: 24,
            maxodds: 4.0,
            minbet: 16.0,
            maxbet: 49,
            maxodds: 3.9,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Jelly bean',
            name: 375,
            minbet: 0.0,
            maxbet: 24,
            maxodds: 4.0,
            maxbet: 94,
            maxodds: 0.0,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Lollipop',
            name: 392,
            minbet: 0.2,
            maxbet: 24,
            maxodds: 4.0,
            maxbet: 98,
            maxodds: 0,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Honeycomb',
            name: 408,
            minbet: 3.2,
            maxbet: 24,
            maxodds: 4.0,
            maxbet: 87,
            maxodds: 6.5,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            name: 'Donut',
            name: 452,
            minbet: 25.0,
            maxbet: 51,
            maxbet: 24,
            maxodds: 4.0,
            maxodds: 4.9,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          },
          {
            namename: 'KitKat',
            name: 518,
            minbet: 26.0,
            maxbet: 24,
            maxodds: 4.0,
            maxbet: 65,
            maxodds: 7,
            timeout: 4.3,
            funds: 4.3,
            txid: '1%'
          }
        ]




      }
    },
    created() {
      this.getinfo = "hi"
    },
    methods: {
      newTable: function(newTable) {
	console.log("New table received")
	console.log(newTable)
	this.desserts.push(newTable)
      }
    }
  }
</script>
