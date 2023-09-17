<script setup lang='ts'>

import { ref, h } from "vue"

interface ListProps {
  activeIndex: number,
  list: {
    name: string
  }[],
}

/**
 * Implement a functional component :
 * 1. Render the list elements (ul/li) with the list data
 * 2. Change the list item text color to red when clicked.
*/
const ListComponent = (props: ListProps, { emit }) => {
  const listItemGenerator = (item, index) => {
    return h('li', {
      onClick: () => {
        emit('toggle', index)
      },
      style: index === props['active-index'] ? { color: 'red' } : undefined
    }, 
      item.name
    )
  }

  return h('ul', {}, props.list.map(listItemGenerator)) 
}

const list = [{
  name: "John",
}, {
  name: "Doe",
}, {
  name: "Smith",
}]

const activeIndex = ref(0)

function toggle(index: number) {
  activeIndex.value = index
}

</script>

<template>
  <list-component
    :list="list"
    :active-index="activeIndex"
    @toggle="toggle"
  />
</template>

// Read more
// https://play.vuejs.org/#eNqVVV1v00gU/StXfolTBYeWN2/CAl20KlrtIlie6j64zk1sOp6xPOOkqMp/59wZO3ZpQaISor3f98w51w/R26ZJ9h1HabSyRVs1jiy7riGV69165uzsdaYzXdWNaR09UMvbBZV0pG1rasoipGaRj9CO221eMP1TWfexNY2lh0wT5YWr9nylN3yfku7qW24XYlcIS0MIkc5rTsm6ttI7sRyvbxB0lMLLszNYzuiqbhTXrB3ltO00qhqdKyoMRtNiTn3YeUKfGM1aciX7JsQhz1LcqaWq5nSoXDm6N7nLfepFQpcl1ubRVzmuyfG9Qx9lUNMAgQ0dStZUqKq4402S6bNlpgujES+7X54mWlPcCBDpiMkCGHJdOTrOaf06rB9Spd8V2v3NmtvcoRnSpf+CKgFvjCfM4LpWUxnPVDVDyWAlMvpShkopnkbLj/SMZ87sdoqRESoO7qN/EPmx7pvCQ3g3rddr8vNfz8IjvvD22Q39iS08ICnNgMcMfEipg3Nbad6EYscFDVVli0SeOBh8X/+20006JZsgy7dMBI6kzpv4CS7zOQr79BE4YHXttw1EyqIPptRZJBzq4RkcfxkQ9hn7ZwBUBs/NWHtCXrQA+eOXmD7TAwFBCEE09sAM9J4/IX6yz1XHqODj+ulXyyA4L7AVNmxU7hh/Ea1kpxcnagfYUjGus0j+E8152/Rh4Jv0HELehBHhDL8E+xJ9VstJ02gR+SKJYwDvLA7CSfS16cDmk+bfQPRIxYSdq5SVgqfQDctStwyKuQXxfcPFJHMPJoThTym4P4M3WfbHKAQMpeIsGvU+ASVaTGkOemeRLU2nIE/T3ok7t9908UgK4VUPbd40uBDrsFmMtr0WHjGqD0tA6s1J1PHDiTI/PFIETYcqYW3P3GRfzxNn3vGXQR2xJ9DYTMRxjm4+Wlq9VQqrqCqL5tcvwcXHoRc/Cz3vQ/vmvmySO5zU2w6oCzoiboSGgWDoJQwF/wHzk/SLX6U/s09+yHHYQibydjtupYlcJF/+9+Z71OB3Jnt2MXka+QeaOws0t9Uu+WqNBs09NSSnbirF7X+NMA2sPn2cICulzOGDt7m24/5cIqfk4u4Z+1cL+QlFPrZsud2HkxN8Lm93DLaI+/3nf/FtmThrs+lklV84P7E1CsIzuG8S9g53F2NP4vy0+FxCXvic/m/f3zvWdlhKBvWI+Hj/BRdy/2z1cdxXyav+cB+j43eg5r9y
// https://vuejs.org/guide/extras/render-function.html#functional-components
// https://github.com/webfansplz/vuejs-challenges/issues/673
