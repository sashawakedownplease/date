```html
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Вопрос ❤️</title>

<style>

body{
    margin:0;
    height:100vh;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ff9a9e,#fad0c4);
    font-family:Arial;
    text-align:center;
    overflow:hidden;
}

h1{
    font-size:38px;
}

img{
    width:280px;
    border-radius:20px;
    margin:20px;
}

.buttons{
    position:relative;
}

button{
    font-size:20px;
    padding:14px 28px;
    margin:10px;
    border:none;
    border-radius:12px;
    cursor:pointer;
    transition:0.3s;
}

#yes{
    background:#ff3b6b;
    color:white;
}

#no{
    background:#eeeeee;
    position:absolute;
}

.big{
    transform:scale(1.4);
}

.heart{
    position:fixed;
    bottom:-10px;
    font-size:24px;
    animation:float 4s linear infinite;
}

@keyframes float{
    0%{transform:translateY(0);}
    100%{transform:translateY(-100vh);}
}

</style>
</head>

<body>

<h1 id="question">Пойдешь со мной на свидание? ❤️</h1>

<img src="https://i.imgur.com/8Km9tLL.png">

<div class="buttons">
<button id="yes">Да</button>
<button id="no">Нет</button>
</div>

<script>

let stage = 0
let yesSize = 1

const questions = [
"Точно нет? 🥺",
"Может всё-таки да? 😅",
"Я обещаю классное свидание 😌",
"Последний шанс 😏"
]

const yes = document.getElementById("yes")
const no = document.getElementById("no")
const question = document.getElementById("question")

yes.onclick = () => {

question.innerText = "Урааа! Тогда скоро увидимся ❤️"

no.style.display = "none"
yes.style.transform = "scale(2)"

createHearts()

}

no.onmouseover = () => {

stage++

if(stage <= questions.length){
question.innerText = questions[stage-1]
}

yesSize += 0.3
yes.style.transform = "scale(" + yesSize + ")"

const x = Math.random()*300 - 150
const y = Math.random()*200 - 100

no.style.transform = `translate(${x}px,${y}px)`

}

function createHearts(){

setInterval(() => {

const heart = document.createElement("div")
heart.className = "heart"
heart.innerHTML = "❤️"

heart.style.left = Math.random()*100 + "vw"

document.body.appendChild(heart)

setTimeout(()=>heart.remove(),4000)

},200)

}

</script>

</body>
</html>
```
