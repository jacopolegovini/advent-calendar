<script>
export default {
    data() {
        return {
            source: [
                {
                    "type": "image",
                    "icon": "ico-neve",
                    "url": "images/gremlins.gif"
                },
                {
                    "type": "image",
                    "icon": "ico-albero",
                    "url": "images/friends.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-fiocco",
                    "text": "Se fossi nato fra il 1647 al 1660 non avresti potuto festeggiare il Natale! In quegli anni fu bandito e cambiato in un giorno di digiuno."
                },
                {
                    "type": "image",
                    "icon": "ico-stella",
                    "url": "images/homealone.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-omino",
                    "text": "La stella di Natale sembra una pianta tipicamente invernale, invece nasce come cespuglio nel caldo del Messico ed era conosciuta fin dai tempi degli Aztechi"
                },
                {
                    "type": "image",
                    "icon": "ico-stella",
                    "url": "images/griffin.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-pupazzo",
                    "text": "Babbo Natale non ha sempre indossato abiti rossi!Lo sapevi che anni fa indossava il verde?"
                },
                {
                    "type": "text",
                    "icon": "ico-caramella",
                    "text": "Jingle Bells, Jingle Bells: non mentire, l’hai letta cantando. Sapevi che la canzone più famosa del natale è anche stata la prima cantata nello spazio?"
                },
                {
                    "type": "image",
                    "icon": "ico-calza",
                    "url": "images/skeleton.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-pupazzo",
                    "text": "Natale a Luglio? A Cuba è stato così per quasi 30 anni, fra il 1968 e il 1997: i festeggiamenti avvenivano in piena estate"
                },
                {
                    "type": "text",
                    "icon": "ico-fiocco",
                    "text": "Oltre a Pasqua, anche Natale ha la sua isola: è Christmas Island nell’Oceano Indiano, scoperta il 25 dicembre 1643."
                },
                {
                    "type": "text",
                    "icon": "ico-fiocco",
                    "text": "Anche Babbo Natale cede al lato oscuro della Forza. Il suo alter ego è Krampus, un demone che va alla ricerca di bambini cattivi."
                },
                {
                    "type": "text",
                    "icon": "ico-calza",
                    "text": "Pensi di essere un campione seriale di regali? Beh, i francesi hanno regalato agli americani la Statua della Libertà in segno di amicizia nel Natale del 1883"
                },
                {
                    "type": "image",
                    "icon": "ico-stella",
                    "url": "images/nightmare.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-stella",
                    "text": "In Svezia c’è una versione local di Babbo Natale: si chiama Tomte, è basso come un folletto e gira accompagnato da Yule, la sua capra"
                },
                {
                    "type": "image",
                    "icon": "ico-calza",
                    "url": "images/grinch.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-caramella",
                    "text": "Anche tu addobbi l’albero solo da un lato?Chissà se lo fecero anche gli antichi Egizi quando nel loro equivalente del Natale addobbavano le Piramidi"
                },
                {
                    "type": "text",
                    "icon": "ico-omino",
                    "text": "In Giappone il Natale è festeggiato come una sorta di San Valentino durante il quale solo le coppie si scambiano i doni"
                },
                {
                    "type": "text",
                    "icon": "ico-caramella",
                    "text": "È tempo di panettone, ma da dove viene questo nome? È quello di un dolce, il Pan di Toni inventato dall’aiuto cuoco della famiglia Sforza"
                },
                {
                    "type": "text",
                    "icon": "ico-calza",
                    "text": "Ma Babbo Natale abita in Puglia? Il nostro barbuto personaggio si ispira a San Nicola di Myra, un vescovo le cui spoglie sono custodite a Bari"
                },
                {
                    "type": "image",
                    "icon": "ico-caramella",
                    "url": "images/poltrona.gif"
                },
                {
                    "type": "image",
                    "icon": "ico-caramella",
                    "url": "images/spongebob.gif"
                },
                {
                    "type": "image",
                    "icon": "ico-neve",
                    "url": "images/elf.gif"
                },
                {
                    "type": "text",
                    "icon": "ico-neve",
                    "text": "Se pensi di non aver fritto abbastanza durante le scorse festività, ti sproniamo dicendo che in Polonia il pranzo natalizio è di 12 portate, una per ogni apostolo "
                },
                {
                    "type": "image",
                    "icon": "ico-caramella",
                    "url": "images/dance.gif"
                }
            ],

            clicked: false,
            iconNumber: null,
            cardsClicked: Array(25).fill(false)
        }
    },
    methods: {
        getImagePath(imgPath) {
            return new URL(imgPath, import.meta.url).href;
        },

        getRandomImage(source) {
            let randomNumber = Math.floor(Math.random() * source.length);
            return source[randomNumber].icon;
        },

        openIcon(index) {
            this.clicked = !this.clicked;
            this.iconNumber = index;
            this.cardsClicked[index] = true;
        }
    },

    computed: {

    }
}
</script>

