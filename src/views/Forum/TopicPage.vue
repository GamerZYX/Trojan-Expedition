<template>
  <div class="forum-css">
    <div class="outer-frame">
      <div class="forum-container">
        <div class="content-wrapper">
          <div class="forum-wrapper">
            <div class="topic-container">
              <div class="topic-root">
                <div class="back r-border">
                  <router-link to="/forum">
                    <v-btn
                      variant="text"
                      prepend-icon="mdi-arrow-left">
                      Back
                    </v-btn>
                  </router-link>
                  </div>
                <div class="title-container ">
                  <h5 class="title">
                    Hello CS 201!
                  </h5>
                </div>
                <div class="action-panel">
                  <v-row>
                    <v-btn
                      :color="HeartisDisabled ? '#FE8E86' : '#DCDCDC'"
                      @click="HeartisDisabled = !HeartisDisabled"
                      class="heart"
                      variant="text"
                      icon="mdi-heart"
                    ></v-btn>
                    <v-btn
                      :color="FavisDisabled ? '#FFCB4C' : '#DCDCDC'"
                      @click="FavisDisabled = !FavisDisabled"
                      class="fav"
                      variant="text"
                      icon="mdi-star-plus"
                    ></v-btn>
                    <v-btn
                      :color="LikeisDisabled ? 'blue-lighten-2' : '#DCDCDC'"
                      @click="LikeisDisabled = !LikeisDisabled"
                      class="like"
                      variant="text"
                      icon="mdi-thumb-up"
                    ></v-btn>
                  </v-row>
                </div>
              </div>
              <div class="main">
                <div class="detail-container">
                  <div class="action-col">
                    <div class="action-container action-container-css">
                      <div class="upvote">
                        <v-btn
                          icon="mdi-arrow-up-bold"
                          @click="inc"
                        >
                        </v-btn>
                      </div>
                      <div id="count"
                           class="count">
                        0
                      </div>
                      <div class="upvote">
                        <v-btn
                          icon="mdi-arrow-down-bold"
                          @click="dec"
                        >
                        </v-btn>
                      </div>
                    </div>
                  </div>
                  <div class="post-area">
                    <div class="root">
                      <img class="avatar" :src="image">
                      <div>
                        <div class="user-info">
                          <span class="user-name">
                            Frank He
                          </span>
                        </div>
                        <div class="post-info">
                          created at: 11 27, 2022 11:27
                        </div>
                      </div>
                    </div>
                    <div class="content-area">
                      <p>CS 201 by Marco Papa is my most favorite class at USC ever!</p>
                    </div>
                  </div>
                </div>
                <div class="comment-container">
                  <div class="comment-header">
                    <div class="comment-count">
                      <span>
                        <v-icon icon="mdi-comment-quote"></v-icon>
                      </span>
                    </div>
                    <div class="comment-sort">
                      <v-btn variant="text">

                      </v-btn>
                      <v-btn variant="text">

                      </v-btn>
                      <v-btn variant="text">

                      </v-btn>
                    </div>
                  </div>
                  <div class="comment-container2">
                    <div class="comment">
                      <div class="editor">
                        <v-textarea auto-grow rows="2" counter="50">

                        </v-textarea>
                        <div class="action-area">
                          <div class="blank-space">

                          </div>
                          <v-btn color="blue-grey" class="comment-post-button">
                            Post
                          </v-btn>
                        </div>
                      </div>
                    </div>

                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    HeartisDisabled: false,
    FavisDisabled: false,
    LikeisDisabled: false,
    image: require("@/assets/tommytrojan.png"),
  }),
  methods: {
    inc() {
      const page = document.getElementById('count');
      let num = page.innerHTML;
      num ++;
      page.innerHTML = num;
    },
    dec() {
      const page = document.getElementById('count');
      let num = page.innerHTML;
      num --;
      page.innerHTML = num;
    },
    openReply() {
      const page = document.querySelector("#sub-comment");
      page.dataset.isShow = "true";
    },
    closeReply(){
      const page = document.querySelector("#sub-comment");
      page.dataset.isShow = "false";
    },
  }
}
</script>

