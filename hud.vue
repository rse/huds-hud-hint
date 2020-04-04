<!--
/*
**  HUDS ~~ Head-Up-Display Server (HUDS)
**  Copyright (c) 2020 Dr. Ralf S. Engelschall <rse@engelschall.com>
**
**  Permission is hereby granted, free of charge, to any person obtaining
**  a copy of this software and associated documentation files (the
**  "Software"), to deal in the Software without restriction, including
**  without limitation the rights to use, copy, modify, merge, publish,
**  distribute, sublicense, and/or sell copies of the Software, and to
**  permit persons to whom the Software is furnished to do so, subject to
**  the following conditions:
**
**  The above copyright notice and this permission notice shall be included
**  in all copies or substantial portions of the Software.
**
**  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
**  EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
**  MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
**  IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
**  CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
**  TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
**  SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
*/
-->

<template>
    <div v-bind:style="style" class="hud">
        <hint ref="hint" class="hint"
            v-bind:opacity="config.hint.opacity"
            v-bind:background="config.hint.background"
            v-bind:iconname="config.hint.iconname"
            v-bind:iconcolor="config.hint.iconcolor"
            v-bind:hintcolor="config.hint.hintcolor"
            v-bind:hinttext="config.hint.hinttext"
        ></hint>
    </div>
</template>

<style lang="less" scoped>
body {
    background-color: var(--background);
}
.hud {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    .hint {
        flex-basis: auto;
    }
}
</style>

<script>
module.exports = {
    name: "hud",
    data: () => ({
        config: huds.config()
    }),
    computed: {
        style: () => {
            return {
                background: huds.options.debug ? "#999999" : "transparent"
            }
        }
    },
    components: {
        "hint": "url:hud-widget-hint.vue"
    }
}
</script>