<template>
    <div class="page">
        <div class="advent-calendar container" :class="clicked ? 'advent-calendar-close' : ''">
            <header class="img-container">
                <img src="../../images/header-bg.png" alt="header">
            </header>
            <main class="icons-container">
                <ul class="icons">
                    <li v-for="(icon, index) in 25" :key="index" @click="openIcon(index)">
                        <div :class="cardsClicked[index] ? 'icon-clicked-visibility' : 'icon'">
                            <div class="icon-img">
                                <img :src="getImagePath(`/images/icons/${getRandomImage(source)}.png`)" alt="icon">
                            </div>
                            <div class="icon-text">{{ icon }}</div>
                        </div>
                    </li>
                </ul>
            </main>
        </div>
        <div class="advent-calendar-clicked-image-type">
            <div class="icon-clicked-gif" v-if="clicked && source[iconNumber].type === 'image'">
                <div class="icon-clicked-img">
                    <img :src="getImagePath(`../../public/${source[iconNumber].url}`)" alt="icon-gif">
                </div>
                <button class="btn btn-primary" @click="openIcon">Chiudi</button>
            </div>
        </div>
        <div class="advent-calendar-clicked-text-type" v-if="clicked && source[iconNumber].type === 'text'">
            <div class="icon-clicked-text">
                <div class="icon-clicked">
                    <p>{{ source[iconNumber].text }}</p>
                </div>
                <button class="btn btn-primary" @click="openIcon">Chiudi</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
/* General */
ul {
    padding: 0;
    margin: 0;
}

li {
    list-style-type: none;
    text-align: center;
}

li:last-child {
    width: 100%;
}

li:last-child * {
    width: 100%;
    background-color: #D4D6F5;
    color: #2E6754;
    border-radius: 10px;
}


/* General page */
.page {
    height: 100vh;
    overflow-y: hidden;
}

.advent-calendar {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

/* Header */
.img-container {
    height: 40%;
    display: flex;
    justify-content: center;
}

header img {
    background-color: #2D28EB;
    width: 1040px;
    object-fit: cover;
    object-position: 0 105px;
}

/* Main */
.img-container,
.icons-container {
    width: 1040px;
}

.icons-container {
    margin-top: 20px;
    height: 60%;
}

.icons {
    display: flex;
    justify-content: space-between;
    gap: 30px;
    row-gap: 20px;
    flex-wrap: wrap;
}

.icon {
    background-color: #2E6754;
    border-radius: 10px;
    width: 90px;
    height: 90px;
    color: white;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.icon:hover {
    cursor: pointer;
}

.icon-img img {
    width: 2rem;
}

.icon-text {
    font-size: 3rem;
    line-height: 50px;
}


/* Advent calendar clicked */
.advent-calendar-close {
    opacity: 0.5;
}

.advent-calendar-clicked-image-type {
    background-color: #E689B5;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 10px;
}

.icon-clicked-gif {
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: center;
    justify-content: center;
    padding: 20px 0;
}

.icon-clicked-img {
    display: flex;
    justify-content: center;
}

.advent-calendar-clicked-image-type img {
    width: 90%;
    object-fit: cover;
}

.advent-calendar-clicked-text-type {
    background-color: #E689B5;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 10px;
    padding: 20px 0px;
}

.icon-clicked-text {
    text-align: center;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: center;
    justify-content: center;
}

.icon-clicked-text p {
    padding: 0 20px;
    margin: 0;
}

.icon-clicked-visibility {
    opacity: 0.3;
    background-color: #100645;
    border-radius: 10px;
    width: 90px;
    height: 90px;
    color: white;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
</style>