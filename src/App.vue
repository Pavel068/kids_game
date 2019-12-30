<template>
    <div v-if="currentPicture" class="wrapper" :style="picBackgroundImage">
        <div class="item-liter">{{currentPicture.liter}}</div>
        <div class="item-text">{{currentPicture.text}}</div>
    </div>
</template>

<script>
    export default {
        name: 'app',
        data() {
            return {
                currentPicture: null,
                pictures: [
                    {
                        liter: 'А',
                        text: 'Арбуз',
                        image: 'images/watermelon.jpg'
                    },
                    {
                        liter: 'Б',
                        text: 'Банан',
                        image: 'images/banana.jpg'
                    },
                    {
                        liter: 'В',
                        text: 'Волк',
                        image: 'images/wolf.jpeg'
                    },
                    {
                        liter: 'Г',
                        text: 'Гуси',
                        image: 'images/gooses.jpg'
                    },
                    {
                        liter: 'Д',
                        text: 'Дом',
                        image: 'images/house.jpg'
                    },
                    {
                        liter: 'Е',
                        text: 'Енот',
                        image: 'images/racoon.jpeg'
                    },
                    {
                        liter: 'Ё',
                        text: 'Ёлка',
                        image: 'images/spruce.jpg'
                    },
                    {
                        liter: 'Ж',
                        text: 'Жираф',
                        image: 'images/giraffe.jpg'
                    },
                    {
                        liter: 'З',
                        text: 'Заяц',
                        image: 'images/hare.jpg'
                    },
                    {
                        liter: 'И',
                        text: 'Игра',
                        image: 'images/game.jpg'
                    },
                    {
                        liter: 'Й',
                        text: 'Йогурт',
                        image: 'images/yogurt.jpeg'
                    },
                    {
                        liter: 'К',
                        text: 'Кошка',
                        image: 'images/cat.jpg'
                    },
                    {
                        liter: 'Л',
                        text: 'Лампа',
                        image: 'images/lamp.jpeg'
                    },
                    {
                        liter: 'М',
                        text: 'Мина',
                        image: 'images/mine.jpeg'
                    },
                    {
                        liter: 'Н',
                        text: 'Нос',
                        image: 'images/nose.jpeg'
                    },
                    {
                        liter: 'О',
                        text: 'Огурец',
                        image: 'images/cucumber.jpg'
                    },
                    {
                        liter: 'П',
                        text: 'Поросёнок',
                        image: 'images/pig.jpg'
                    },
                    {
                        liter: 'Р',
                        text: 'Радуга',
                        image: 'images/rainbow.jpg'
                    },
                    {
                        liter: 'С',
                        text: 'Соска',
                        image: 'images/nipple.jpg'
                    },
                    {
                        liter: 'Т',
                        text: 'Трактор',
                        image: 'images/tractor.jpg'
                    },
                    {
                        liter: 'У',
                        text: 'Утка',
                        image: 'images/duck.jpeg'
                    },
                    {
                        liter: 'Ф',
                        text: 'Фея',
                        image: 'images/fairy.jpg'
                    },
                    {
                        liter: 'Х',
                        text: 'Хрен',
                        image: 'images/horseradish.jpg'
                    },
                    {
                        liter: 'Ц',
                        text: 'Цветок',
                        image: 'flower.jpeg'
                    },
                    {
                        liter: 'Ч',
                        text: 'Чебурашка',
                        image: 'images/cheburashka.jpg'
                    },
                    {
                        liter: 'Ш',
                        text: 'Шл*ха',
                        image: 'images/whore.jpg'
                    },
                    {
                        liter: 'Щ',
                        text: 'Щука',
                        image: 'images/pike.jpg'
                    },
                    {
                        liter: 'Ъ',
                        text: 'Уъу',
                        image: 'images/uuu.jpg'
                    },
                    {
                        liter: 'Ы',
                        text: 'Ы',
                        image: 'images/uuu.jpg'
                    },
                    {
                        liter: 'Ь',
                        text: 'Ь',
                        image: 'images/uuu.jpg'
                    },
                    {
                        liter: 'Э',
                        text: 'Экскаватор',
                        image: 'images/excavator.jpg'
                    },
                    {
                        liter: 'Ю',
                        text: 'Юпитер',
                        image: 'images/jupiter.jpg'
                    },
                    {
                        liter: 'Я',
                        text: 'Ягуар',
                        image: 'images/jaguar.jpg'
                    }
                ]
            }
        },
        computed: {
            picBackgroundImage() {
                return `background-image: url('${this.currentPicture.image}')`
            }
        },
        methods: {
            randomInt(min, max) {
                let rand = min - 0.5 + Math.random() * (max - min + 1);
                return Math.round(rand);
            },
            getRussianSymbol(charCode) {
                let chars = 'АБВГДЕЁЖЗИЙКЛМНОПРСТУФХЦЧШЩЪЫЬЭЮЯ'.split('');
                let codes = [70, 188, 68, 85, 76, 84, 192, 186, 80, 66, 81, 82, 75, 86, 89, 74, 71, 72, 67, 78, 69, 65, 219, 87, 88, 73, 79, 221, 83, 87, 222, 190, 90];

                return codes.indexOf(charCode) !== -1 ? chars[codes.indexOf(charCode)] : chars[0];
            }
        },
        mounted() {
            this.currentPicture = this.pictures[this.randomInt(0, this.pictures.length - 1)];
            document.addEventListener('keydown', event => {
                this.pictures.forEach(picture => {
                    if (picture.liter === this.getRussianSymbol(event.which))
                        this.currentPicture = picture;
                });
                console.log(event.which);
            });
        }
    }
</script>

<style>
    .wrapper {
        position: relative;
        width: 100%;
        height: 100vh;
        font-size: 100px;
        background-size: cover;
        background-repeat: no-repeat;
        color: #ae1939;
    }

    .item-liter {
        position: absolute;
        top: 0;
        width: 100%;
        background-color: rgba(0, 0, 0, 0.7);
    }

    .item-text {
        position: absolute;
        bottom: 0;
        width: 100%;
        background-color: rgba(0, 0, 0, 0.7);
        text-align: center;
    }
</style>
