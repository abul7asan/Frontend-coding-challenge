<template>
	<div class="single">
		<header>
			<div class="head">
			</div>
			<div class="nav">
			</div>
		</header>
		<aside>
			<article>
				<div class="poster">
					<img src="http://femme.nextmedia.ma/content/uploads/2018/07/3a6a533b66.jpg" />
					<div class="category" >ok</div>
				</div>
				<div class="infos">
          <div class="title">
            jjjjjjjjjjjjjjjjjjjjjjjjjjj
          </div>
          <div class="at">
            ooooooooo
          </div>
        </div>
			</article>
			<div class="share">
				<div class="fb">SHARE</div>
				<div class="tw">SHARE</div>
			</div>
			<article class="content">
			</article>
			<div class="share">
				<div class="fb">SHARE</div>
				<div class="tw">SHARE</div>
			</div>
		</aside>
		<footer>
		</footer>
	</div>
</template>
<script>
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
			border-bottom: .2px solid gray;
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
				width: 49%;
				display: inline-block;
				text-align: center;
				border: .5px solid black;
				border-radius: 5px;
			}
			.fb {
				background-color: #3b5998;
			}
			.tw {
				float: right;
				background-color: #1da1f2;
			}
		}
		.content {
			height: 100vh;
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