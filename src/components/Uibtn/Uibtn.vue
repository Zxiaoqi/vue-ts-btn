<template>
        <button class="ui-btn" @click="onClickBtn"
        :class="{
            'ui-btn-xlarge':xlarge,
            'ui-btn-large':large,
            'ui-btn-small':small,
            'ui-btn-xsmall':xsmall,
            'ui-btn-tile':tile,
            'ui-btn-rounded':rounded,
            'ui-btn-circle':circle,
            'ui-btn-disabled':disabled
        }" :style="`
            --color-tint:${TintColor}
        `">
            <slot>按钮</slot>
        </button>
</template>


<script lang="ts">

import { Component, Vue,Emit,Prop} from 'vue-property-decorator';

@Component({
    components: {

    },
})

export default class Uibtn extends Vue {
    //定义自定义属性
    @Prop(Boolean) private xlarge:boolean|undefined;
    @Prop(Boolean) private large:boolean|undefined;
    @Prop(Boolean) private small:boolean|undefined;
    @Prop(Boolean) private xsmall:boolean|undefined;
    @Prop(Boolean) private tile:boolean|undefined;
    @Prop(Boolean) private rounded:boolean|undefined;
    @Prop(Boolean) private circle:boolean|undefined;
    @Prop(Boolean) private disabled:boolean|undefined;
    @Prop(String) private color:string|undefined;


    //监听父组件的点击事件
    @Emit('click') private emitClickEvent(evnet:MouseEvent){}

    private get TintColor(){
        if(this.color){
            return this.color
        }else{
            return '#2d8cf0'
        }
    }
    private onClickBtn(event:MouseEvent){
        if(!this.disabled){
            this.emitClickEvent(event);
        }
    }
}

</script>
    
<style lang="stylus">
resize(minWidth,height,paddingLR,fontSize)
    min-width minWidth
    height height
    padding 0 paddingLR
    font-size fontSize
    &.ui-btn-rounded,&.ui-btn-circle
        border-radius (@height/2)
    &.ui-btn-circle
        width @height
        min-width 0
        padding 0
.ui-btn
    resize(64px,36px,16px,0.875rem)
    border 0 
    border-radius 4px
    box-shadow  0px 0px 3px 1px #6dbbf9
    background-color  var(--color-tint)
    cursor pointer
    user-select none
    outline none
    &:hover
        filter brightness(120%)
    &:active
        filter brightness(80%)
    &.ui-btn-xsmall
        resize(38px,22px,9px,0.625rem)
    &.ui-btn-small
        resize(52px,28px,13px,0.75rem)
    &.ui-btn-large
        resize(78px,38px,19px,0.875rem)
    &.ui-btn-xlarge
        resize(98px,46px,23px,1rem)
    &.ui-btn-tile
        border-radius 0
    &.ui-btn-disabled
        color #999
        background-color #ccc
        cursor no-drop
        box-shadow 0 0 3px 1px #999
</style>