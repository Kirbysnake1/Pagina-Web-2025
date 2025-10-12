<template lang="pug">
<section id="Footer">

div.main
div.footer
    div.bubbles
        - for (var i = 0; i < 128; i++) //Small numbers looks nice too
            div.bubble(style=`--size:${2+Math.random()*4}rem; --distance:${6+Math.random()*4}rem; --position:${-5+Math.random()*110}%; --time:${2+Math.random()*2}s; --delay:${-1*(2+Math.random()*2)}s;`)
    div.content
        div
            div
                b Mis medios de contacto <br> <br>
                b Hola, Gracias por leer esto! <br>
                a Actualmente busco trabajo como
                b QA Automatizador o
                b Junior Frontend Developer.<br>
                b Puedes escribirme a <br>
                a(href="mailto:andresfeliperamirezespinal@gmail.com" target="_blank") andresfeliperamirezespinal@gmail.com <br>
                b También por Whatsapp: <br>
                a(href="https://wa.me/573002393455" target="_blank") +57 3002393455
            div
                
                
        div
            a.image(href="https://www.linkedin.com/in/andres-ramirez-4a677023b/" target="_blank" style="background-image: url(\"https://s3-us-west-2.amazonaws.com/s.cdpn.io/199011/happy.svg\")")
        
svg(style="position:fixed; top:100vh")
    defs
        filter#blob
            feGaussianBlur(in="SourceGraphic" stdDeviation="10" result="blur")
            feColorMatrix(in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -9" result="blob")
            //feComposite(in="SourceGraphic" in2="blob" operator="atop") //After reviewing this after years I can't remember why I added this but it isn't necessary for the blob effect


</section>
</template>

<script>

import './Footer.css'
</script>