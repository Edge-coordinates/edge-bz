<script>
    let jq
    import { onMount } from 'svelte'
    import Carousel_02 from '../../components/carousel_02.svelte';
    function parallax_height() {
        var scroll_top = jq(this).scrollTop()
        var sample_section_top = jq('.sample-section').offset().top
        // var h_height = jq('.sample-header-section').outerHeight()
        var header_height = jq(window).height()
        jq('.sample-section').css({ 'margin-top': header_height })
        jq('.sample-header').css({ height: header_height - scroll_top })
    }
    onMount(async () => {
        jq = window.$;
        var header_height = jq(window).height()
        parallax_height()
        jq('.sample-header').css({ height: header_height })
        var valine = new Valine();
        valine.init({
            el: '#vcomments',
            appId: 'bmfiUG79ugFV2EJgR9mPnFIB-gzGzoHsz',
            appKey: '4wn64SFU7lP9BzzhyViOL2Es',
        })
    })
</script>

<svelte:window on:scroll={parallax_height} on:resize={parallax_height} />

<div class="sample-header">
    <div class="sample-header-section">
        <!-- <Carousel_01 /> -->
        
        <!-- <h1>Scroll down to see the parallax effect</h1>
        <h2>Background landcape scrolls with its own depth</h2> -->
    </div>
    <Carousel_02 />
    <div style="position: absolute; bottom: 5%; left:50%;">
        <button class="btn btn-lg btn-ghost shadow-sm text-base-100 text-2xl"
            >向下滚动……</button
        >
    </div>
</div>
<div class="sample-section-wrap">
    <div class="sample-section">
        <h2 class="text-2xl">留言板</h2>
        <div id="vcomments" />
    </div>
</div>

<style>
    /* .webmadewell {
        background-color: white;
    } */
    .sample-header {
        position: fixed;
        left: 0;
        top: 0;
        width: 100%;
        background-image: url('/89991203_p0.jpg');
        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
    }
    .sample-header::before {
        content: '';
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: MidnightBlue;
        opacity: 0.3;
    }
    .sample-header-section {
        position: relative;
        padding: 15% 0 10%;
        width: 100%;
        margin-left: auto;
        margin-right: auto;
        color: white;
        text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.5);
        font-family: 'Montserrat', sans-serif;
    }
    /* h1 {
        font-weight: 500;
    }
    h2 {
        font-weight: 400;
    } */
    .sample-section-wrap {
        position: relative;
        background-color: white;
    }
    .sample-section {
        font-family: 'ZCOOL KuaiLe', sans-serif;
        position: relative;
        margin-left: auto;
        margin-right: auto;
        padding: 40px;
        margin-left: auto;
        margin-right: auto;
        max-width: 1200px;
    }
</style>
