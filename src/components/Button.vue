<template>
  <button class="button">
    {{ buttonText }}
    <a v-if="link" :href="link" rel="noreferrer nooppener" target="_blank"></a>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    buttonText: String,
    link: String,
  },
};
</script>

<style scoped lang="scss">
$whiteBlue: #e7ecef;
$darkBlue: #274c77;
$normalBlue: #6aa7cf;
$lightBlue: #a3cef1;
$easing: cubic-bezier(0.39, 1.61, 0.89, 1.22);
$fastEasing: cubic-bezier(0.075, 0.82, 0.165, 1);

.button {
  position: relative;
  display: inline-block;
  color: $whiteBlue;
  background-color: $darkBlue;
  border: 1px solid $normalBlue;
  outline: none;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  padding-top: 1rem;
  padding-bottom: 1rem;
  font-size: 1.125rem;
  font-weight: 500;
  line-height: 1.5;
  text-align: center;
  opacity: 1;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.5s $fastEasing;

  &:hover {
    transform: translateY(-5px) !important;
    box-shadow: 0px 2px 10px 0px rgba($color: #000000, $alpha: 0.25);
  }

  a {
    position: absolute;
    width: 155px;
    height: 60px;
    right: 0;
    bottom: 0;
  }
}

.lastButton {
  margin-left: 30px;
  color: $darkBlue;
  background-color: $whiteBlue;
  border: 1px solid $darkBlue;
}

@media (max-width: 450px) {
  .button {
    padding: 15px;
  }
}
@media (max-width: 350px) {
  .button {
    padding: 8px;
  }
}

@media (max-width: 600px) {
  .showMoreButton {
    width: 100% !important;
  }
}
</style>
