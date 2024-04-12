<!--  -->
<template>
  <div class="ym">
    <div class="zy iconfont icon-shuangjiantouzuo" @click="subyear(true)"></div>
    <div
      class="zm iconfont icon-jiantou_liebiaoxiangyou_o"
      @click="submonth(true)"
      v-if="state.yyyy == false && state.mmmm == false"
    ></div>
    <div class="date">
      <div class="yyyy" @click="yyyy" v-if="state.yyyy == false">
        <div class="dy">{{ state.year }}</div>
        <div class="dw">年</div>
      </div>
      <div class="yyyy" @click="yyyy" v-if="state.yyyy">
        <div class="dy">{{ state.year - (state.year % 10) }}</div>
        <div class="dw">年</div>
        <div class="dw">-</div>
        <div class="dy">{{ state.year - (state.year % 10) + 9 }}</div>
        <div class="dw">年</div>
      </div>
      <div class="mmmm" @click="mmmm" v-if="state.yyyy == false && state.mmmm == false">
        <div class="dm">{{ state.month }}</div>
        <div class="dw">月</div>
      </div>
    </div>
    <div
      class="ym iconfont icon-jiantou_liebiaoxiangyou_o"
      @click="addmonth(true)"
      v-if="state.yyyy == false && state.mmmm == false"
    ></div>
    <div class="yy iconfont icon-shuangjiantouzuo" @click="addyear(true)"></div>
  </div>
  <div class="days" v-if="state.yyyy == false && state.mmmm == false">
    <div class="title">
      <span>日</span>
      <span>一</span>
      <span>二</span>
      <span>三</span>
      <span>四</span>
      <span>五</span>
      <span>六</span>
    </div>
    <div class="nr">
      <div class="linenr">
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[0] == 'last' || state.dayztlist[0] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[0] == 'not' || state.dayztlist[0] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[0] == 'yes'
                ? state.clicknum == 0
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : '',
            backgroundColor: state.clicknum == 0 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[0] == 'yes' ? '5px' : state.clicknum == 0 ? '5px' : '',
          }"
          @click="handleClick(0)"
        >
          {{ state.daylist[0] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[1] == 'last' || state.dayztlist[1] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[1] == 'not' || state.dayztlist[1] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[1] == 'yes'
                ? state.clicknum == 1
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 1
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 1 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[1] == 'yes' ? '5px' : state.clicknum == 1 ? '5px' : '',
          }"
          @click="handleClick(1)"
        >
          {{ state.daylist[1] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[2] == 'last' || state.dayztlist[2] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[2] == 'not' || state.dayztlist[2] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[2] == 'yes'
                ? state.clicknum == 2
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 2
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 2 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[2] == 'yes' ? '5px' : state.clicknum == 2 ? '5px' : '',
          }"
          @click="handleClick(2)"
        >
          {{ state.daylist[2] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[3] == 'last' || state.dayztlist[3] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[3] == 'not' || state.dayztlist[3] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[3] == 'yes'
                ? state.clicknum == 3
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 3
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 3 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[3] == 'yes' ? '5px' : state.clicknum == 3 ? '5px' : '',
          }"
          @click="handleClick(3)"
        >
          {{ state.daylist[3] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[4] == 'last' || state.dayztlist[4] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[4] == 'not' || state.dayztlist[4] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[4] == 'yes'
                ? state.clicknum == 4
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 4
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 4 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[4] == 'yes' ? '5px' : state.clicknum == 4 ? '5px' : '',
          }"
          @click="handleClick(4)"
        >
          {{ state.daylist[4] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[5] == 'last' || state.dayztlist[5] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[5] == 'not' || state.dayztlist[5] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[5] == 'yes'
                ? state.clicknum == 5
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 5
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 5 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[5] == 'yes' ? '5px' : state.clicknum == 5 ? '5px' : '',
          }"
          @click="handleClick(5)"
        >
          {{ state.daylist[5] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[6] == 'last' || state.dayztlist[6] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[6] == 'not' || state.dayztlist[6] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[6] == 'yes'
                ? state.clicknum == 6
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 6
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 6 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[6] == 'yes' ? '5px' : state.clicknum == 6 ? '5px' : '',
          }"
          @click="handleClick(6)"
        >
          {{ state.daylist[6] }}
        </div>
      </div>
      <div class="linenr">
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[7] == 'last' || state.dayztlist[7] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[7] == 'not' || state.dayztlist[7] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[7] == 'yes'
                ? state.clicknum == 7
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 7
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 7 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[7] == 'yes' ? '5px' : state.clicknum == 7 ? '5px' : '',
          }"
          @click="handleClick(7)"
        >
          {{ state.daylist[7] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[8] == 'last' || state.dayztlist[8] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[8] == 'not' || state.dayztlist[8] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[8] == 'yes'
                ? state.clicknum == 8
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 8
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 8 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[8] == 'yes' ? '5px' : state.clicknum == 8 ? '5px' : '',
          }"
          @click="handleClick(8)"
        >
          {{ state.daylist[8] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[9] == 'last' || state.dayztlist[9] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[9] == 'not' || state.dayztlist[9] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[9] == 'yes'
                ? state.clicknum == 9
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 9
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 9 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[9] == 'yes' ? '5px' : state.clicknum == 9 ? '5px' : '',
          }"
          @click="handleClick(9)"
        >
          {{ state.daylist[9] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[10] == 'last' || state.dayztlist[10] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[10] == 'not' || state.dayztlist[10] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[10] == 'yes'
                ? state.clicknum == 10
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 10
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 10 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[10] == 'yes' ? '5px' : state.clicknum == 10 ? '5px' : '',
          }"
          @click="handleClick(10)"
        >
          {{ state.daylist[10] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[11] == 'last' || state.dayztlist[11] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[11] == 'not' || state.dayztlist[11] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[11] == 'yes'
                ? state.clicknum == 11
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 11
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 11 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[11] == 'yes' ? '5px' : state.clicknum == 11 ? '5px' : '',
          }"
          @click="handleClick(11)"
        >
          {{ state.daylist[11] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[12] == 'last' || state.dayztlist[12] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[12] == 'not' || state.dayztlist[12] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[12] == 'yes'
                ? state.clicknum == 12
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 12
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 12 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[12] == 'yes' ? '5px' : state.clicknum == 12 ? '5px' : '',
          }"
          @click="handleClick(12)"
        >
          {{ state.daylist[12] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[13] == 'last' || state.dayztlist[13] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[13] == 'not' || state.dayztlist[13] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[13] == 'yes'
                ? state.clicknum == 13
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 13
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 13 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[13] == 'yes' ? '5px' : state.clicknum == 13 ? '5px' : '',
          }"
          @click="handleClick(13)"
        >
          {{ state.daylist[13] }}
        </div>
      </div>
      <div class="linenr">
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[14] == 'last' || state.dayztlist[14] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[14] == 'not' || state.dayztlist[14] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[14] == 'yes'
                ? state.clicknum == 14
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 14
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 14 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[14] == 'yes' ? '5px' : state.clicknum == 14 ? '5px' : '',
          }"
          @click="handleClick(14)"
        >
          {{ state.daylist[14] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[15] == 'last' || state.dayztlist[15] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[15] == 'not' || state.dayztlist[15] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[15] == 'yes'
                ? state.clicknum == 15
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 15
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 15 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[15] == 'yes' ? '5px' : state.clicknum == 15 ? '5px' : '',
          }"
          @click="handleClick(15)"
        >
          {{ state.daylist[15] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[16] == 'last' || state.dayztlist[16] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[16] == 'not' || state.dayztlist[16] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[16] == 'yes'
                ? state.clicknum == 16
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 16
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 16 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[16] == 'yes' ? '5px' : state.clicknum == 16 ? '5px' : '',
          }"
          @click="handleClick(16)"
        >
          {{ state.daylist[16] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[17] == 'last' || state.dayztlist[17] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[17] == 'not' || state.dayztlist[17] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[17] == 'yes'
                ? state.clicknum == 17
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 17
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 17 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[17] == 'yes' ? '5px' : state.clicknum == 17 ? '5px' : '',
          }"
          @click="handleClick(17)"
        >
          {{ state.daylist[17] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[18] == 'last' || state.dayztlist[18] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[18] == 'not' || state.dayztlist[18] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[18] == 'yes'
                ? state.clicknum == 18
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 18
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 18 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[18] == 'yes' ? '5px' : state.clicknum == 18 ? '5px' : '',
          }"
          @click="handleClick(18)"
        >
          {{ state.daylist[18] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[19] == 'last' || state.dayztlist[19] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[19] == 'not' || state.dayztlist[19] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[19] == 'yes'
                ? state.clicknum == 19
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 19
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 19 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[19] == 'yes' ? '5px' : state.clicknum == 19 ? '5px' : '',
          }"
          @click="handleClick(19)"
        >
          {{ state.daylist[19] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[20] == 'last' || state.dayztlist[20] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[20] == 'not' || state.dayztlist[20] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[20] == 'yes'
                ? state.clicknum == 20
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 20
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 20 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[20] == 'yes' ? '5px' : state.clicknum == 20 ? '5px' : '',
          }"
          @click="handleClick(20)"
        >
          {{ state.daylist[20] }}
        </div>
      </div>
      <div class="linenr">
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[21] == 'last' || state.dayztlist[21] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[21] == 'not' || state.dayztlist[21] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[21] == 'yes'
                ? state.clicknum == 21
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 21
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 21 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[21] == 'yes' ? '5px' : state.clicknum == 21 ? '5px' : '',
          }"
          @click="handleClick(21)"
        >
          {{ state.daylist[21] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[22] == 'last' || state.dayztlist[22] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[22] == 'not' || state.dayztlist[22] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[22] == 'yes'
                ? state.clicknum == 22
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 22
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 22 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[22] == 'yes' ? '5px' : state.clicknum == 22 ? '5px' : '',
          }"
          @click="handleClick(22)"
        >
          {{ state.daylist[22] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[23] == 'last' || state.dayztlist[23] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[23] == 'not' || state.dayztlist[23] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[23] == 'yes'
                ? state.clicknum == 23
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 23
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 23 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[23] == 'yes' ? '5px' : state.clicknum == 23 ? '5px' : '',
          }"
          @click="handleClick(23)"
        >
          {{ state.daylist[23] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[24] == 'last' || state.dayztlist[24] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[24] == 'not' || state.dayztlist[24] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[24] == 'yes'
                ? state.clicknum == 24
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 24
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 24 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[24] == 'yes' ? '5px' : state.clicknum == 24 ? '5px' : '',
          }"
          @click="handleClick(24)"
        >
          {{ state.daylist[24] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[25] == 'last' || state.dayztlist[25] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[25] == 'not' || state.dayztlist[25] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[25] == 'yes'
                ? state.clicknum == 25
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 25
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 25 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[25] == 'yes' ? '5px' : state.clicknum == 25 ? '5px' : '',
          }"
          @click="handleClick(25)"
        >
          {{ state.daylist[25] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[26] == 'last' || state.dayztlist[26] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[26] == 'not' || state.dayztlist[26] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[26] == 'yes'
                ? state.clicknum == 26
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 26
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 26 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[26] == 'yes' ? '5px' : state.clicknum == 26 ? '5px' : '',
          }"
          @click="handleClick(26)"
        >
          {{ state.daylist[26] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[27] == 'last' || state.dayztlist[27] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[27] == 'not' || state.dayztlist[27] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[27] == 'yes'
                ? state.clicknum == 27
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 27
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 27 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[27] == 'yes' ? '5px' : state.clicknum == 27 ? '5px' : '',
          }"
          @click="handleClick(27)"
        >
          {{ state.daylist[27] }}
        </div>
      </div>
      <div class="linenr">
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[28] == 'last' || state.dayztlist[28] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[28] == 'not' || state.dayztlist[28] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[28] == 'yes'
                ? state.clicknum == 28
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 28
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 28 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[28] == 'yes' ? '5px' : state.clicknum == 28 ? '5px' : '',
          }"
          @click="handleClick(28)"
        >
          {{ state.daylist[28] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[29] == 'last' || state.dayztlist[29] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[29] == 'not' || state.dayztlist[29] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[29] == 'yes'
                ? state.clicknum == 29
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 29
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 29 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[29] == 'yes' ? '5px' : state.clicknum == 29 ? '5px' : '',
          }"
          @click="handleClick(29)"
        >
          {{ state.daylist[29] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[30] == 'last' || state.dayztlist[30] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[30] == 'not' || state.dayztlist[30] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[30] == 'yes'
                ? state.clicknum == 30
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 30
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 30 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[30] == 'yes' ? '5px' : state.clicknum == 30 ? '5px' : '',
          }"
          @click="handleClick(30)"
        >
          {{ state.daylist[30] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[31] == 'last' || state.dayztlist[31] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[31] == 'not' || state.dayztlist[31] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[31] == 'yes'
                ? state.clicknum == 31
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 31
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 31 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[31] == 'yes' ? '5px' : state.clicknum == 31 ? '5px' : '',
          }"
          @click="handleClick(31)"
        >
          {{ state.daylist[31] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[32] == 'last' || state.dayztlist[32] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[32] == 'not' || state.dayztlist[32] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[32] == 'yes'
                ? state.clicknum == 32
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 32
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 32 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[32] == 'yes' ? '5px' : state.clicknum == 32 ? '5px' : '',
          }"
          @click="handleClick(32)"
        >
          {{ state.daylist[32] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[33] == 'last' || state.dayztlist[33] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[33] == 'not' || state.dayztlist[33] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[33] == 'yes'
                ? state.clicknum == 33
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 33
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 33 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[33] == 'yes' ? '5px' : state.clicknum == 33 ? '5px' : '',
          }"
          @click="handleClick(33)"
        >
          {{ state.daylist[33] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[34] == 'last' || state.dayztlist[34] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[34] == 'not' || state.dayztlist[34] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[34] == 'yes'
                ? state.clicknum == 34
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 34
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 34 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[34] == 'yes' ? '5px' : state.clicknum == 34 ? '5px' : '',
          }"
          @click="handleClick(34)"
        >
          {{ state.daylist[34] }}
        </div>
      </div>
      <div class="linenr">
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[35] == 'last' || state.dayztlist[35] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[35] == 'not' || state.dayztlist[35] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[35] == 'yes'
                ? state.clicknum == 35
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 35
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 35 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[35] == 'yes' ? '5px' : state.clicknum == 35 ? '5px' : '',
          }"
          @click="handleClick(35)"
        >
          {{ state.daylist[35] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[36] == 'last' || state.dayztlist[36] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[36] == 'not' || state.dayztlist[36] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[36] == 'yes'
                ? state.clicknum == 36
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 36
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 36 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[36] == 'yes' ? '5px' : state.clicknum == 36 ? '5px' : '',
          }"
          @click="handleClick(36)"
        >
          {{ state.daylist[36] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[37] == 'last' || state.dayztlist[37] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[37] == 'not' || state.dayztlist[37] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[37] == 'yes'
                ? state.clicknum == 37
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 37
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 37 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[37] == 'yes' ? '5px' : state.clicknum == 37 ? '5px' : '',
          }"
          @click="handleClick(37)"
        >
          {{ state.daylist[37] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[38] == 'last' || state.dayztlist[38] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[38] == 'not' || state.dayztlist[38] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[38] == 'yes'
                ? state.clicknum == 38
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 38
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 38 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[38] == 'yes' ? '5px' : state.clicknum == 38 ? '5px' : '',
          }"
          @click="handleClick(38)"
        >
          {{ state.daylist[38] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[39] == 'last' || state.dayztlist[39] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[39] == 'not' || state.dayztlist[39] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[39] == 'yes'
                ? state.clicknum == 39
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 39
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 39 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[39] == 'yes' ? '5px' : state.clicknum == 39 ? '5px' : '',
          }"
          @click="handleClick(39)"
        >
          {{ state.daylist[39] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[40] == 'last' || state.dayztlist[40] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[40] == 'not' || state.dayztlist[40] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[40] == 'yes'
                ? state.clicknum == 40
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 40
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 40 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[40] == 'yes' ? '5px' : state.clicknum == 40 ? '5px' : '',
          }"
          @click="handleClick(40)"
        >
          {{ state.daylist[40] }}
        </div>
        <div
          class="day"
          :style="{
            color:
              state.dayztlist[41] == 'last' || state.dayztlist[41] == 'next'
                ? '#C7C7C7'
                : state.dayztlist[41] == 'not' || state.dayztlist[41] == 'yes'
                ? '#1C1C28'
                : '',
            border:
              state.dayztlist[41] == 'yes'
                ? state.clicknum == 41
                  ? '1px solid #3259CE'
                  : '1px dashed #3259CE'
                : state.clicknum == 41
                ? '1px solid #3259CE'
                : '',
            backgroundColor: state.clicknum == 41 ? '#EBF3FA' : '',
            borderRadius:
              state.dayztlist[41] == 'yes' ? '5px' : state.clicknum == 41 ? '5px' : '',
          }"
          @click="handleClick(41)"
        >
          {{ state.daylist[41] }}
        </div>
      </div>
    </div>
  </div>
  <div class="days" v-if="state.yyyy">
    <div class="yynr">
      <div class="linenr">
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10))">
          {{ state.year - (state.year % 10) }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 1)">
          {{ state.year - (state.year % 10) + 1 }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 2)">
          {{ state.year - (state.year % 10) + 2 }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 3)">
          {{ state.year - (state.year % 10) + 3 }}
        </div>
      </div>
      <div class="linenr">
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 4)">
          {{ state.year - (state.year % 10) + 4 }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 5)">
          {{ state.year - (state.year % 10) + 5 }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 6)">
          {{ state.year - (state.year % 10) + 6 }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 7)">
          {{ state.year - (state.year % 10) + 7 }}
        </div>
      </div>
      <div class="linenr1">
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 8)">
          {{ state.year - (state.year % 10) + 8 }}
        </div>
        <div class="yyyynr" @click="clickynr(state.year - (state.year % 10) + 9)">
          {{ state.year - (state.year % 10) + 9 }}
        </div>
      </div>
    </div>
  </div>
  <div class="days" v-if="state.mmmm">
    <div class="yynr">
      <div class="linenr">
        <div class="yyyynr" @click="clickmnr(1)">1月</div>
        <div class="yyyynr" @click="clickmnr(2)">2月</div>
        <div class="yyyynr" @click="clickmnr(3)">3月</div>
        <div class="yyyynr" @click="clickmnr(4)">4月</div>
      </div>
      <div class="linenr">
        <div class="yyyynr" @click="clickmnr(5)">5月</div>
        <div class="yyyynr" @click="clickmnr(6)">6月</div>
        <div class="yyyynr" @click="clickmnr(7)">7月</div>
        <div class="yyyynr" @click="clickmnr(8)">8月</div>
      </div>
      <div class="linenr">
        <div class="yyyynr" @click="clickmnr(9)">9月</div>
        <div class="yyyynr" @click="clickmnr(10)">10月</div>
        <div class="yyyynr" @click="clickmnr(11)">11月</div>
        <div class="yyyynr" @click="clickmnr(12)">12月</div>
      </div>
    </div>
  </div>
  <div class="line" v-if="state.yyyy == false && state.mmmm == false"></div>
  <div class="time_btn" v-if="state.yyyy == false && state.mmmm == false">
    <el-input
      class="time"
      id="ipt"
      type="time"
      v-model="state.time"
      placeholder="请输入时间(冒号分隔)"
      step="2"
    />
    <el-button
      class="btn"
      @click="submit"
      color="#1A59E6"
      plain
      v-if="state.clickDate == '' && state.time == ''"
      >此刻</el-button
    >
    <el-button
      class="btn"
      @click="submit"
      color="#1A59E6"
      plain
      v-if="state.clickDate || state.time"
      >确定</el-button
    >
  </div>
</template>

<script setup>
import { dayjs } from "element-plus";
const emit = defineEmits(["datetime"]);
const otherStroe = useOtherStore();
const datetimes = otherStroe.datetimes;
const props = defineProps({
  date: {
    type: String,
    default: () => "",
  },
});
const input = ref();
const state = reactive({
  yyyy: false,
  mmmm: false,
  clicknum: -1,
  clickday: 0,
  changeclick: false,
  offest: 7,
  firstweek: 0,
  lastMonthDay: 0,
  nextMonthDay: 0,
  year: 0,
  month: 0,
  day: datetimes.date,
  daylist: [], //42个
  dayztlist: [],
  clickDate: "",
  time: "",
});
const handleClick = (v) => {
  state.clicknum = v;
  state.clickday = state.daylist[v];
  if (state.dayztlist[v] == "last") {
    submonth(false);
  } else if (state.dayztlist[v] == "next") {
    addmonth(false);
  }
  if (state.daylist[state.clicknum]) {
    state.clickDate = state.year + "-" + state.month + "-" + state.clickday;
  }
  if (state.clickDate) {
    emit("datetime", state.clickDate + " " + state.time, true);
  }
};
const submit = (v) => {
  if (state.clickDate && state.time) {
    emit("datetime", state.clickDate + " " + state.time, false);
  } else if (state.clickDate && state.time == "") {
    emit("datetime", state.clickDate + " " + "00:00:00", false);
  } else if (state.clickDate == "" && state.time) {
    emit(
      "datetime",
      dayjs(datetimes.datetime).format("YYYY-MM-DD") + " " + state.time,
      false
    );
  } else {
    emit("datetime", dayjs(datetimes.datetime).format("YYYY-MM-DD HH:mm:ss"), false);
  }
};
const subyear = (v) => {
  state.changeclick = v;
  if (state.yyyy) {
    state.year -= 10;
  } else {
    state.year -= 1;
  }
  state.firstweek = new Date(state.year + "-" + state.month + "-01").getDay();
};
const submonth = (v) => {
  state.changeclick = v;
  if (state.month == 1) {
    state.month = 12;
    state.year = state.year - 1;
  } else {
    state.month -= 1;
  }
  state.firstweek = new Date(state.year + "-" + state.month + "-01").getDay();
};
const addyear = (v) => {
  state.changeclick = v;
  if (state.yyyy) {
    state.year += 10;
  } else {
    state.year += 1;
  }
  state.firstweek = new Date(state.year + "-" + state.month + "-01").getDay();
};
const addmonth = (v) => {
  state.changeclick = v;
  if (state.month == 12) {
    state.month = 1;
    state.year = state.year + 1;
  } else {
    state.month += 1;
  }
  state.firstweek = new Date(state.year + "-" + state.month + "-01").getDay();
};
const dayshow = () => {
  state.daylist = [];
  state.dayztlist = [];
  for (
    let i = state.lastMonthDay;
    i <= new Date(state.year, state.month - 1, 0).getDate();
    i++
  ) {
    state.daylist.push(i);
    state.dayztlist.push("last");
  }
  for (let i = 1; i <= new Date(state.year, state.month, 0).getDate(); i++) {
    state.daylist.push(i);
    if (state.year + "年" + state.month + "月" + i + "日" == state.day) {
      state.dayztlist.push("yes");
    } else {
      state.dayztlist.push("not");
    }
  }
  for (let i = 1; i <= state.nextMonthDay; i++) {
    state.daylist.push(i);
    state.dayztlist.push("next");
  }
  // for (let i = 0; i < state.dayztlist.length; i++) {
  //   if (state.dayztlist[i] == "yes") {
  //     state.clicknum = i;
  //   }
  // }
  //   for (let i = 0; i < arr.length; i += 7) {
  //     state.daylist.push(arr.slice(i, i + 7));
  //   }
  //   for (let i = 0; i < zt.length; i += 7) {
  //     state.dayztlist.push(zt.slice(i, i + 7));
  //   }
};
const yyyy = () => {
  state.yyyy = true;
  state.mmmm = false;
};
const mmmm = () => {
  state.mmmm = true;
  state.yyyy = false;
};
const clickynr = (v) => {
  state.changeclick = v;
  state.year = v;
  mmmm();
  state.firstweek = new Date(state.year + "-" + state.month + "-01").getDay();
};
const clickmnr = (v) => {
  state.changeclick = v;
  state.month = v;
  state.yyyy = false;
  state.mmmm = false;
  state.firstweek = new Date(state.year + "-" + state.month + "-01").getDay();
};
onMounted(() => {
  state.year = props.date
    ? Number(dayjs(props.date).format("YYYY"))
    : Number(datetimes.date.split("年")[0]);
  state.month = props.date
    ? Number(dayjs(props.date).format("M"))
    : Number(datetimes.date.split("年")[1].split("月")[0]);
  state.clickday = props.date ? Number(dayjs(props.date).format("D")) : 0;
  state.firstweek = props.date
    ? new Date(dayjs(props.date).format("YYYY-MM-01")).getDay()
    : new Date(dayjs(datetimes.datetime).format("YYYY-MM-01")).getDay();
  state.time = props.date ? props.date.split(" ")[1] : "";
  if (state.firstweek == 0) {
    state.lastMonthDay =
      new Date(state.year, state.month - 1, 0).getDate() - state.offest + 1;
  } else {
    state.lastMonthDay =
      new Date(state.year, state.month - 1, 0).getDate() - state.firstweek + 1;
  }
  state.nextMonthDay =
    42 -
    (new Date(state.year, state.month - 1, 0).getDate() -
      state.lastMonthDay +
      1 +
      new Date(state.year, state.month, 0).getDate());
  dayshow();
});
watch(
  () => [state.year, state.month],
  (newVal) => {
    console.log("?????", dayjs(props.date).format("DD"));
    let ym = state.year + "-" + state.month;
    console.log("????", ym);
    if (ym == dayjs(props.date).format("YYYY-MM")) {
      state.changeclick = false;
      state.clickday = dayjs(props.date).format("DD");
    }
    if (state.firstweek == 0) {
      state.lastMonthDay =
        new Date(state.year, state.month - 1, 0).getDate() - state.offest + 1;
    } else {
      state.lastMonthDay =
        new Date(state.year, state.month - 1, 0).getDate() - state.firstweek + 1;
    }
    state.nextMonthDay =
      42 -
      (new Date(state.year, state.month - 1, 0).getDate() -
        state.lastMonthDay +
        1 +
        new Date(state.year, state.month, 0).getDate());
    dayshow();
  }
);
watch(
  () => [state.daylist, state.dayztlist, state.changeclick],
  (newVal) => {
    if (state.changeclick == false) {
      let position = [];
      for (let i = 0; i < state.daylist.length; i++) {
        if (state.daylist[i] == state.clickday) {
          position.push(i);
        }
      }
      position.forEach((e) => {
        if (state.dayztlist[e] == "not" || state.dayztlist[e] == "yes") {
          state.clicknum = e;
        }
      });
    } else {
      state.clicknum = -1;
    }
    if (state.daylist[state.clicknum]) {
      state.clickDate =
        state.year + "-" + state.month + "-" + state.daylist[state.clicknum];
    }
  }
);
</script>
<style lang="scss" scoped>
.ym {
  width: 256px;
  height: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  .zy {
    width: 15px;
    height: 15px;
    font-size: 15px;
    display: flex;
    align-items: center;
    &::before {
      cursor: pointer;
    }
  }
  .zm {
    width: 15px;
    height: 15px;
    font-size: 15px;
    display: flex;
    align-items: center;
    transform: rotateY(180deg);
    &::before {
      cursor: pointer;
    }
  }
  .date {
    // width: 83px;
    height: 15px;
    font-size: 15px;
    font-family: Microsoft YaHei UI;
    color: #1c1c28;
    display: flex;
    justify-content: center;
    align-items: center;
    .yyyy {
      // width: 51px;
      height: 15px;
      display: flex;
      .dy {
        width: 36px;
        height: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
      }
      .dw {
        height: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
      }
      &:hover {
        color: #409eff;
      }
    }
    .mmmm {
      width: 33px;
      height: 15px;
      display: flex;
      .dm {
        width: 18px;
        height: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
      }
      .dw {
        height: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
      }
      &:hover {
        color: #409eff;
      }
    }
  }
  .ym {
    width: 15px;
    height: 15px;
    font-size: 15px;
    display: flex;
    align-items: center;
    &::before {
      cursor: pointer;
    }
  }
  .yy {
    width: 15px;
    height: 15px;
    font-size: 15px;
    display: flex;
    align-items: center;
    transform: rotateY(180deg);
    &::before {
      cursor: pointer;
    }
  }
}
.days {
  width: 100%;
  max-height: 254px;
  padding: 29px 0 12px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  .title {
    width: 239px;
    height: 14px;
    font-size: 14px;
    font-family: Microsoft YaHei UI;
    color: #b3b3b3;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 3px;
  }
  .nr {
    width: 250px;
    height: 192px;
    .linenr {
      margin-top: 16px;
      width: 100%;
      height: 16px;
      font-size: 16px;
      font-family: Microsoft YaHei UI;
      color: #c7c7c7;
      display: flex;
      justify-content: space-between;
      align-items: center;
      .day {
        width: 25px;
        height: 25px;
        font-size: 16px;
        font-family: Microsoft YaHei UI;
        color: #1c1c28;
        display: flex;
        justify-content: center;
        align-items: center;
        &:hover {
          background: #ebf3fa;
          border: 1px solid #3259ce;
          border-radius: 5px;
        }
      }
    }
  }
  .yynr {
    width: 250px;
    display: flex;
    flex-direction: column;
    .linenr {
      margin-top: 16px;
      margin-bottom: 16px;
      width: 100%;
      height: 16px;
      font-size: 16px;
      font-family: Microsoft YaHei UI;
      color: #1c1c28;
      display: flex;
      justify-content: space-between;
      align-items: center;
      .yyyynr {
        width: 38px;
        height: 25px;
        font-size: 16px;
        font-family: Microsoft YaHei UI;
        color: #1c1c28;
        display: flex;
        justify-content: center;
        align-items: center;
        &:hover {
          color: #409eff;
        }
      }
    }
    .linenr1 {
      margin-top: 16px;
      width: 108.67px;
      height: 16px;
      font-size: 16px;
      font-family: Microsoft YaHei UI;
      color: #1c1c28;
      display: flex;
      justify-content: space-between;
      align-items: center;
      .yyyynr {
        width: 38px;
        height: 25px;
        font-size: 16px;
        font-family: Microsoft YaHei UI;
        color: #1c1c28;
        display: flex;
        justify-content: center;
        align-items: center;
        &:hover {
          color: #409eff;
        }
      }
    }
  }
}
.line {
  width: 278px;
  height: 1px;
  border: 1px solid rgba(199, 199, 199, 0.5);
}
.time_btn {
  margin-top: 11px;
  width: 265px;
  height: 26px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  .time {
    width: 188px;
    height: 26px;
  }
  .btn {
    width: 66px;
    height: 26px;
  }
}
:deep(.el-input__inner) {
  height: 100%;
}
</style>