<style scoped>
.sub-comment[data-is-show='false'] {
  display: none;
}
.sub-comment {
  border: 1px solid #cfd8dc;
  border-radius: 3px;
  margin-top: 5px;
}
.comment-action {
  display: flex;
  margin-top: 5px;
}
.comment-avatar {
  width: 30px;
  height: 30px;
}
.root2 {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}
.comment-content {
  line-height: 1.57;
  color: #424242;
}
.comment2 .comment-content {
  padding-left: 40px;
  margin-top: 5px;
}
.editor .action-area .blank-space {
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
}
.editor .action-area {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: end;
  -ms-flex-pack: end;
  justify-content: flex-end;
  overflow: hidden;
  border-radius: 0 0 2px 2px;
}
.editor {
  line-height: 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
}
.comment-list {
  margin-top: 12px;
  position: relative;
}
.comment {
  border: 1px solid #cfd8dc;
  border-radius: 3px;
  margin-top: 5px;
}
.comment-container2 {
  padding: 0 20px;
}
.comment-header .comment-sort {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  line-height: 40px;
}
.comment-header .comment-count {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
  margin: 0;
  cursor: default;
  font-weight: 500;
  font-size: 12px;
}
.comment-header{
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  margin-bottom: 20px;
  background: #fafafa;
  border-style: solid;
  border-color: #eeeeee;
  border-width: 1px 0;
  padding: 0 20px;
}
.user-name{
  color: #424242;
  margin-left: 10px;
}
.avatar {
  border-radius: 50%;
  opacity: 0.7;
  width: 30px;
  height: 30px;
  display: inline-block;
  background-color: #f5f5f5;
}
.post-info{
  color: #bdbdbd;
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
  display: -webkit-inline-box;
  display: -ms-inline-flexbox;
  display: inline-flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  margin-left: 25px;
}
.user-info{
  display: -webkit-inline-box;
  display: -ms-inline-flexbox;
  display: inline-flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  line-height: 1;
  font-size: 12px;
}
.root {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}
.content-area {
  margin-top: 10px;
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
  overflow: hidden;
}
.upvote {
  padding: 2px 7px;
  border-radius: 3px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-transition: color 0.3s, background-color 0.3s;
  -o-transition: color 0.3s, background-color 0.3s;
  transition: color 0.3s, background-color 0.3s;
}
.count {
  font-size: 12px;
  font-weight: bold;
  line-height: 40px;
  /*color: #78909c;*/
}
.action-container-css {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}
.action-container {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
}
.post-area {
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
  max-width: 100%;
  min-width: 0;
}
.action-col {
  margin-right: 20px;
}
.comment-container {
  margin: 15px 0;
  min-width: 750px;
}
.detail-container {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  margin-top: 10px;
  padding: 0 20px;
}
.main {
  position: relative;
}

.action-panel {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  margin: 0 20px 0 5px;
}
.title {
  margin: 0px;
  min-width: 0px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: pre;
}
.title-container{
  display: flex;
  -webkit-box-align: center;
  align-items: center;
  flex: 1 1 auto;
  min-width: 0px;
}
.back {
  padding: 13px 16px 13px 16px
}
.r-border {
  margin-right: 16px;
  position: relative;
}
.topic-root {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-shadow: inset 0 -1px 0 0 #eeeeee;
  box-shadow: inset 0 -1px 0 0 #eeeeee;
  overflow: hidden;
  height: 50px;
}
.topic-container {
  background: white;
  -webkit-box-shadow: 0 1px 2px 0 rgb(0 0 0 / 10%);
  box-shadow: 0 1px 2px 0 rgb(0 0 0 / 10%);
  border-radius: 3px;
}
input[type='checkbox'] {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  padding: 0;
}
input:not([type='range']), label, select, summary, textarea {
  -ms-touch-action: manipulation;
  touch-action: manipulation;
}
.forum-css {
  position: relative;
  z-index: 0;
  display: flex;
  height: 100%;
  width: 100%;
  min-width: 992px;
  flex-direction: column;
  overflow: hidden;
  -webkit-font-smoothing: antialiased;
}
.outer-frame {
  position: relative;
  display: flex;
  flex-direction: column;
  flex: 1 1 0%;
  z-index: 0;
  min-height: 0px;
}
.forum-container > div {
  max-width: 1240px;
  margin: 0px auto;
}
.forum-container {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  z-index: 0;
  overflow-y: auto;
  background-color: rgb(245, 245, 245);
}
.content-wrapper {
  width: 100%;
}
.forum-wrapper {
  margin: 10px 0px 40px;
}
.topic-item-wrap .topic-item{
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  height: 80px;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: start;
  -ms-flex-pack: start;
  justify-content: flex-start;
  -webkit-transition: background-color 500ms linear;
  -o-transition: background-color 500ms linear;
  transition: background-color 500ms linear;
}
.search-wrapper1 .search-input {
  width: 100%;
}

