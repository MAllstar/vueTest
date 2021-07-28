<template>
  <div class="pageHeader">
    <ul class="pageNav">
      <li class="navItem" 
        v-for="item in navItems" 
        :key="item.name"
        @mouseover="showPop(item.name)"
        @mouseleave="hidePop()"
      > 
        {{ item.name }}
        <div class="navPopup" @mouseover="showPop(item.name)">
          <ul 
            v-if="hoverName===item.name"  
          >
            <li class="popup" v-for="ll in item.list" :key="ll.name">
              <a :href="ll.url">{{ ll.name }}</a>
            </li> 
          </ul>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Header',
    props: {
    },
    data: () => {
      return {
        hoverName: null,
        navItems: [
          {name: '现货&杠杆', list: [
            {name: 'REST', url: '#'},
            {name: 'WebSocket(New)', url: '#'},
            {name: 'WebSocket(Old)', url: '#'},
            {name: 'APIv2 REST', url: '#'},
            {name: 'APIv2 WebSocket', url: '#'}
          ]},
          {name: '永续合约'},
          {name: '交割合约'}
        ]
      }
    },
    methods: {
      showPop(name) {
        console.log(name)
        this.hoverName = name
      },
      hidePop() {
        this.hoverName = null
      }
    }
  }
</script>