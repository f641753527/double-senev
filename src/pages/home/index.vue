<template>
    <div>
        <Header/>
        <div class="body">
            <van-notice-bar :text="notice" left-icon="volume-o" mode="link" color="#1989fa" background="#ecf9ff"/>
            <div>
                <div class="box">
                    <vue-big-wheel ref="luckyWheel" :prizeList = 'listData' :colors = 'colors' fontColor = 'red' goClassName = 'btn' :strMaxLength = '14'
                        :strLineLength = '6' strKey='name' @go-click = "go" @on-over = "onOver" :transitionDuration = "3"
                    />
                </div>
            </div>
            <audio style="display: none;" autoplay="autoplay" controls="controls" loop="loop" preload="auto" src="/static/Psycho.mp3"/>
        </div>
    </div>
</template>

<script>
import Vue from 'vue'
import vueBigWheel from 'vue-big-wheel'
import { NoticeBar } from 'vant'
import Header from '@/components/Header'
import { PIGS } from '@/utils/resource'

Vue.use(NoticeBar)

export default {
  components: { Header, vueBigWheel },
  data () {
    return {
      listData: [
        { name: 'GUCCI', val: 1 },
        { name: '男朋友一枚', val: 2 },
        { name: '谢谢参与', val: 0 },
        { name: '亲亲', val: 3 },
        { name: '谢谢参与', val: 0 },
        { name: '爱玛士', val: 8 },
        { name: '抱抱', val: 4 },
        { name: '谢谢参与', val: 0 },
        { name: '520红包', val: 0 },
        { name: '为爱鼓掌', val: 0 },
        { name: '陪伴卡', val: 0 }
      ],
      colors: ['#F47F45', '#FFA468'],
      targetIndex: 0,
      notice: ''
    }
  },
  methods: {
    onOver () {
      const res = confirm(`请联系小范童鞋领取~${this.listData[this.targetIndex].name}`)
      if (res) {
        alert('mua')
      } else {
        alert('对奖品不满意? 请重新开启您的幸运之手')
      }
    },
    go (event) {
      setTimeout(() => {
        const util = [1, 3, 6, 9, 10]
        this.targetIndex = util[Math.floor(Math.random() * util.length)]
        this.$refs.luckyWheel.rotateFunc(this.targetIndex)
      }, 200)
    }
  },
  created () {
    const key = this.$route.query.pig || 'b'
    this.notice = `亲爱的 ${PIGS[key]}, 恭喜您被小范童鞋评选为幸运用户, 请抽奖领取您的之奖`
  }
}
</script>

<style lang='scss'>
.body{
    box-sizing: border-box;
    min-height: calc(100vh - 1.2rem);
    background: url('../../../static/bg.jpg') no-repeat center center;
    background-size: cover;
    .box{
        margin: 0 auto;
        margin-top: 3.2rem;
        box-sizing: border-box;
        width: 5rem;
        height: 5rem;
        background-repeat: no-repeat;
        background-size: 100%;
        background-position: center;
        overflow: hidden;
        .btn { // 使用自定义类 不能用scope
            width: 1.2rem !important;
            top: 50% !important;
            transform: translate(-50%, -50%) !important;
        }
    }
}
</style>
