<template>
    <div class="writebox">
        <form class="sendbox" action="#" @submit.prevent="onFormSubmit" >
            <input type="text" v-model="input">
              <transition v-if="showModal" name="modal">
                <div class="modal-mask">

                <div class="modal-wrapper">
                    <div class="modal-container">

                    <div class="modal-header">
                        <slot name="header">
                        FORBBIDEN
                        </slot>
                    </div>

                    <div class="modal-body">
                        <slot name="body">
                        BigBrother is watching you !
                        <div class="stage">
                            <figure class="ball">
                                <span class="iris"></span>
                            </figure>
                        </div>
                        </slot>
                    </div>

                    <div class="modal-footer">
                        <slot name="footer">
                        <button class="modal-default-button" @click="closeModal">
                            X
                        </button>
                        </slot>
                    </div>
                    </div>
                </div>
                </div>
            </transition>
            <button class="send"><div class="arrow"></div></button>
        </form>
    </div>
</template>

<script>
export default {
  data () {
    return {
      input: '',
      life: 5,
      whitelist: ['cc', 'fdp', 'connard', 'pd'],
      showModal: false,
      banned: false
    }
  },
  methods: {
    onFormSubmit () {
      if (this.whitelist.indexOf(this.input) > -1) {
        this.life--
        this.showModal = true
        console.log(this.life)
        if (this.life == 0) {
          this.banned
          this.life = 5
        }
      }
      if (this.input != '') {
        this.$emit('messageSent', this.input)
        this.input = ''
      }
    },
    closeModal () {
      this.showModal = false
      console.log('Modal fermer')
    }
  }
}
</script>

<style lang="stylus">
    .writebox
        margin-top: 10px;
    .sendbox
        background-color: #000000;
        display flex
    input:focus
        outline none
    input
        background-color #000000
        border none
        color #ffffff
        padding: 15px
        border-radius: 20px
        margin-left: 20px
        margin-right: auto
        width: 100%;
        text-align: left
        font-size: 1.3em

    button
        width: 60px
        border-radius: 100%
        border: none
        background:url(../assets/send-icon.svg) no-repeat;
        background-position center
    .modal-mask
        position: fixed;
        z-index: 9998;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, .5);
        display: table;
        transition: opacity .3s ease;

    .modal-wrapper
        display: table-cell;
        vertical-align: middle;

    .modal-container
        width: 500px;
        margin: 0px auto;
        padding: 20px 30px;
        border-radius: 100px!important
        background-color: #000;
        border-radius: 2px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
        transition: all .3s ease;
        font-family: Helvetica, Arial, sans-serif;

    .modal-default-button
        background-image: none
        color white
        border solid 1px white
        border-radius: 10px;
    .modal-header
        margin-top: 0;
        color: #fbea4e;

    .modal-body
        color #fbea4e

    @keyframes move-eye-skew {
        0% {
            transform: none;
        }
        20% {
            transform: translateX(-68px) translateY(30px) skewX(15deg) skewY(-10deg) scale(0.95);
        }
        25%, 44% {
            transform: none;
        }
        50%, 60% {
            transform: translateX(68px) translateY(-40px) skewX(5deg) skewY(2deg) scaleX(0.95);
        }
        66%, 100% {
            transform: none;
        }
    }

    .ball {
        display: inline-block;
        width: 100%;
        height: 100%;
        margin: 0;
        border-radius: 50%;
        position: relative;
        background: radial-gradient(circle at 50% 40%, #fcfcfc, #efeff1 66%, #9b5050 100%);
    }
    .ball:after {
        content: "";
        position: absolute;
        top: 5%;
        left: 10%;
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background: radial-gradient(circle at 50% 50%, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.8) 14%, rgba(255, 255, 255, 0) 24%);
        transform: translateX(-80px) translateY(-90px) skewX(-20deg);
    }

    .iris {
        width: 40%;
        height: 40%;
        margin: 30%;
        right: 0px;
        border-radius: 50%;
        background: radial-gradient(circle at 50% 50%, #ffe100 0%, #f4ff00 30%, #ffe000 100%)
        transform: translateX(68px) translateY(-60px) skewX(15deg) skewY(2deg);
        position: absolute;
        animation: move-eye-skew 5s ease-out infinite;
    }
    .iris:before {
        content: "";
        display: block;
        position: absolute;
        width: 37.5%;
        height: 37.5%;
        border-radius: 50%;
        top: 31.25%;
        left: 31.25%;
        background: black;
    }
    .iris:after {
        content: "";
        display: block;
        position: absolute;
        width: 31.25%;
        height: 31.25%;
        border-radius: 50%;
        top: 18.75%;
        left: 18.75%;
        background: rgba(255, 255, 255, 0.2);
    }

    .ball .shadow {
        position: absolute;
        width: 100%;
        height: 100%;
        background: radial-gradient(circle at 50% 50%, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.1) 40%, rgba(0, 0, 0, 0) 50%);
        transform: rotateX(90deg) translateZ(-150px);
        z-index: -1;
    }
    .stage {
        width: 300px;
        height: 300px;
        display: inline-block;
        margin: 20px;
        perspective: 1200px;
        perspective-origin: 50% 50%;
        transform-style: preserve-3d;
        transform: rotateY(0.01deg);
    }

</style>
