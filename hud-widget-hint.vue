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
    <div v-bind:style="style" class="hint">
        <div class="banner">
            <div class="icon">
                <i v-bind:class="[ 'fa', 'fa-' + iconname ]"></i>
            </div>
            <div class="text" v-html="hinttext">
            </div>
        </div>
    </div>
</template>

<style lang="less" scoped>
.hint {
    opacity: var(--opacity);
    .banner {
        display: flex;
        flex-direction: row;
        align-items: top;
        background-color: var(--background);
        padding: 50px 200px 50px 200px;
        font-size: 20pt;
        font-family: "TypoPro Fira Sans";
        .icon {
            perspective: 200px;
            width: 400px;
            transform-origin: 50% 50%;
            transform-style:  preserve-3d;
            color: var(--iconcolor);
            font-size: 400px;
        }
        .text {
            padding-left: 80px;
            width: auto;
            color: var(--hintcolor);
            kbd {
                border: 1px solid var(--hintcolor);
                border-radius: 4px;
                padding: 0 5px 0 5px;
            }
        }
    }
}
</style>

<script>
module.exports = {
    name: "hint",
    props: {
        opacity:    { type: Number, default: 1.0 },
        background: { type: String, default: "" },
        iconname:   { type: String, default: "" },
        iconcolor:  { type: String, default: "" },
        hintcolor:  { type: String, default: "" },
        hinttext:   { type: String, default: "" }
    },
    computed: {
        style: HUDS.vueprop2cssvar()
    },
    mounted () {
        setInterval(() => {
            anime({
                targets:  this.$el.querySelector(".icon"),
                duration: 3000,
                easing:   "easeInOutQuad",
                rotateY:  [ 0, 360 ],
            })
        }, 4000)
    }
}
</script>

