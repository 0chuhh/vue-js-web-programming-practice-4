<template>
<background>
    <leafs
        :class="`leafs${index+1}`"
        v-for="(imageL, index) in leafsImgs"
        :key="index"
        :src="imageL"></leafs>
    
    <main-content>
        <my-nav
        ></my-nav>
        <middle-content>
            <text
                v-for="(text, index) in texts[textNumber]"
                :key="index"
            >
            {{text}}
            </text>
            <my-button
                @nextQuestion="next"
                :isActive="isActive"
            ></my-button>
        </middle-content>
        <div class="images">
            <images
                v-for="(image, index) in questions[currentQuestion].images"
                :key="index"
                :id="index"
                :src="image"
                @click="answer"
            />
        </div>
    </main-content>
</background>


</template>

<script>
    import MainContent from '@/components/MainContent.vue'
    import background from '@/components/Background.vue'
    import leafs from '@/components/leafs.vue'
    import MiddleContent from '@/components/MiddleContent.vue'
    import Text from '@/components/Text.vue'
    import Images from './components/Images.vue'
    import MyButton from '@/components/MyButton.vue'
    import MyNav from '@/components/MyNav.vue'
    export default {
        components: {background, MainContent,MiddleContent, Text, Images, MyButton, MyNav, leafs },
        data(){
            return{
                leafsImgs: ['./../assets/imgs/leafs1.png', './../assets/imgs/leafs2.png'],
                isActive: false,
                canClick: true,
                result: 100,
                currentQuestion: 0,
                textNumber: 0,
                texts: [
                    {
                        text: 'Начинаем с простенького. Судя по мультфильму, Чебурашка и Гена много гуляли и ходили пешком. А вот если бы они устали, то могли бы спокойно воспользоваться любым другим способом передвижения, кроме одного. Какого?'
                    },
                    {
                        text: 'Ну конечно! Это было просто. На осле из "Бременских музыкантов" могли кататься только бременские музыканты. Увы!'
                    },
                    {
                        text: 'Кто из них настоящий буратино???'
                    },
                    {
                        text: 'Молодец! Ты распознал настоящего среди этих клонов!'
                    },
                    {
                        text: 'Кто из них Сказал фразу "Бесконечность не предел!"'
                    },
                    {
                        text: 'Это был трудный выбор, но ты справился!'
                    },
                    {
                        text: 'А сейчас самый сложный вопрос!!! Кого из них зовут Фредди?'
                    },
                    {
                        text: 'Да, это было легко. Тут всех зовут Фредди'
                    },
                    {
                        text: 'Кто НЕ является противником Человека-Паука?'
                    },
                    {
                        text: 'Это была бы великая битва, но увы!'
                    },
                    {
                        text: ''
                    }
                ],
                questions: [
                    {
                        images: ['./../assets/imgs/var1-1.jpg','./../assets/imgs/var1-2.jpg', './../assets/imgs/var1-3.jpg', './../assets/imgs/var1-4.jpg' ]
                    },
                    {
                        images: ['./../assets/imgs/var2-1.jpg','./../assets/imgs/var2-2.jpg', './../assets/imgs/var2-3.jpg', './../assets/imgs/var2-4.jpg' ]
                    },
                    {
                        images: ['./../assets/imgs/var3-1.jpg','./../assets/imgs/var3-2.jpg', './../assets/imgs/var3-3.jpg', './../assets/imgs/var3-4.jpg' ]
                    },
                    {
                        images: ['./../assets/imgs/var4-1.jpg','./../assets/imgs/var4-2.jpg', './../assets/imgs/var4-3.jpg', './../assets/imgs/var4-4.jpg' ]
                    },
                    {
                        images: ['./../assets/imgs/var5-1.jpg','./../assets/imgs/var5-2.jpg', './../assets/imgs/var5-3.jpg', './../assets/imgs/var5-4.jpg' ]
                    },
                    {
                        images: ['','', '', '' ]
                    },
                   
                ]
            }
        },
        methods:{
            answer(e){
                const images = document.querySelectorAll('.image')
                function trueAnswer(element){
                    images.forEach(elem => {
                        elem.style.pointerEvents = 'none'
                    })
                    element.target.parentNode.classList.add('image__success')
                }
                function falseAnswer(element, trueAnswer){
                    element.target.parentNode.classList.add('image__failure')
                    for (var image of images){
                        image.style.pointerEvents = 'none'
                        if (image.id == trueAnswer){
                            image.classList.add('image__success')
                        }   
                    }
                }

                if (this.canClick){
                    if (this.currentQuestion==0 && e.target.parentNode.id == 3){
                    trueAnswer(e)
                    this.canClick = false
                    this.textNumber += 1
                    }else if(this.currentQuestion == 0 && e.target.parentNode.id != 3){
                        falseAnswer(e, 3)
                        this.texts[1].text = 'Не правильно!'
                        this.result -= 25
                        this.canClick = false
                        this.textNumber += 1

                    }else if(this.currentQuestion == 1 && e.target.parentNode.id == 2){
                        trueAnswer(e)
                        this.textNumber += 1
                        this.canClick = false
                    }else if(this.currentQuestion == 1 && e.target.parentNode.id != 2){
                        falseAnswer(e, 2)
                        this.texts[3].text = 'Может быть в следующий раз повезёт...'
                        this.result -= 25
                        this.canClick = false
                        this.textNumber += 1
                    }else if(this.currentQuestion == 2 && e.target.parentNode.id == 0){
                        this.canClick = false
                        trueAnswer(e)
                        this.textNumber += 1
                    }else if(this.currentQuestion == 2 && e.target.parentNode.id != 0){
                        falseAnswer(e, 0)
                        this.texts[5].text = 'Неа'
                        this.result -= 25
                        this.canClick = false
                        this.textNumber += 1
                    }else if(this.currentQuestion == 4 && e.target.parentNode.id == 2){
                        trueAnswer(e)
                        this.canClick = false
                        this.textNumber += 1
                    }else if(this.currentQuestion == 4 && e.target.parentNode.id != 2){
                        falseAnswer(e, 2)
                        this.texts[9].text = 'Как бы не так!'
                        this.result -= 25
                        this.canClick = false
                        this.textNumber += 1
                    }else if(this.currentQuestion == 3 && (e.target.parentNode.id == 0 || e.target.parentNode.id == 1 || e.target.parentNode.id == 2 || e.target.parentNode.id == 3)){
                        images.forEach(elem => {
                            elem.classList.add('image__success')
                        })
                        this.canClick = false
                        this.textNumber += 1
                    }
                    this.isActive = true

                }
                        
                
            },
            next(e){

                this.textNumber += 1
                const images = document.querySelectorAll('.image')
                const links = document.querySelectorAll('.link')
                images.forEach(el => {
                    el.classList.remove('image__success');
                    el.classList.remove('image__failure');
                });
                this.isActive = false;
                this.currentQuestion += 1;
                for (let i = 0; i <= this.currentQuestion; i++){

                    links[i].classList.add('link__active')
                }
                this.canClick = true
                images.forEach(elem => {
                        elem.style.pointerEvents = ''
                    })
                this.texts[10].text = `Твой результат равен: ${this.result} %`
                console.log(this.leafsImgs)
            },
             
        }
    }
// import var1 from '../public/assets/var1-1.jpg'
</script>

<style scoped>


</style>