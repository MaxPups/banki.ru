<template>
  <div class="modal" >
    <div class="item">
    <div class="section">
            <div class="slider">
                <input type="radio" id="btn-1" name="toggle" checked>
                <input type="radio" id="btn-2" name="toggle">
                <input type="radio" id="btn-3" name="toggle">
                <div class="slider-controls">
                    <label for="btn-1"></label>
                    <label for="btn-2"></label>
                    <label for="btn-3"></label>
                </div>
                <div class="slider-inner">
                    <div class="slider-slides">
                        <img :src="modal.image" alt="Кекс смотрит на еду">
                        <img :src="modal.image" alt="Кекс смотрит на тебя">
                        <img :src="modal.image" alt="Кекс не хочет никуда смотреть">
                    </div>
                </div>
            </div>
        </div>
    <p class="title">{{modal.title}}</p>
    <p class="price">{{modal.price}} $</p>
    <button @click="hide" id="close">✖</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Modal",
  props: {
    modal: Object,
    hide: Function
  },
};

</script>
<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.555);
}
.item{
    overflow: hidden;
    position: relative;
    width:600px;
    height: 600px;
    background: #5b3a32;
    color: white;
    border-radius: 8px;
}
.item-img{
    width:100%;
    header: 300px;
}
.title{
    padding: 30px;
    font-size: 38px;
    text-align: center;
}
.price{
        font-size: 28px;
text-align: center;
  padding: 30px;
}
#close{
    font-size: 30px;
    position: absolute;
    top: 0px;
    right: 5px;
    border:none;
    background: transparent;
    color: #ffffff;
}
/*  */
.section {
    width: 100%;
    height:300px;
    background-color: white;
}

.slider {
    position: relative;
}

.slider input[type=radio] {
    display: none;
}

.slider-inner {
    overflow: hidden;
}

.slider-slides {
    width: 300%;
    transition: transform 0.8s ease;
}

.slider-slides img {
    float: left;
    width: 600px;
    height: 300px;
}

.slider-controls {
    position: absolute;
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 100;
    text-align: center;
}

.slider-controls label {
    display: inline-block;
    width: 10px;
    height: 10px;
    margin: 0 15px;
    background-color: #cccccc;
    border-radius: 50%;
    box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.8);
    transition: background-color 0.2s;
    cursor: pointer;
}

#btn-1:checked ~ .slider-controls label[for="btn-1"],
#btn-2:checked ~ .slider-controls label[for="btn-2"],
#btn-3:checked ~ .slider-controls label[for="btn-3"] {
    background-color: #666666;
}

#btn-1:checked ~ .slider-inner .slider-slides {
    transform: translate(0);
}

#btn-2:checked ~ .slider-inner .slider-slides {
    transform: translate(calc(-100%/3));
}

#btn-3:checked ~ .slider-inner .slider-slides {
    transform: translate(calc(-100%/1.5));
}
</style>
