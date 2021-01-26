<template>
    <div class="switch-wrapper">
        <label for="toggle">
            <input type="checkbox" id="toggle" />
            <span class="switcher"></span>
        </label>
    </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
$button-width: 500px;
$button-height: 295px;
$toggle-diameter: 255px;
$button-toggle-offset: ($button-height - $toggle-diameter) / 2; // 就是高度 对着呢
$toggle-shadow-offset: 10px; // 阴影半径
$toggle-wider: 333px;
$color-grey: #e9e9ea;
$color-dark-grey: #39393d;
$color-green: #30d158;
.switch-wrapper {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    input {
        display: none;
    }
    span {
        display: block;
        width: $button-width;
        height: $button-height;
        background-color: $color-grey;
        border-radius: $button-height/2;
        position: relative;
        transition: all 300ms ease;
        &:before {
            transition: ease all 300ms;
            content: '';
            position: absolute;
            display: inline-block;
            width: $toggle-diameter;
            height: $toggle-diameter;
            background-color: #fff;
            border-radius: $toggle-diameter/2;
            top: $button-toggle-offset;
            transform: translateX($button-toggle-offset);
            box-shadow: $toggle-shadow-offset 0 $toggle-shadow-offset * 4 rgba(0, 0, 0, 0.1);
        }
    }
    input:checked {
        & + span {
            background-color: $color-green;
        }
        & + span::before {
            transform: translateX($button-width - $button-toggle-offset - $toggle-diameter);
            box-shadow: $toggle-shadow-offset 0 $toggle-shadow-offset * -4 rgba(0, 0, 0, 0.1);
        }
        &:active + span::before {
            transform: translateX($button-width - $toggle-wider - $button-toggle-offset);
        }
    }
    input[type='checkbox']:active {
        & + span:before {
            width: $toggle-wider;
        }
    }
}
@media (prefers-color-scheme: dark) {
    .switch-wrapper {
        background-color: #1c1c1e;
    }
    span {
        background-color: $color-dark-grey;
    }
}
</style>
