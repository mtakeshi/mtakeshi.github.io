---
layout: page
title: Tempo
description: Lembrete.
keywords: lembrete, tempo
---

<h4><span id="myClock" style="font-family:'Fira Mono',monospace;letter-spacing:2px;color:#FF4136;text-transform:uppercase"></span></h4>
<script>
var myClock = document.getElementById('myClock');
function renderTime () {
    var currentTime = new Date();
    var months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
    var mo = currentTime.getMonth();
  	var d = currentTime.getDate();
  	var y = currentTime.getFullYear();
    var h = currentTime.getHours();
    var m = currentTime.getMinutes();
    var s = currentTime.getSeconds();
    var ms = currentTime.getMilliseconds();
    if (h < 10) { h = "0" + h; }   
    if (m < 10) { m = "0" + m; }    
    if (s < 10) { s = "0" + s; }
    myClock.textContent = months[mo] + " " + d + ", " + y + " • " + h + ":" + m + ":" + s + ":" + ms;
    myClock.innerText = months[mo] + " " + d + ", " + y + " • " + h + ":" + m + ":" + s + ":" + ms;
}

setInterval(function(){
    renderTime();
}, 1);
</script>

Don't wait until Friday to begin your projects. Do it now.<br>
Keep studying and keep creating.<br>
Be humble and patient.<br>
It's what you do in the dark, that puts you in the light.

<small style="opacity:0.5">Este pequeno texto foi montado a partir de trechos de diversas fontes.</small>
