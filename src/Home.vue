<template>
    <div class="root-home">
        <div class="btn-container">
            <Uibtn @click="onClick"
            :xlarge="xlarge"
            :large="large"
            :small="small"
            :xsmall="xsmall"
            :tile="tile"
            :rounded="rounded"
            :circle="circle"
            :disabled="disabled">
            an
            </Uibtn>
        </div>
        <div class="btn-grounp">
            <Uibtn class="btn" @click="resize('xsmall')">超小</Uibtn>
            <Uibtn class="btn" @click="resize('small')">小</Uibtn>
            <Uibtn class="btn" @click="resize('normal')">正常</Uibtn>
            <Uibtn class="btn" @click="resize('large')">大</Uibtn>
            <Uibtn class="btn" @click="resize('xlarge')">超大</Uibtn>
        </div>
        <div class="btn-grounp">
            <Uibtn class="btn" @click="changeRadius('tile')">矩形</Uibtn>
            <Uibtn class="btn" @click="changeRadius('normal')">正常</Uibtn>
            <Uibtn class="btn" @click="changeRadius('rounded')">椭圆</Uibtn>
            <Uibtn class="btn" @click="changeRadius('circle')">圆</Uibtn>
        </div>
        <div class="btn-grounp">
            <Uibtn class="btn" @click="changeDisabled">禁用</Uibtn>
        </div>
    </div>
</template>


<script lang="ts">

import { Component, Vue } from 'vue-property-decorator';
import Uibtn from '@/components/Uibtn/Uibtn.vue'

@Component({
    components: {
        Uibtn
    },
})

export default class Home extends Vue {

    private xsmall:boolean=false 
    private small:boolean=false 
    private large:boolean=false 
    private xlarge:boolean=false 
    private tile:boolean=false 
    private rounded:boolean=false 
    private circle:boolean=false 
    private disabled:boolean=false

    private changeDisabled() {
        this.disabled=!this.disabled
    }
    private changeRadius(name:String) {
        switch (name) {
            case 'tile':
                this.tile=true
                this.rounded=false
                this.circle=false
                break;
            case 'normal':
                this.tile=false
                this.rounded=false
                this.circle=false
                break;
            case 'rounded':
                this.tile=false
                this.rounded=true
                this.circle=false
                break;
            case 'circle':
                this.tile=false
                this.rounded=false
                this.circle=true
                break;
        }
    }
    private resize(name:String){
        switch (name) {
            case 'xsmall':
                this.xsmall=true
                this.small=false
                this.large=false
                this.xlarge=false
                break;
            case 'small':
                this.xsmall=false
                this.small=true
                this.large=false
                this.xlarge=false
                break;
            case 'normal':
                this.xsmall=false
                this.small=false
                this.large=false
                this.xlarge=false
                break;
            case 'large':
                this.xsmall=false
                this.small=false
                this.large=true
                this.xlarge=false
                break;
            case 'xlarge':
                this.xsmall=false
                this.small=false
                this.large=false
                this.xlarge=true
                break;
        }
    }

    private onClick(event:MouseEvent){
       console.log(event);
       
   }
}

</script>
    
<style lang="stylus">
.btn-container
    height 100px
.btn-group
    float left
.btn
    margin 5px
</style>