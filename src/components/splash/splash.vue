<template>
    <div id="splash-component">
        <div id="splash-form-one">
            <div id="splash-gradient-one">
                <div class="title">
                    <p>Hajime is </p>
                    <ul id="qualities">
                        <li v-for="quality in qualities" :key="quality.quality">{{ quality }}</li>
                    </ul>
                </div>
            </div>
            <svg id="svg-one" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none">
                <polygon filter="url(#dropshadow)" fill="white" points="0,70 0,100 100,100 100,0 75,60 50,75"/>
                <filter id="dropshadow" height="130%">
                    <feGaussianBlur in="SourceAlpha" stdDeviation="4"/> <!-- stdDeviation is how much to blur -->
                    <feOffset dx="1" dy="1" result="offsetblur"/> <!-- how much to offset -->
                    <feComponentTransfer>
                        <feFuncA type="linear" slope="0.5"/> <!-- slope is the opacity of the shadow -->
                    </feComponentTransfer>
                    <feMerge>
                        <feMergeNode/> <!-- this contains the offset blurred image -->
                        <feMergeNode in="SourceGraphic"/>
                        <!-- this contains the element that the filter is applied to -->
                    </feMerge>
                </filter>
            </svg>
        </div>
        <div id="splash-form-two">
            <div id="splash-container">
                <svg id="svg-two" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none">
                    <polygon filter="url(#dropshadow-two)" fill="white" points="0,0 0,75 100,75 100,0 "/>
                    <filter id="dropshadow-two" height="130%">
                        <feGaussianBlur in="SourceAlpha" stdDeviation="8"/> <!-- stdDeviation is how much to blur -->
                        <feOffset dx="1" dy="-1" result="offsetblur"/> <!-- how much to offset -->
                        <feComponentTransfer>
                            <feFuncA type="linear" slope="0.5"/> <!-- slope is the opacity of the shadow -->
                        </feComponentTransfer>
                        <feMerge>
                            <feMergeNode/> <!-- this contains the offset blurred image -->
                            <feMergeNode in="SourceGraphic"/>
                            <!-- this contains the element that the filter is applied to -->
                        </feMerge>
                    </filter>
                </svg>
                <div id="splash-gradient-two">
                    <div>
                        <div id="icon-container">
                            <span></span>
                            <div class="icon">
                                <div>Conversational Interface</div>
                                <img class="icon-img" src="../../assets/img/speech-bubble.png"/>
                                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. </p>
                            </div>
                            <div class="icon">
                                <div>Medical Expertise</div>
                                <img class="icon-img" src="../../assets/img/doctor-icon-white.png"/>
                                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. </p>
                            </div>
                            <div class="icon">
                                <div>Machine learning</div>
                                <img class="icon-img" src="../../assets/img/ml.png"/>
                                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. </p>
                            </div>
                            <div class="icon">
                                <div>Data</div>
                                <img class="icon-img" src="../../assets/img/data-encryption.png"/>
                                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. </p>
                            </div>
                            <span></span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "splash.vue",
        data() {
            return {
                qualities: ["Helpful"]
            }
        }
    }
</script>

<style scoped>

    #splash-component {
        display: flex;
        flex-direction: column;
        position: relative;
        width: 100vw;
        height: 100vh;
    }

    #splash-form-one {
        width: 50%;
        height: 60%;
        background: #C779D0;
        border-radius: 5px;
        will-change: transform, opacity;
        opacity: 0;
        transform: translateY(-100%);
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 0.5s 1 slideInFromTopWithOpacity forwards;
    }

    #splash-gradient-one {
        width: 100%;
        height: 100%;
        will-change: transform;
        transform: translateY(-100%);
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 1s 1 slideInFromTop forwards;
        background: #FEAC5E; /* fallback for old browsers */
        background: -webkit-linear-gradient(to top, #C779D0, #C779D0, #FEAC5E); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to top, #C779D0, #C779D0, #FEAC5E); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    }

    #svg-one {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        /* set height to pixels if you want angle to change with screen width */

    }

    #splash-form-two {
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 55%;
        overflow: hidden;
        will-change: transform, opacity;
        transform: translateY(100%);
        opacity: 0;
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 0.5s 1 slideInFromBottomWithOpacity forwards;
        border-radius: 5px;
    }

    #splash-container {
        width: 100%;
        height: 100%;
        will-change: transform;
        background: #C779D0;
        overflow-Y: hidden;
    }

    #splash-gradient-two {
        position: absolute;
        top: 0;
        z-index: -10;
        width: 100%;
        height: 100%;
        animation: 2s cubic-bezier(0.215, 0.61, 0.355, 1) 0.5s 1 slideInFromBottom forwards;
        background: #FEAC5E; /* fallback for old browsers */
        background: -webkit-linear-gradient(to top, #FEAC5E, #C779D0); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to top, #FEAC5E, #C779D0); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    }

    #svg-two {
        width: 100%;
        height: 20%;
        /* set height to pixels if you want angle to change with screen width */
    }

    .title {
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        position: relative;
        top: 24%;
        margin-left: 16px;
        color: #FFF;
        font-family: "Bebas Neue", sans-serif;
        font-size: 100px;
        font-style: normal;
        font-variant: normal;
        font-weight: 500;
        line-height: 26.4px;
        opacity: 0;
        animation: 2s cubic-bezier(0.215, 0.61, 0.355, 1) 1s 1 slideInFromTopWithOpacity forwards;
    }

    #icon-container {
        width: 100%;
        height: 80%;
        margin-top: 8%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        color: #FFF;
        font-family: "Bebas Neue", sans-serif;
        font-size: 24px;
        font-style: normal;
        font-variant: normal;
        font-weight: 500;
        line-height: 26.4px;
        opacity: 0;
        animation: 2s cubic-bezier(0.215, 0.61, 0.355, 1) 1s 1 slideInFromBottomWithOpacity forwards;
    }

    .icon {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-content: center;
        align-items: center;
        width: 20%;
        height: 100%;
    }

    .icon div {
        margin-bottom: 4%;
    }

    .icon-img {
        width: 50%;
        height: 50%;
        margin-bottom: 4%;
    }

    .icon p {
        font-family: "Bebas Neue", sans-serif;
        font-size: 16px;
        font-style: normal;
        font-variant: normal;
        font-weight: 500;
        line-height: 26.4px;
        text-align: center;
    }

    #qualities {
        margin-left: 16px;
    }

    @keyframes slideInFromTop {
        0% {
            transform: translateY(-100%);
        }
        100% {
            transform: translateY(0);
        }
    }

    @keyframes slideInFromBottom {
        0% {
            transform: translateY(100%);
        }
        100% {
            transform: translateY(0);
        }
    }

    @keyframes slideInFromTopWithOpacity {
        0% {
            transform: translateY(-100%);
            opacity: 0;
        }
        100% {
            transform: translateY(0);
            opacity: 1;
        }
    }

    @keyframes slideInFromBottomWithOpacity {
        0% {
            transform: translateY(100%);
            opacity: 0;
        }
        100% {
            transform: translateY(0);
            opacity: 1;
        }
    }


</style>