<script>
    import { onDestroy } from "svelte"
    import HappyText from "./happyText.svelte";
    const texts = [
        '令公桃李满天下，何用堂前更种花。',
        '鹤发银丝映日月，丹心热血沃新花。',
        '落红不是无情物，化作春泥更护花。',
        '采得百花成蜜后，为谁辛苦为谁甜？',
        '玉壶存冰心，朱笔写师魂。',
        '半亩方塘长流水，呕心沥血育新苗。',
        '师者，传道解惑，爱其生者。',
        '愿天下学子可以学其爱学之事，成其所望之才。',
        '节日快乐，身体健康',
    ]
    let currentIndex = 0
    function updateValue() {
        if (currentIndex < texts.length - 1) {
            currentIndex++
        } else {
            currentIndex = 0
        }
    }

    const interval = setInterval(updateValue, 3000) // 每隔1秒钟调用一次updateValue
    $: text = texts[currentIndex].split("");

    onDestroy(() => {
        clearInterval(interval) // 在组件销毁时清除定时器
    })
</script>

<div class="container"> 
    <HappyText items={text} ></HappyText>
</div>

<style>
    .container {
        position: absolute;
        /* margin: auto; */
        max-width: 1500px;
        height: 80pt;
        top: 30%; /* 相对于父组件的顶部偏移为50% */
        left: 10%;

        filter: url(#threshold) blur(0.6px);
    }
</style>
