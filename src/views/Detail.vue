<template>
    <ion-card>
        <ion-card-header>
            <ion-card-label>
                {{ post.title }}
            </ion-card-label>
            
            <ion-card-content>
                <ion-img :src="image" alt=""></ion-img>
                <ion-button color="tertiary" extend="full" @click="$router.go(-1)">Back</ion-button>        
            </ion-card-content>    
        </ion-card-header>    
    </ion-card>   
</template>
<script>
export default {
    props: ['post'],
    data(){
        return{
            image : ''
        }
    },
    mounted(){
        this.image = this.post.preview.images[0].source.url.replace('&amp;','&')
    }    
}
</script>