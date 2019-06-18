<template lang="html">
  <div
    class="company-selector"
    :style="{ backgroundImage: `url( ${ require('@/assets/' + companyLogoUrl ) } )` }"
  >
      {{ title }}
  </div>
</template>

<script>
export default {
  name: 'CompanySelector',
  props: ['title', 'companyLogoUrl'],
}
</script>

<style lang="scss" scoped>

  .company-selector{
    width: 250px;
    height:250px;
    background-color: #dadada;
    background-size: contain;
    font-size: 20px;
  }

</style>
