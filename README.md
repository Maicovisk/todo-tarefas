<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Akaya+Kanadaka&family=Oi&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Oi&display=swap" rel="stylesheet">
    <title>todo list</title>
    <style>

        html {
            -webkit-user-drag: none;
        }
        body {
            margin: 0px;
            background: #222;
            user-select: none;
        }
        header {
            height: 150px;
            background: rgb(5, 31, 39);
            color: white;
            font-family: Arial, Helvetica, sans-serif;
            display: flex;
            flex-direction: column;
        }


        a {
            color: white;
            margin-left: 5px;
            width: 100px;
        }

        .conta {
            background-repeat: no-repeat;
            width: 50px;
            height: 50px;
            margin: 0px 0px 0px 20px;
            cursor: pointer;
            background-image: url('https://www.devmedia.com.br/join/images/user.svg');
        }

        header h1 {
            margin: 0px;
            text-align: center;
            position: relative;
            top: 40px;
        }

        .todo{
            max-width: 900px;
            margin: auto;
        }

        
        .todoScreen {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
        }

        .td{
            width: 250px;
            background: #16161b;
            min-height: 300px;
            margin: 5px;
            box-shadow: 2px 5px 13px;
            border: 1px solid rgba(255, 255, 255, 0.075);
            border-radius: 3px;
            flex-shrink: 0;
        }

        .todoArg {
            width: 93%;
            background: rgb(14, 41, 40);
            height: 90px;
            border-radius: 2px;
            box-shadow: 2px 1px 13px 1px;
            margin: -15px auto;
            padding: 4px;
            overflow-y: hidden;
            cursor: pointer;
            margin-bottom: 10px;
            overflow: auto;
        }

        .todoArgNot {
            width: 93%;
            background: rgb(14, 41, 40);
            height: 90px;
            border-radius: 2px;
            box-shadow: 2px 1px 13px 1px;
            margin: -15px auto;
            padding: 4px;
            overflow-y: hidden;
            cursor: pointer;
            margin-bottom: 10px;
            overflow: auto;
        }

        .todoArgNot::-webkit-scrollbar {
            width: 2px;
            
        }

        .todoArgNot::-webkit-scrollbar-track {
           background: rgba(34, 34, 34, 0.548);
           border-radius: 5px;
        }

        .todoArgNot::-webkit-scrollbar-thumb {
           background: rgba(16, 255, 175, 0.315);
           border-radius: 100%;
        }



        .todoArg:hover {
            height: auto;
            transform: scale(1.01);
        }

        .todoArg:hover textarea {
            height: 55px;
        }

        .todoArg::-webkit-scrollbar {
            width: 2px;
            
        }

        .todoArg::-webkit-scrollbar-track {
           background: rgba(34, 34, 34, 0.548);
           border-radius: 5px;
        }

        .todoArg::-webkit-scrollbar-thumb {
           background: rgba(16, 255, 175, 0.315);
           border-radius: 100%;
        }


        .text {
            color: white;
            font-family: Arial, Helvetica, sans-serif;
            font-size: 15px;
            outline: none;
            margin-top: 2px;
            border: 3px solid transparent;
            border-bottom: 3px solid black;
            padding: 4px;
            border-radius: 4px;
            text-align: center;
            cursor: pointer;
        }

        .content {
            color: white;
            background: none;
            font-family: Arial, Helvetica, sans-serif;
            font-size: 15px;
            margin-top: 4px;
            padding-bottom: 0px;
            padding: 4px;
            cursor: text;
            resize: none;
            outline: none;
            width: 97%;
            border: 0px solid;
            cursor: pointer;
        }

        
        .content::-webkit-scrollbar {
            width: 3px;
            z-index: 100;
            
        }

        .content::-webkit-scrollbar-track {
           background: rgba(128, 128, 128, 0.308);
           border-radius: 5px;
        }

        .content::-webkit-scrollbar-thumb {
           background: rgba(0, 0, 0, 0.651);
        }


        .pendentes .todoArg .status{
            width: 50px;
            height: 10px;
            background: rgba(255, 0, 0, 0.801);
            border-radius: 3px;
            box-shadow: 3px 3px 13px 1px rgba(2, 1, 1, 0.397);
        }

        .prontas .todoArg .status{
            width: 50px;
            height: 10px;
            background: rgb(32, 226, 14);
            border-radius: 3px;
            box-shadow: 3px 3px 13px 1px rgba(2, 1, 1, 0.397);
        }

        .depois .todoArg .status{
            width: 50px;
            height: 10px;
            background: rgb(241, 227, 32);
            border-radius: 3px;
            box-shadow: 3px 3px 13px 1px rgba(2, 1, 1, 0.397);
        }


        .titletd {
            color: goldenrod;
            font-family: 'Akaya Kanadaka', cursive;
            margin: 10px;
            padding-bottom: 6%;
            text-align: center;
            font-size: 22px;
        }

        .titletdconfig {
            color: red;
            font-family: 'Akaya Kanadaka', cursive;
            margin: 15px;
            padding-bottom: 0%;
            text-align: center;
            font-size: 22px;
        }

        .is {
            cursor: initial;
        }


        progress {
            width: 100%;
            border-radius: 1px;
            height: 20px;
            position: absolute;
            top: 127px;
        }

        .lixeira {
            position: fixed;
            top: 830px;
            right: 20px;
            user-select: none;
        }

        .lixeira .tampa {
            text-align: center;
            color: green;
            width: 50px;
            height: 15px;
            background-color: white;
            margin: 0px 0px 3px 0px;
            position: relative;
        }

        .lixeira .corpo {
            width: 50px;
            height: 60px;
            display: flex;
            justify-content: space-around;
            align-items: center;
            background-color: white;
        }

        .lixeira .corpo .pontos {
            height: 80%;
            width: 5px;
            background: black;
        }

        .open {
            transform: rotate(20deg);
            top: -5px;
            left: 4px;
        }


        .mais {
            width: 30px;
            height: 30px;
            cursor: pointer;
            position: relative;
            top: 8px;
            right: -50px;
        }

        .mais .x {
            width: 24px;
            background: white;
            height: 3px;
            position: relative;
            top: 14px;
        }

        
        .mais .y {
            height: 24px;
            background: white;
            width: 3px;
            position: relative;
            left: 10px;
        }

        .flexivel {
            display: flex;
            justify-content: center;
        }


        /* parte do painel de edição */

        section.painel {
            width: 300px;
            height: 100%;
            background: black;
            position: absolute;
            overflow-y: scroll;
            display: flex;
            justify-content: center;
            left: -300px;
            transition: left 200ms;
            flex-wrap: wrap;
            align-content: flex-start;
        }

        .painel .cpanel {
            margin: 0px;
            align-self: flex-start;
            width: 100%;
            margin: 10px 5px;
            color: white;
            font-size: 20px;
            font-family: Georgia, 'Times New Roman', Times, serif;
            text-align: center;
        }

        input {
            width: 180px;
            height: 12px;
            cursor: pointer;
        }

        .count {
            border-bottom: 2px solid white;
            height: 100px;
            width: 90%;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .close {
            width: 30px;
            height: 40px;
            position: absolute;
            left: 250px;
            cursor: pointer;
        } 

        .pinox {
            background: white;
            width: 100%;
            height: 5px;
            border-radius: 5px;
            margin: 6px auto;
            transform: rotate(50deg);
            position: relative;
            top: 11px;
        }
        .pinoy {
            transform: rotate(-50deg);
            background: white;
            width: 100%;
            height: 5px;
            border-radius: 5px;
        }

        .openPainel{
            position: absolute;
            top: 160px;
            left: 20px;
            width: 50px;
            height: 50px;
            background-position: center;
            background-repeat: no-repeat;
            background-size: 100%;
            cursor: pointer;
            z-index: 10;
            background-image: url('https://image.flaticon.com/icons/png/512/17/17146.png');
        }


        .openPainel:hover {
            animation: rot 4s linear infinite;
        }

        @keyframes rot {
            to {
                transform: rotate(360deg);
            }
        }

        .cabARG {
            display: flex;
            justify-content: space-around;
        }


        .edition {
            display: inline-block;
            width: 170px;
            text-align: right;
        }

        .edition button {
            outline: none;
            border: 0px solid white;
            cursor: pointer;
            border-radius: 100%;
            background: transparent;
            z-index: 1;
            margin: 0px;
            padding: 2px;
        }

        .activefix {
            background: rgba(207, 207, 207, 0.233);
            box-shadow: 1px 2px 10px 1px rgba(0, 0, 0, 0.438);
        }

        .edition button:hover {
            background: rgba(0, 0, 0, 0.233);
            box-shadow: 1px 2px 10px 1px rgba(0, 0, 0, 0.521);
        }

        .edition button:active {
            transform: scale(1.3);
        }

        .complete {
            display: flex;
            justify-content: space-around;
        }

        .complete input {
            position: relative;
            top: 4px;
            width: 50%;
        }


        .mask {
            position: absolute;
            width: 100%;
            background: rgba(0, 0, 0, 0.74);
            height: 100%;
        }

        .showMask {
            visibility: hidden;
        }

        font {
            display: flex;
            justify-content: space-around;
        }



        /* area do relogio */
        .time {

            top: 10px;
            left: 200px;
            width: 100px;
            background:none;
            display: flex;
            flex-direction: column;
            cursor: pointer;
            position: absolute;
        }

        .time .seta{
            width: 30px;
            height: 30px;
            position: relative;
            display: inline-block;
            background: black;
            top: 25px;
            z-index: 0;
            left: 35px;
            transform: rotate(47deg);
            overflow-y: hidden;
        }

        .time .timeArea{
            height: 20px;
            display: flex;
            background: black;
            justify-content: center;
            align-items: center;
            color: #ffff;
            z-index: 100;
        }

        .time button {
            outline: none;
            cursor: pointer;
            z-index: 1;
        }

        .time input {
            text-align: center;
            overflow-x: hidden;
            width: 96%;
            font-size: 15px;
            outline: none;
            padding: 0px;
            color: black;
        }



    </style>
</head>
<body>
    <header>
        <h1>todo list</h1>

        <a href="#" target="_blank" rel="noopener noreferrer">
            <div class="conta">
            </div>
            crie sua conta
        </a>
        <progress id="bar" value="0" min="0" max="100"></progress>
    </header>

    <div class="mask showMask" id="mask"></div>

    <main role="main" class="main">

        <section class="painel" id="painel">
            <div class="count">
                <a href="#" target="_blank" rel="noopener noreferrer">
                    <div class="conta">
                    </div>
                    crie sua conta
                </a>
            </div>
            <div class="close" id="closesetings">
                <div class="pinox"></div>
                <div class="pinoy"></div>
            </div>
            <div class="cpanel">
                <h3 class="titletdconfig">configuração {{card}}</h3>
                <div class="font">title: 
                    <input type="range" v-model:value="font" max="50" min="10"> {{ font }}
                </div>
                <div class="complete">
                    anabled: <input class="comp" v-model:checked='anable' type="checkbox">
                </div>
            </div>
        </section>
        
        <div class="todo">
            <div class="todoScreen">
                <div class="pendentes td" id="pendentes">
                    <div class="flexivel">

                        <h3 class="titletd">pendentes</h3>

                        <div class="mais" onclick="newtd()">
                            <div class="x"></div>
                            <div class="y"></div>
                        </div>

                    </div>
                    <div tabindex="0" class="todoArg" id='todoArg' draggable="true">
                        <div class="cabARG">
                            <div class="status"></div>
                            <div class="edition">
                                <button id="config" onclick="config()" class="config">&#128295;</button>
                                <button id='fixar' onclick="fixar()" class="fixar">&#128204;</button>
                                <button id='alarme' onclick="openAlarme()" class="alarme">&#x23F0;</button>
                            </div>
                        </div>
                        <div class="text" contenteditable="true">
                            titulo
                        </div>
                        <textarea class="content" cols="28" rows="2">atotações
                        </textarea>
                    </div>
                </div>

                <div class="depois td">
                    <h3 class="titletd">para depois</h3>
                    <div tabindex="0" class="todoArg" id="todoArg" draggable="true">
                        <div class="cabARG">
                            <div class="status"></div>
                            <div class="edition">
                                <button id="config" onclick="config()" class="config">&#128295;</button>
                                <button id='fixar' onclick="fixar()" class="fixar">&#128204;</button>
                            </div>
                        </div>
                        <div class="text" contenteditable="true">
                            titulo
                        </div>

                        <textarea class="content" name="" id="" cols="28" rows="2">atotações
                        </textarea>
                    </div>
                </div>

                <div class="prontas td" id="prontas">
                    <h3 class="titletd">prontas</h3>
                    <div tabindex="0" class="todoArg" id="todoArg" draggable="true">
                        <div class="cabARG">
                            <div class="status"></div>
                            <div class="edition">
                                <button id="config" onclick="config()" class="config">&#128295;</button>
                                <button id='fixar' onclick="fixar()" class="fixar">&#128204;</button>
                            </div>
                        </div>
                        <div class="text" contenteditable="true">
                            titulo
                        </div>
                        <textarea class="content">atotações
                        </textarea>
                    </div>
                </div>
                
            </div>
        </div>


        <div class="openPainel" id="openPainel"></div>
        <div class="lixeira" id="lixeira">
            <div class="tampa" id="tampa"><span style="text-align: center;">lixeira</span></div>
            <div class="corpo">
                <div class="pontos"></div>
                <div class="pontos"></div>
                <div class="pontos"></div>
            </div>
        </div>

        <div class="time">
            <div class="seta"></div>
            <div class="timeArea">
                00:00
            </div>
            <button>save</button>
        </div>
    </main>
</body>


<script>
    const app = new Vue({
        el: '.main',
        data: {
            font: 15,
            card: 'all',
            anable: true,
            now: '00:00'
        },
        watch: {
            font: function(){
                this.fontAT()
            },

            anable: function () {
                this.pointerEvents()
            }
        },
        
        methods:{
            pointerEvents: function () {
                var cards = document.querySelectorAll('#todoArg')
                if (this.anable == false){
                    for (c of cards){
                        c.classList.remove('todoArg')
                        c.classList.add('todoArgNot')
                    }
                }else {
                    for (c of cards){
                        c.classList.remove('todoArgNot')
                        c.classList.add('todoArg')
                    }
                }
            },
            fontAT: function(){
                var cards = document.querySelectorAll('.text')
                if (editable == 0){    
                    for (c of cards){
                        c.style.fontSize = this.font + 'px'
                    }
                }else {
                    editable.style.fontSize = this.font + 'px'
                }
            }
        },
        computed: {
        }
    })
</script>


<script>
    var ev
    var data

    var all = document.getElementsByClassName('td')
    var cards = document.getElementsByClassName('todoArg')


    /* parte do alarme */
    function openAlarme() {
        
    }


    var Mask = document.getElementById('mask')
    function maskAdd(){
        Mask.classList.remove('showMask')
    }

    function maskRemove() {
        Mask.classList.add('showMask')
    }

    /* parte da latra de lixo */
    var lixo = document.getElementById('lixeira')
    lixo.addEventListener('dragover', lixoOver)
    lixo.addEventListener('dragleave', lixoLeave)


    function corRange() {
        let a = Math.round(Math.random() * 255)
        let b = Math.round(Math.random() * 255)
        let c = Math.round(Math.random() * 255)
        return `rgb(${a},${b},${c})`
    }


    /* parte que mostra o menu de settings */
    var barsetings = document.querySelector('.openPainel')
    barsetings.addEventListener('click', openPainel)

    var painel = document.getElementById('painel')
    function openPainel() {
        if (editable == 0){
            app.card = 'all'
        }

        painel.style.left = '0px'
        document.body.style.overflow = 'hidden'
        maskAdd()
    }


    var closePainel = document.querySelector('.close')
    closePainel.addEventListener('click', closeP)
    function closeP() {
        document.body.style.overflow = 'auto'
        painel.style.left = '-300px'
        editable = 0
        maskRemove()
    }

    function newtd() {

        teste = `
        <div class="cabARG">
            <div class="status"></div>
            <div class="edition">
                <button id="config" class="config">&#128295;</button>
                <button id='fixar' onclick="fixar()" class="fixar">&#128204;</button>
            </div>
        </div>`


        var td = document.getElementById('pendentes')


        let textAREA = document.createElement('textarea')
        textAREA.className = 'content'
        textAREA.value = 'anotações'


        let text = document.createElement('div')
        text.className = 'text'
        text.contentEditable = 'true'
        text.innerText = 'titulo'


        let status = document.createElement('div')
        status.className = 'status'


        let bt1 = document.createElement('button')
        bt1.className = 'config'
        bt1.id = 'config'
        bt1.innerHTML = '&#128295;'
        bt1.addEventListener('click', config)


        let bt2 = document.createElement('button')
        bt2.className = 'fixar'
        bt2.id = 'fixar'
        bt2.innerHTML = '&#128204;' 
        bt2.addEventListener('click', fixar)     

        let edition = document.createElement('div')
        edition.className = 'edition'
        edition.appendChild(bt1)
        edition.appendChild(bt2)

        let cab = document.createElement('div')
        cab.className = 'cabARG'
        cab.appendChild(status)
        cab.appendChild(edition)


        let el = document.createElement('div')
        el.className = 'todoArg'
        el.id = 'todoArg'
        el.draggable = true

        el.addEventListener('dragstart', dragstart)
        el.addEventListener('dragend', dragend)
        el.tabIndex = 0

        el.style.background = corRange()

        el.appendChild(cab)
        el.appendChild(text)
        el.appendChild(textAREA)

        td.appendChild(el)

        /* metodos do app */
        //app.fontAT()
        app.pointerEvents()
    }



    /*parte da fixação */
    function fixar(){
        var path = event.path[3]
        path.draggable = false

        if (event.target.classList.value.indexOf('activefix') == -1){
            event.target.classList.add('activefix')
        }else {
            event.target.classList.remove('activefix')
            path.draggable = true
        }
    }


    /* parte de fonfiguração */
    var editable = 0
    function config(){
        var evt = event
        event.path[3].hidden = true

        setTimeout(() => {
            evt.path[3].hidden = false
        }, 50);

        editable = event.path[3].querySelector('.text')
        openPainel()
        let nb = Number(editable.style.fontSize.split('px')[0])
        app.font = nb != 0 ? nb : 15

        app.card = nb != 0 ? 'all' : editable.innerText

    }


    var elementSelect = false 
    function lixoOver() {
        var tampa = document.getElementById('tampa')
        tampa.classList.add('open')
        elementSelect = true
    }

    function lixoLeave() {
        var tampa = document.getElementById('tampa')
        tampa.classList.remove('open')
        setTimeout(() => {
            elementSelect = false
        }, 100);
    }


    for (c of cards){
        c.addEventListener('dragstart', dragstart)
        c.addEventListener('dragend', dragend)
        
    }

    function dragstart() {
        this.classList.add('is')
    }

    function dragend() {
        if (elementSelect){
            var obj = document.querySelector('.is')
            obj.remove()
        }
        this.classList.remove('is')
        elementSelect = false
    }


    for (c of all){
        c.addEventListener('dragover', dgleave)
        c.addEventListener('dragleave', dgldrop)
        
    }

    function dgleave() {

        var obj = document.querySelector('.is')
        this.appendChild(obj)
    }

    function dgldrop(){
        
    }

    var i = 0
    var pre
    function addBar(porcent) {
        porcent = Number.parseInt(porcent)+ 1
        if (porcent != pre){
            var inter = setInterval(() => {
                barProgress.value = i
                if (i >= porcent){
                    clearInterval(inter)
                    i = 0
                }
                i++
            }, 20);
        }
        pre = porcent
    }

    var barProgress = document.getElementById('bar') 
    var interFrame = setInterval(() => {
        var num = document.getElementsByClassName('prontas')[0].getElementsByClassName('todoArg').length
        if (num != 0){
            //barProgress.value = (num * 100) / cards.length
            addBar((num * 100) / cards.length)
        }else {
            barProgress.value = 0
            pre = 0
        }

    }, 100);
</script>
</html>
