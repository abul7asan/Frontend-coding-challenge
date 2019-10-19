<template>
  <div id="in">
    <header>
    <div class="head">
    </div>
    <nav>
      <ul>
        <li v-for="menu in menus" :key="menu.id"><a href="#">{{ menu.label }}</a></li>
      </ul>
    </nav>
    </header>
    <aside>
      <article v-for="post in posts" :key="post.id">
        <div class="poster">
          <img :src="post.thumbnail_images.large.url" :alt="post.categories[0].title" />
          <div class="category">{{ post.categories[0].title }}</div>
        </div>
        <div class="infos">
          <div class="title">
            {{ post.title }}
          </div>
          <div class="at">
            {{ post.date }}
          </div>
        </div>
      </article>
    </aside>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  name: 'app',
  props: {
    menus: Array,
    posts: Array
  },
  mounted() {
    axios.get('http://femme.nextmedia.ma/api/menus/get_menu/?menu_id=7')
      .then(response => {
        this.menus = response.data.menu.output
    })
    axios.get('http://femme.nextmedia.ma/api/get_recent_posts/')
      .then(response => {
        this.posts = response.data.posts
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
    background-image: linear-gradient(to right, #8220a4, #8b21a4, #9423a4, #9c25a4, #a428a4);
    .head {
      height: 70px;
      border-bottom: .1px solid white;
    }
    nav {
      height: 40px;
        ul {
          margin: 0;
          list-style-type: none;
          li {
            float: right;
            cursor: pointer;
            margin-top: 2px;
            :hover {
              background-color: black;
              border-radius: 5px;
            }
            a {
              text-decoration: none;
              display: inline-block;
              padding: 2px 10px;
              color: white;
              transition: all 1s;
            }
          }
        }
    }
  }
  aside {
    width: 100%;
    article {
      width: 95%;
      height: 300px;
      margin: 5px auto;
      .poster {
        width: 100%;
        height: 70%;
        position: relative;
        img{
          height: 100%;
          width: 100%;
          border-radius: 5px;
        }
        .category  {
          text-align: right;
          padding: 2px 15px;
          background-color: red;
          position: absolute;
          bottom: -10px;
          right: 0;
          border-radius: 5px;
        }
      }
      .infos {
        width: 100%;
        height: 25%;
        margin-top: 10px;
        text-align: right;
        position: relative;
        .title {

        }
        .at {
          position: absolute;
          bottom: 0;
          right: 0;
        }
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
