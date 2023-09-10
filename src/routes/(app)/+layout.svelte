<script>
    import ExpandMenu from './expandMenu.svelte'

    import FlowerText from '@/components/flower_text.svelte'

    let isshow = 0
    function handleClick() {
        isshow = !isshow
    }
</script>

<div
    class="navbar bg-neutral rounded-lg shadow-lg fixed top-0 left-0 w-full z-50"
>
    <div class="navbar-start">
        <div class="btn btn-ghost normal-case text-xl text-base-100">
            边缘の小站
        </div>
    </div>
    <div class="navbar-center">
        <ul class="menu menu-horizontal text-base-100">
            <li><a class="link link-hover" href="/">首页</a></li>
            <!-- <li><a class="link link-hover" href="/">教师节</a></li> -->
            <li><a class="link link-hover" href="/about">关于</a></li>
        </ul>
    </div>
    <div class="navbar-end"><ExpandMenu /></div>
</div>

<div>
    <slot />
</div>

{#if isshow}
    <div class="themask">
        <!-- 这里可以添加您的内容 -->
    </div>
    <FlowerText />
{/if}

<div class="fixed-element tooltip" data-tip="打开/关闭鲜花祝福">
    <button class="btn btn-square text-blue-600" on:click={handleClick}>
        {#if !isshow}
            展示鲜花祝福
        {:else}
            隐藏鲜花祝福
        {/if}
    </button>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=ZCOOL+KuaiLe&display=swap');
    .fixed-element {
        position: fixed; /* 使用固定定位 */
        bottom: 10px; /* 距离窗口底部的距离为0 */
        right: 10px; /* 距离窗口右侧的距离为0 */
        z-index: 999;
        /* background-color: lightblue;
      padding: 10px; */
    }
    .themask {
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(221, 221, 221, 0.7);
    }
</style>
