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
            <div id="splash-gradient-two">
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
                <div id="splash-gradient-in" ></div>
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
        width: 100vw;
        height: 100vh;
    }


    #splash-form-one {
        position: relative;
        top: 0;
        width: 50%;
        height: 60%;
        background: #4BC0C8;
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
        background: -webkit-linear-gradient(to top, #4BC0C8, #C779D0, #FEAC5E); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to top, #4BC0C8, #C779D0, #FEAC5E); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
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
        will-change: transform, opacity;
        transform: translateY(100%);
        opacity: 0;
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 0.5s 1 slideInFromBottomWithOpacity forwards;
        border-radius: 5px;
    }

    #splash-gradient-two {
        width: 100%;
        height: 100%;
        will-change: transform;
        background: #C779D0;
    }

    #splash-gradient-in{
        width: 100%;
        height: 100%;
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 1s 1 slideInFromBottom forwards;
        background: #FEAC5E; /* fallback for old browsers */
        background: -webkit-linear-gradient(to top, #FEAC5E,  #C779D0); /* Chrome 10-25, Safari 5.1-6 */
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
        top: 32%;
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