<template>
	<div class="home">
		<header>
    <div class="head">
      <div class="logo">
        <a href="#">
          <img :src="require('@/assets/img/logo.png')" alt="logo" />
          <div class="name">next media</div>
        </a>
      </div>
      <a href="#">
        <img class="menu" :src="require('@/assets/img/menu.png')" alt="menu" />
      </a>
    </div>
    <nav>
      <ul>
        <li><a href=""><img :src="require('@/assets/img/home.png')" alt="home page" /></a></li>
        <li v-for="menu in menus" :key="menu.object_id"><a href="#">{{ menu.label }}</a></li>
      </ul>
    </nav>
    </header>
    <aside>
      <article v-for="post in posts" :key="post.id">
        <div class="poster">
          <img :src="post.thumbnail_images.large.url" :alt="post.categories[0].title" />
          <div class="category" >{{ post.categories[0].title }}</div>
        </div>
        <div class="infos">
          <div class="title">
            {{ post.title }}
          </div>
          <div class="at">
            {{ getArabeDate(post.date) }}
          </div>
        </div>
      </article>
      <div class="more" v-if="isMore">
        <img :src="require('@/assets/img/more.png')" al="more post"  @click="loadMore()" />
      </div>
    </aside>
    <footer>
    </footer>
	</div>	
</template>

<script>
import axios from 'axios'

export default {
  name: 'home',
  props: {
    menus: Array,
    posts: Array,
    isMore: Boolean
  },
  methods: {
    getArabeDate: function(date) {
      date = new Date(date);
      var months = ["يناير", "فبراير", "مارس", "إبريل", "مايو", "يونيو",
        "يوليو", "أغسطس", "سبتمبر", "أكتوبر", "نوفمبر", "ديسمبر"
      ];
      var days = ["اﻷحد", "اﻷثنين", "الثلاثاء", "اﻷربعاء", "الخميس", "الجمعة", "السبت"];
      var arDateString = days[date.getDay()] + ' ' + date.getDate() + ' ' + months[date.getMonth()] + ' ' + date.getFullYear();
      return arDateString;
    },
    loadMore: function() {
      axios.get('http://femme.nextmedia.ma/api/get_recent_posts/?page=2')
        .then(response => {
          this.posts = this.posts.concat(response.data.posts)
      })
      this.isMore = false
    }
  },
  mounted() {
    this.isMore = true
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
.home {
  header {
    width: 100%;
    background-image: linear-gradient(to right, #8220a4, #8b21a4, #9423a4, #9c25a4, #a428a4);
    .head {
      height: 70px;
      border-bottom: .1px solid white;
      .logo {
        width: 150px;
        margin: auto;
        img {
          height: 50px;
          padding-top: 10px;
        }
        .name {
          display: inline-block;
          width: 83px;
          font-family: sans-serif;
          font-size: 26px;
          font-weight: bold;
          color: white;
          line-height: 24px;
          position: relative;
          top: -7px;
          left: 12px;
        }
      }
      img.menu {
        float: right;
        position: relative;
        top: -45px;
        height: 20px;
        right: 20px;
      }
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
              background-color: #690a5f;
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
        position: relative;
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
          font-size: 20px;
          font-weight: bold;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
          direction: rtl;
        }
        .at {
          font-size: 16px;
          position: absolute;
          bottom: 0;
          right: 0;
          color: gray;
        }
      }
    }
    .more {
      text-align: center;
      padding: 20px 0;
      img {
        cursor: pointer;
      }
    }
  }
  footer {
    width: 100%;
    height: 100px;
    background-image: linear-gradient(to left, #8220a4, #8b21a4, #9423a4, #9c25a4, #a428a4);
    margin-top: 5px;
  }
}
</style>