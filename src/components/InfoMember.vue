<style>
.c-member-content {
  display: flex;
  width: 100%;
  word-break: break-all;
}
.c-member-avatar {
  display: flex;
  align-items: center;
  flex: 0 1;
  max-width: 40vw;
}
.c-member-avatar img {
  max-height: 18rem;
}
.c-member-info {
  flex: 1;
}
.c-member-info-in {
  margin: 1rem;
  padding: 1.5rem 1.5rem 1.5rem 2.5rem;
  border-left: 1px solid #cccccc;
}
.c-member-photo img {
  max-width: 24%;
}
@media screen and (max-width: 760px) {
  .c-member-photo img {
    max-width: 48%;
  }
}
</style>

<template>
  <div v-if="item!=false">
    <div class="c-member-content">
      <div class="c-member-avatar">
        <img :src="GLOBAL.getPicPath(item.avatar) ">
      </div>
      <div class="c-member-info">
        <div class="c-member-info-in">
          <p>{{ item.realName }} {{ item.pinyin }} ({{item.abbr}})</p>
          <p>
            【所属】 {{ item.groupName }} / {{item.teamName}}
            <!-- <span
        v-if="item.team!=item.first_team"
            >(原 {{GLOBAL.teamId2name(item.first_team)}} )</span>-->
          </p>
          <p>【期数】 {{item.periodName}} 【加入时间】 {{ item.joinTime }}</p>
          <p>【昵称】 {{item.nickname}} 【籍贯】 {{ item.birthplace }}</p>
          <p>【生日】 {{item.birthday}} 【星座】 {{item.constellation}}</p>
          <p>
            【身高】 {{item.height}} 【微博】
            <a
              target="_blank"
              :href="'https://weibo.com/u/'+item.wbUid"
            >@{{item.wbName}}</a>
          </p>
          <p>【特长】 {{item.specialty}} 【爱好】 {{item.hobbies}}</p>
        </div>
      </div>
    </div>
    <div class="c-member-photo">
      <img v-if="item.fullPhoto1" :src="GLOBAL.getPicPath(item.fullPhoto1)">
      <img v-if="item.fullPhoto2" :src="GLOBAL.getPicPath(item.fullPhoto2)">
      <img v-if="item.fullPhoto3" :src="GLOBAL.getPicPath(item.fullPhoto3)">
      <img v-if="item.fullPhoto4" :src="GLOBAL.getPicPath(item.fullPhoto4)">
    </div>
  </div>
</template>
<script>
export default {
  name: "InfoMember",
  computed: {
    item: function() {
      var f;
      for (var i in this.GLOBAL.info.starInfo) {
        if (this.GLOBAL.info.starInfo[i].userId == this.memberId) {
          return this.GLOBAL.info.starInfo[i];
          break;
        }
      }
      return false;
    }
  },
  props: ["memberId"]
};
</script>