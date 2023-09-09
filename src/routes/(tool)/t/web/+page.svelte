<script>
    // export let ocss = ''
    export let arr = []
    import VirtualList from '@sveltejs/svelte-virtual-list'

    function rs() {
        const greetings = [
            '您好啊,今天过得怎么样?',
            '祝您新年快乐,阖家幸福!',
            '我很高兴见到您,很荣幸认识您。',
            '天气不错啊,一起出去走走吧。',
            '早上好,一日之计在于晨。',
            '晚上好,夜深人静时祝您安睡。',
            '中午好,午休后继续加油。',
            '下午好,工作顺利吗,遇到任何问题都可以问我。',
            '您回来啦,欢迎欢迎!',
            '好久不见,想念您的笑容呢。',
        ]
        return greetings[Math.floor(Math.random() * 10)]
    }

    for (let i = 0; i < 2000; i++) {
        let num = i
        let name = '第' + i + '章: ' + rs()
        arr.push({
            name,
            num,
        })
    }
    console.log(arr)
</script>

<div class="drawer">
    <input id="my-drawer" type="checkbox" class="drawer-toggle" />
    <div class="drawer-content">
        <label for="my-drawer" class="btn btn-ghost drawer-button text-base-100"
            ><i class="gg-menu-left-alt" /></label
        >
    </div>
    <div class="drawer-side">
        <label for="my-drawer" class="drawer-overlay" />
        <!-- 使用插板，选项和动态class实现tab切换 -->
        <!-- svelte-ignore a11y-missing-attribute -->
        <div class="rounded-box h-screen">
            <div class="bg-neutral tabs sticky top-0" style="z-index: 9999;">
                <a class="tab tab-bordered tab-active">目录</a>
                <a class="tab tab-bordered">书签</a>
                <a class="tab tab-bordered">搜索</a>
            </div>
            <!-- 特判输出卷名 -->
            <div class="h-full menu menu-md bg-base-200 w-99">
                <VirtualList items={arr} let:item>
                    <!-- this will be rendered for each currently visible item -->
                    <li><a>{item.num}: {item.name}</a></li>
                </VirtualList>
            </div>
        </div>
    </div>
</div>


<div class="drawer">
    <input id="my-drawerd" type="checkbox" class="drawer-toggle" />
    <div class="drawer-content">
      <!-- Page content here -->
      <label for="my-drawerd" class="btn btn-primary drawer-button">Open drawer</label>
    </div> 
    <div class="drawer-side">
      <label for="my-drawerd" class="drawer-overlay"></label>
      <ul class="menu p-4 w-80 h-full bg-base-200 text-base-content">
        <!-- Sidebar content here -->
        <li><a>Sidebar Item 1</a></li>
        <li><a>Sidebar Item 2</a></li>
        
      </ul>
    </div>
  </div>