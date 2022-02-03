<template>
  <div>
      <li>
          <p>{{info.title}}</p>
      </li>
  </div>
</template>

<script>
export default {
    name:"Film",
    props: {
        info: Object
    }
}
</script>

<style>

</style>