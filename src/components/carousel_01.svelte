<script>
    import { onMount } from 'svelte'
    onMount(async () => {
        const elts = {
            text1: document.getElementById('text1'),
            text2: document.getElementById('text2'),
        }

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

        const morphTime = 1
        const cooldownTime = 0.5

        let textIndex = texts.length - 1
        let time = new Date()
        let morph = 0
        let cooldown = cooldownTime

        elts.text1.textContent = texts[textIndex % texts.length]
        elts.text2.textContent = texts[(textIndex + 1) % texts.length]

        function doMorph() {
            morph -= cooldown
            cooldown = 0

            let fraction = morph / morphTime

            if (fraction > 1) {
                cooldown = cooldownTime
                fraction = 1
            }

            setMorph(fraction)
        }

        function setMorph(fraction) {
            elts.text2.style.filter = `blur(${Math.min(
                8 / fraction - 8,
                100
            )}px)`
            elts.text2.style.opacity = `${Math.pow(fraction, 0.4) * 100}%`

            fraction = 1 - fraction
            elts.text1.style.filter = `blur(${Math.min(
                8 / fraction - 8,
                100
            )}px)`
            elts.text1.style.opacity = `${Math.pow(fraction, 0.4) * 100}%`

            elts.text1.textContent = texts[textIndex % texts.length]
            elts.text2.textContent = texts[(textIndex + 1) % texts.length]
        }

        function doCooldown() {
            morph = 0

            elts.text2.style.filter = ''
            elts.text2.style.opacity = '100%'

            elts.text1.style.filter = ''
            elts.text1.style.opacity = '0%'
        }

        function animate() {
            requestAnimationFrame(animate)

            let newTime = new Date()
            let shouldIncrementIndex = cooldown > 0
            let dt = (newTime - time) / 1000
            time = newTime

            cooldown -= dt

            if (cooldown <= 0) {
                if (shouldIncrementIndex) {
                    textIndex++
                }

                doMorph()
            } else {
                doCooldown()
            }
        }

        animate()
    })
</script>

<div>
    <div id="container">
        <span id="text1" />
        <span id="text2" />
    </div>

    <svg id="filters">
        <defs>
            <filter id="threshold">
                <feColorMatrix
                    in="SourceGraphic"
                    type="matrix"
                    values="1 0 0 0 0
									0 1 0 0 0
									0 0 1 0 0
									0 0 0 255 -140"
                />
            </filter>
        </defs>
    </svg>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Ma+Shan+Zheng&display=swap');

    #container {
        position: absolute;
        /* margin: auto; */
        width: 100vw;
        height: 80pt;
        top: 50%; /* 相对于父组件的顶部偏移为50% */
        /* left: 50%; */

        filter: url(#threshold) blur(0.6px);
    }

    #text1,
    #text2 {
        position: absolute;
        width: 100%;
        display: inline-block;

        font-family: 'Ma Shan Zheng', cursive;
        font-size: 80pt;

        text-align: center;

        user-select: none;
    }
</style>
