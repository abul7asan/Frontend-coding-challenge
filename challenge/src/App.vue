<template>
  <div id="in">
    <Home />
  </div>
</template>
<script>
import Home from './views/Home.vue'
export default {
  name: 'app',
  components: {
    Home
  }
}
/*import Single from './views/Single.vue'
export default {
  name: 'app',
  components: {
    Single
  }
}*/
</script>
<style lang="scss">
@font-face {
  font-family: 'Droid Arabic Kufi';
  font-style: normal;
  font-weight: 400;
  src: url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Regular.eot);
  src: url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Regular.eot?#iefix) format('embedded-opentype'),
       url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Regular.woff2) format('woff2'),
       url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Regular.woff) format('woff'),
       url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Regular.ttf) format('truetype');
}
@font-face {
  font-family: 'Droid Arabic Kufi';
  font-style: normal;
  font-weight: 700;
  src: url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Bold.eot);
  src: url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Bold.eot?#iefix) format('embedded-opentype'),
       url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Bold.woff2) format('woff2'),
       url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Bold.woff) format('woff'),
       url(//fonts.gstatic.com/ea/droidarabickufi/v6/DroidKufi-Bold.ttf) format('truetype');
}

#in {
  width: 90%;
  margin: 0 auto;
  font-family: 'Droid Arabic Kufi' , serif;
}
@media only screen and (max-width: 780px) {
  #in {
    width: 100%;
  }
}
</style>
