<template>
  <div id="container">
    <!-- 1 -->
    <div id="page1">
        <span></span>
    </div>
    <!-- 2 -->
    <div id="page2">
        <span></span>
        <span></span>
    </div>
    <!-- 3 -->
    <div id="page3">
        <span></span>
        <span></span>
        <span></span>
    </div>
    <!-- 4 -->
    <div id="page4">
        <div>
            <span></span>
            <span></span>
        </div>
        <div>
            <span></span>
            <span></span>
        </div>
    </div>
    <!-- 5 -->
    <div id="page5">
        <div>
            <span></span>
            <span></span>
        </div>
        <div>
            <span></span>
        </div>
        <div>
            <span></span>
            <span></span>
        </div>
    </div>
    <!-- 6 -->
    <div id="page6">
        <div>
            <span></span>
            <span></span>
            <span></span>
        </div>
        <div>
            <span></span>
            <span></span>
            <span></span>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TransformDice',
  data () {
    return {}
  }
}
</script>

<style scoped>
#container {
    height: 140px;
    width: 140px;
    position: relative;
    margin: 100px auto;
    transform-style: preserve-3d;
    /* display: flex; */
    justify-content: space-around;
    /* 设置旋转的基准点 */
    transform-origin: 50% 50% -70px;
    -webkit-animation: scroll 6s linear 0s infinite;
}

#container>div {
    width: 100px;
    height: 100px;
    background: #eee;
    border-radius: 10px;
    padding: 20px;
    position: absolute;
}

#container span {
    width: 25px;
    height: 25px;
    background: #000;
    border-radius: 50%;
    display: block;
    box-shadow: inset 3px 3px 5px #fff;
}

#container #page1 span {
    width: 35px;
    height: 35px;
    background: #f00;
}

/* 第一个 */
#container>div:nth-child(1) {
    display: flex;
    justify-content: center;
    align-items: center;
}

/* 2 */
#container>div:nth-child(2) {
    display: flex;
    flex-direction: column;
    /* 在侧轴居中 */
    align-items: center;
    /* 左右边上有边距 */
    justify-content: space-around;
}

/* 3 */
#container>div:nth-child(3) {
    display: flex;
    justify-content: space-between;
}

#container>div:nth-child(3) span:nth-child(2) {
    align-self: center;
}

#container>div:nth-child(3) span:nth-child(3) {
    align-self: flex-end;
}

/* 4 */
#container>div:nth-child(4) {
    display: flex;
    justify-content: space-between;
}

#container>div:nth-child(4) div:nth-child(1),
#container>div:nth-child(4) div:nth-child(2) {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

/* 5 */
#container>div:nth-child(5) {
    display: flex;
    justify-content: space-between;
}

#container>div:nth-child(5) div:nth-child(1),
#container>div:nth-child(5) div:nth-child(3) {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

#container>div:nth-child(5) div:nth-child(2) {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

/* 6 */
#container>div:nth-child(6) {
    display: flex;
    justify-content: space-between;
}

#container>div:nth-child(6) div {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

#container #page2 {
    transform-origin: right;
    /*点数为2的面以右边为转轴转动*/
    transform: rotateY(-90deg);
    /*绕Y轴逆时针转动90度*/
    -webkit-transform-origin: right;
    -webkit-transform: rotateY(-90deg);
    -moz-transform-origin: right;
    -moz-transform: rotateY(-90deg);
}

#container #page3 {
    transform-origin: left;
    /*点数为3的面以左边为转轴转动*/
    transform: rotateY(90deg);
    /*绕Y轴顺时针转动90度*/
    -webkit-transform-origin: left;
    -webkit-transform: rotateY(90deg);
    -moz-transform-origin: left;
    -moz-transform: rotateY(90deg);
}

#container #page4 {
    transform-origin: top;
    /*点数为4的面以上边为转轴转动*/
    transform: rotateX(-90deg);
    /*绕X轴逆时针转动90度*/
    -webkit-transform-origin: top;
    -webkit-transform: rotateX(-90deg);
    -moz-transform-origin: top;
    -moz-transform: rotateX(-90deg);
}

#container #page5 {
    transform-origin: bottom;
    /*点数为5的面以下边为转轴转动*/
    transform: rotateX(90deg);
    /*绕X轴顺时针转动90度*/
    -webkit-transform-origin: bottom;
    -webkit-transform: rotateX(90deg);
    -moz-transform-origin: bottom;
    -moz-transform: rotateX(90deg);
}

#container #page6 {
    transform: translateZ(-100px);
    /*点数为6的面沿Z轴向后平移140px*/
    /*-webkit-transform: translateZ(-140px);*/
    /*-moz-transform: translateZ(-140px);*/
}

/*@keyframes scroll {
    0% {
        transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg);
    }

    25% {
        transform: rotateY(0deg) rotateX(90deg) rotateZ(90deg);
    }

    50% {
        transform: rotateY(0deg) rotateX(180deg) rotateZ(180deg);
    }

    75% {
        transform: rotateY(180deg) rotateX(270deg) rotateZ(270deg);
    }

    100% {
        transform: rotateY(360deg) rotateX(360deg) rotateZ(360deg);
    }
}*/
</style>