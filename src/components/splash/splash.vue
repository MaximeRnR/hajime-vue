<template>
    <div id="splash-component">
        <div id="splash-bg">
            <div id="splash-gradient">
                <div class="title">
                    <p>Hajime is </p>
                    <ul id="qualities">
                        <li v-for="quality in qualities" :key="quality.quality">{{ quality }}</li>
                    </ul>
                </div>
            </div>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none">
                <polygon fill="white" points="0,100 100,0 100,100"/>
            </svg>
        </div>
    </div>
</template>

<script>
    export default {
        name: "splash.vue",
        data() {
            return {
                qualities: ["Innovant"]
            }
        }
    }

</script>

<style scoped>

    #splash-component {
    }

    #splash-bg {
        background: #4BC0C8;
        position: relative;
        width: 100vw;
        height: 80vh;
        border-radius: 5px;
        transform: translate3d(0, 0, 0);
    }

    #splash-gradient {
        width: 100%;
        height: 100%;
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 0s 1 slideInFromTop;
        background: #FEAC5E; /* fallback for old browsers */
        background: -webkit-linear-gradient(to top, #4BC0C8, #C779D0, #FEAC5E); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to top, #4BC0C8, #C779D0, #FEAC5E); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    }

    .title {
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        position: relative;
        top: 50%;
        margin-left: 16px;
        color: #FFF;
        font-family: "Bebas Neue", sans-serif;
        font-size: 100px;
        font-style: normal;
        font-variant: normal;
        font-weight: 500;
        line-height: 26.4px;
        opacity: 0;
        animation: 1s cubic-bezier(0.215, 0.61, 0.355, 1) 1s 1 slideInFromTopWithOpacity forwards;
    }

    #qualities{
        margin-left: 16px;
    }

    svg {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 20vh;
        /* set height to pixels if you want angle to change with screen width */
    }

    @keyframes slideInFromTop {
        0% {
            transform: translateY(-100%);
        }
        100% {
            transform: translateY(0);
        }
    }

    @keyframes slideInFromTopWithOpacity {
        0% {
            transform: translateY(-200%);
            opacity: 0;
        }
        100% {
            transform: translateY(0);
            opacity: 1;
        }
    }


</style>