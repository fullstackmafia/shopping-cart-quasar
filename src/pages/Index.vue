<template>
<q-page padding>
  <div class="row q-mb-lg">
      <q-input v-model="newItem" placeholder="Add an item" class="col" />
      <q-btn 
      color="primary" 
      size="sm" 
      label="Add" 
      @click.native="addItem"
      />
    </div>

    <div class="q-pa-md q-lb-mg" >
    <q-toolbar class="bg-primary text-white shadow-2">
      <q-toolbar-title>Items</q-toolbar-title>
    </q-toolbar>

     <q-list bordered>
       
      <q-item v-for="(item, index) in Items" :key="item.id" class="q-my-sm" clickable v-ripple>
        <q-item-section main>
          <q-item-label color="primary">
            {{ item }}
          </q-item-label>
        </q-item-section>
         <q-item-section side>
          <q-icon name="close" color="red" @click.native="returnItem(index)" />
        </q-item-section>
           </q-item>
    </q-list>
   
  </div>

  <div class="q-pa-md" >
    <q-toolbar class="bg-primary text-white shadow-2">
      <q-toolbar-title>Returned Items</q-toolbar-title>
    </q-toolbar>
   <q-list bordered>
      <q-item v-for="(item) in returnItems" :key="item.id" class="q-my-sm" clickable v-ripple>
        <q-item-section main>
          <q-item-label color="primary" text-color="white" >
            {{ item }}
          </q-item-label>
        </q-item-section>
           </q-item>
    </q-list>
  </div>
</q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      Items: [],
      returnItems: [], 
      newItem: ""
    }
  },
  methods: {
    addItem() {
        this.Items.push(this.newItem)
        this.newItem = ''
    },
     returnItem(index) {
      this.returnItems.push(this.Items[index])
      this.Items.splice(index, 1 )
    },
  }
}
</script>