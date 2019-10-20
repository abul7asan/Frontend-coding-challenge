<template>
	<div class="home">
		<Navbar :items="menus" />
    <aside>
      <Post v-for="post in posts" :post="post" :key="post.id" />
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
import Navbar from '@/components/Navbar.vue'
import Post from '@/components/Post.vue'

export default {
  name: 'home',
  data() {
		return {
			menus: [],
			posts: [],
			isMore: false
		}
  },
	components: {
		Navbar,
		Post
  },
  methods: {
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
        figure {
					width: 100%;
					height: 100%;
					margin: 0;
					overflow: hidden;
					cursor: pointer;
					img{
            height: 100%;
            width: 100%;
            border-radius: 5px;
            -webkit-transform: scale(1);
						transform: scale(1);
						-webkit-transition: .3s ease-in-out;
						transition: .3s ease-in-out
          }
          :hover {
						transform: scale(1.3);
					}
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