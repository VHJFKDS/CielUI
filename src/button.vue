<template>
<div>
<button class="g-button" :class="{[`icon-${iconPosition}`]:true}">
    <svg v-if="icon" class="icon">
        <use :xlink:href="`#i-${icon}`"></use>
    </svg>
    <div class="content">
        <slot></slot>
    </div>
</button>

</div>
</template>

<script>
export default{
  props:['icon','iconPosition']
}
</script>
<style lang="scss" scoped>
 .g-button{
            height: var(--button-height);
            padding: 0 1em;
            font-size: var(--font-size);
            border-radius: var(--border-radius);
            border: 1px solid var(--border-color);
            background: var(--button-bg);
            display: inline-flex;
            justify-content: center;
            align-items: center;
            vertical-align: middle;//为了解决inline-flex引起的bug
        &:hover{
            border-color: var(--border-color-hover);
        }
        &:active{
            background-color: var(--button-active-bg);
        }
        &:focus{
            outline: none;
        }
        >.icon{order: 1;margin-right: .1em;margin-left: 0;}
        >.content{order: 2;}
        &.icon-right{
            >.content{order: 1;}
            >.icon{order: 2;margin-left: .1em;margin-right: 0;}
        }
 }
</style>