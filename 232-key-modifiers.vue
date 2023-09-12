<template>
  <!-- Add key modifiers made this will fire even if Alt or Shift is also pressed -->
  <!-- Ví dụ: ctrl+shift+click / ctrl+alt+click -->
<button @click.ctrl="onClick1">On click 1</button>

<!-- Add key modifiers made this will only fire when Shift and no other keys are pressed -->
<button @click.shift.exact="onCtrlClick">On Ctrl Click</button>

<!-- Add key modifiers made this will only fire when no system modifiers are pressed -->
<button @click.exact="onClick2">On Click 2</button>
</template>

<script setup>
  function onClick1(){
    console.log('onClick1')
  }
  function onCtrlClick(){
    console.log('onCtrlClick')
  }
  function onClick2(){
    console.log('onClick2')
  }
</script>

// Read more
// https://play.vuejs.org/#eNqtVM1O20AQfpWpLzgicQrcUKBQxIGqLVWpeql7MPY4WdjsWrvjJCjK4/TYJ+ixT9I36exunB+gCRUgoXhn5pv5vtmdmUanVZWMaowOox7hsJIZ4XFqUgXQe9XpwGlRwC3ewVAXohRoLAyzAoEGwsJYSAmlMAg4QgWihFNJoA1cDURJwBGZtBoqg9ZiAZ3OauKvv39C8efXj0PIychd6yC7uRT5LXSDKZONYY7sXddEWsGJtyYu6CiNtDpzx700Or5UEAB7vW6I9TiPfZIYreRdUDQesKKgI1MFKA2aBmgcnGVxwD1V97h5OQlOspwCRebqaQaW7gj+/DJEmZ69s3x/K4jtJFfoufP+nJvv4P4asV537W14k82NqAgsUl3NL7asVU6CCzR3EremwQOQa2W1xETqfrzT+HdawT17iG8atiFFE7Ihi9e1hcX+Gr7XDcKOo3YkVIGThNBSQpYnRAwrbQim3OVaEcygNHoIaXTCA8QdstSpSUibRqlahBbo8l1jGwS1AScV5vw7Ekv0SDioAy1gPJSNN+nOJzQENOniNFp7IGnUhrgFR8cwdVIEcYAd6FoWMNaGn10bMnun8pUYAInET0Qoeq/7cMTFXI17bWL7SCSlioMHIGbjIVhiXH81mftbScZRbxLSVz4ubvG3EcO41cTO5l+uEsHYZFXF03UUOhuz5DV/eIqW/fPIpOS7OZWSVQZfGjEgQLJxJhaQb6+/u8r9Ppp4xz97vm0fFq4ibii3mOyHjPLBhZJC4ZXKKu4fxTuuKw1mS+qEV9b/p18usKeW8dvluYUeK7X3/GZtU/OgxDPULJfqvwTtv5gg3o4B616u++f9QJafZyn6yY3ViveDn4Q0yvWwEhLNZeXWEI/mYTMjaZRJqcfvvI1Mje3Gng8wv33EfmMnzpZGn3iVoxnxGlj4KDN95MXh3OdXH3HC3wsnb4ZacvQG52fkIeeN5abHhb2tVcG0V+I82wu/k3iKv9jzCaGyjShH1HfEx/Miq/Fsg/Ql3YPkIOxbNYtmfwF7OuMP
// https://vuejs.org/guide/essentials/event-handling.html#key-modifiers
