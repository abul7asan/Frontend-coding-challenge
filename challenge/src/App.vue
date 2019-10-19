<template>
  <div id="in">
    <header>
    </header>
    <nav>
      <ul>
        <li v-for="menu in menus" :key="menu.id"><a href="#">{{ menu.label }}</a></li>
      </ul>
    </nav>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  name: 'app',
  props: {
    menus: Array
  },
  mounted() {
    axios.get('http://femme.nextmedia.ma/api/menus/get_menu/?menu_id=7')
      .then(response => {
        this.menus = response.data.menu.output
    })
  }
}
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
  header {
    width: 100%;
    height: 70px;
    border-bottom: 1px solid;
  }
  nav {
    height: 50px;
    background-color: gray;
      ul {
        margin: 0;
        list-style-type: none;
        float: right;
        li {
          display: inline-block;
          padding: 10px;
        }
      }
  }
}
@media only screen and (max-width: 780px) {
  #in {
    width: 100%;
  }
}
</style>
