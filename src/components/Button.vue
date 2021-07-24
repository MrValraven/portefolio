<template>
  <a :href="link" class="button" rel="noreferrer nooppener" target="_blank">{{buttonText}}</a>
</template>

<script>
export default {
    name: 'Button',
    props: {
        buttonText: String,
        link: String,
    }
}
</script>

<style scoped lang="scss">


$whiteBlue: #E7ECEF;
$darkBlue: #274C77;
$normalBlue: #6aa7cf;
$lightBlue: #A3CEF1;
$easing: cubic-bezier(0.39, 1.61, 0.89, 1.22);
$fastEasing: cubic-bezier(0.075, 0.82, 0.165, 1);

.button {
    display: inline-block;
    color: $whiteBlue;
    background-color: $darkBlue;
    border: 1px solid $normalBlue;
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
    transition: all 0.5s $fastEasing ;

    &:hover {
        transform: translateY(-5px) !important;
    }
}

.lastButton {
    margin-left: 30px;
    color: $darkBlue;
    background-color: $whiteBlue;
    border: 1px solid $darkBlue;
}

</style>