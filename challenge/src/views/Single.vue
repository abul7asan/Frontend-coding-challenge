<template>
	<div class="single">
		<header>
			<div class="head">
			</div>
			<div class="nav">
				<div class="logo">
					<a href="#">
						<img :src="require('@/assets/img/logo-nav.png')" class="next" alt="logo" />
					</a>
				</div>
				<a href="#">
						<img :src="require('@/assets/img/prev.png')" class="prev" alt="logo" />
				</a>
				<a href="#">
						<img :src="require('@/assets/img/menu-nav.png')" class="menu" alt="logo" />
				</a>
			</div>
		</header>
		<aside>
			<Post :post="post" />
			<div class="share">
				<div class="fb">شارك <span>(0)</span></div>
				<div class="tw">غرد <span>(0)</span></div>
			</div>
			<article class="content" v-html="post.content">
			</article>
			<div class="share">
				<div class="fb">شارك <span>(0)</span></div>
				<div class="tw">غرد <span>(0)</span></div>
			</div>
		</aside>
		<footer>
		</footer>
	</div>
</template>
<script>
import axios from 'axios'
import Post from '@/components/Post.vue'

export default {
	name: 'single',
	components: {
		Post
	},
	data() {
		return {
			post: {}
		}
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
    }
  },
	mounted() {
    axios.get('http://femme.nextmedia.ma/api/get_post/?id=178')
      .then(response => {
        this.post = response.data.post
    })
	}
}
</script>
<style lang="scss">
.single {
	header {
		.head {
			width: 100%;
			height: 40px;
			background-image: linear-gradient(to right, #8220a4, #8b21a4, #9423a4, #9c25a4, #a428a4);
		}
		.nav {
			width: 100%;
			height: 80px;
			border-bottom: .2px solid #dadada;
			.logo {
				width: 80px;
				margin: auto;
				img.next {
					height: 80px;
				}
			}
			.prev {
				height: 35px;
				position: relative;
				top: -65px;
				left: 5px;
			}
			.menu {
				float: right;
				position: relative;
				top: -50px;
				left: -5px;
			}
		}
	}
	aside {
		width: 100%;
		article {
			width: 95%;
			margin: 5px auto;
			.poster {
				margin-top: 10px;
        position: relative;
        width: 100%;
        height: 300px;
        figure {
					width: 100%;
					height: 100%;
					margin: 0;
					overflow: hidden;
          img {
            height: 100%;
            width: 100%;
            border-radius: 5px;
            -webkit-transform: scale(1);
						transform: scale(1);
						-webkit-transition: .3s ease-in-out;
						transition: .3s ease-in-out;
          }
					:hover {
						transform: scale(1.3);
          }
        }
        .category  {
          text-align: right;
          padding: 2px 15px;
          background-color: #db0303;
          color: white;
          position: absolute;
          bottom: -10px;
          right: 0;
          border-radius: 5px;
          font-size: bold;
        }
      }
      .infos {
        width: 100%;
        height: 100px;
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
		.share {
			width: 95%;
			margin: 5px auto;
			.fb,.tw {
				width: 42%;
				display: inline-block;
				text-align: right;
				border-radius: 5px;
				padding-right: 20px;
				color: white;
				font-size: 16px;
				font-weight: bold;
				cursor: pointer;
				span {
					font-size: 14px;
					font-weight: 100;
				}
			}
			.fb {
				background-color: #3b5998;
				&:before {
					content: '';
					background : url('~@/assets/img/facebook.png') no-repeat;
					width: 30px;
					height: 24px;
					position: relative;
					float: left;
					margin-left: 10px;
					margin-top: 3px;
				}
				&:hover {
					box-shadow: 2px 3px #183a82
				}
			}
			.tw {
				float: right;
				background-color: #1da1f2;
				&:before {
					content: '';
					background : url('~@/assets/img/twitter.png') no-repeat;
					width: 30px;
					height: 24px;
					position: relative;
					float: left;
					margin-left: 10px;
					margin-top: 3px;
				}
				&:hover {
					box-shadow: 2px 3px #1272ad;
				}
			}
		}
		.content {
			display: flex;
			margin-top: 30px;
			margin-bottom: 20px;
			p {
				margin:auto;
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