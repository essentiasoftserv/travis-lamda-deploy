<template>
  <div>
    <p>
      <br>
        <b>{{ msg }}</b>
    </p>
    <img src="../assets/emoji.png" style="height: 90px;width=90px;" />
  </div>
</template>

<script>
export default {
  name: "Ping",
  data() {
    return {
      msg: "Do you mind looking here ?"
    };
  }
};
</script>

<style>
img {
  size: 10em;
}
</style>