.search-wrapper1 .search-box1 input {
  padding-right: 32px;
}
.search-box2 .input {
  padding: 6.3px 10px;
  font-size: 12;
}
.input {
  width: 100%;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  color: #546e7a;
  border: 1px solid #cfd8dc;
  border-radius: 3px;
  font-weight: 300;
  -o-text-overflow: ellipsis;
  text-overflow: ellipsis;
  -webkit-transition: 0.4s all;
  -o-transition: 0.4s all;
  transition: 0.4s all;
}
.input:focus {
  color: #263238;
  border-color: #263238;
  outline: none !important;
  -webkit-box-shadow: 0 0 0 2px rgb(251 192 46 / 40%);
  box-shadow: 0 0 0 2px rgb(251 192 46 / 40%);
}
button, input {
  overflow: visible;
}
input, button, select, optgroup, textarea {
  margin: 0;
  color: inherit;
  font-size: inherit;
  font-family: inherit;
  line-height: inherit;
}
a {
  color: #1890ff;
  text-decoration: none;
  background-color: transparent;
  outline: none;
  cursor: pointer;
  -webkit-transition: color 0.3s;
  -o-transition: color 0.3s;
  transition: color 0.3s;
}
input[type="checkbox" i] {
  background-color: initial;
  cursor: default;
  appearance: auto;
  box-sizing: border-box;
  margin: 3px 3px 3px 4px;
  padding: initial;
  border: initial;
}
input {
  writing-mode: horizontal-tb !important;
  text-rendering: auto;
  color: fieldtext;
  letter-spacing: normal;
  word-spacing: normal;
  line-height: normal;
  text-transform: none;
  text-indent: 0px;
  text-shadow: none;
  display: inline-block;
  text-align: start;
  appearance: auto;
  -webkit-rtl-ordering: logical;
  cursor: text;
  background-color: field;
  margin: 0em;
  padding: 1px 2px;
  border-width: 2px;
  border-style: inset;
  border-color: -internal-light-dark(rgb(118, 118, 118), rgb(133, 133, 133));
  border-image: initial;
}
a {
  background-color: transparent;
}
*, *::before, *::after {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
*, *::before, *::after {
  -webkit-box-sizing: inherit;
  box-sizing: inherit;
}
div {
  display: block;
}
h5 {
  display: block;
  font-size: 0.83em;
  margin-block-start: 1.67em;
  margin-block-end: 1.67em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
}
h1, h2, h3, h4, h5, h6 {
  margin-top: 0;
  margin-bottom: 0.5em;
  color: rgba(0, 0, 0, 0.85);
  font-weight: 500;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
h1 {
  display: block;
  font-size: 2em;
  margin-block-start: 0.67em;
  margin-block-end: 0.67em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
}
p, input, textarea, select, button {
  font-size: 14px;
  font-weight: 400;
}
body {
  margin: 0;
  color: rgba(0, 0, 0, 0.65);
  font-size: 14px;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', 'Helvetica Neue', Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
  font-variant: tabular-nums;
  line-height: 1.5;;
}
</style>