```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ACCESS DENIED</title>
<style>
 @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@900&display=swap');

 * { margin: 0; padding: 0; box-sizing: border-box; }

 body {
   background: #000;
   min-height: 100vh;
   display: flex;
   align-items: center;
   justify-content: center;
   overflow: hidden;
   font-family: 'Share Tech Mono', monospace;
 }

 body::before {
   content: '';
   position: fixed;
   inset: 0;
   background: repeating-linear-gradient(
     0deg,
     transparent,
     transparent 2px,
     rgba(0,0,0,0.18) 2px,
     rgba(0,0,0,0.18) 4px
   );
   pointer-events: none;
   z-index: 100;
 }

 .scene {
   position: relative;
   width: 700px;
   max-width: 95vw;
   text-align: center;
 }

 .letter-wrap {
   position: relative;
   display: inline-block;
   margin-bottom: 36px;
 }

 .letter-bg {
   font-family: 'Orbitron', sans-serif;
   font-size: clamp(120px, 22vw, 200px);
   font-weight: 900;
   color: transparent;
   -webkit-text-stroke: 1px rgba(255,30,30,0.08);
   letter-spacing: -8px;
   line-height: 1;
   user-select: none;
   position: relative;
 }

 .letter-hidden {
   position: absolute;
   inset: 0;
   font-family: 'Orbitron', sans-serif;
   font-size: clamp(120px, 22vw, 200px);
   font-weight: 900;
   color: #ff1a1a;
   text-shadow:
     0 0 20px #ff1a1a,
     0 0 50px #ff000088,
     0 0 100px #ff000044;
   letter-spacing: -8px;
   line-height: 1;
   opacity: 0;
   transition: opacity 0.1s;
   clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
   animation: flicker-hidden 6s infinite;
 }

 .letter-wrap:hover .letter-hidden {
   opacity: 1;
   animation: reveal-glitch 0.4s steps(1) forwards, glitch-loop 2s infinite 0.4s;
 }

 @keyframes flicker-hidden {
   0%, 94%, 96%, 98%, 100% { opacity: 0; }
   95%, 97% { opacity: 0.15; }
 }

 @keyframes reveal-glitch {
   0%   { clip-path: inset(80% 0 0 0); transform: translateX(-4px); }
   25%  { clip-path: inset(40% 0 30% 0); transform: translateX(4px); }
   50%  { clip-path: inset(10% 0 60% 0); transform: translateX(-2px); }
   75%  { clip-path: inset(0 0 20% 0); transform: translateX(2px); }
   100% { clip-path: inset(0 0 0 0); transform: translateX(0); }
 }

 @keyframes glitch-loop {
   0%, 90%, 100% { transform: translate(0,0); filter: none; }
   91% { transform: translate(-3px, 1px); filter: hue-rotate(90deg); }
   93% { transform: translate(3px, -1px); }
   95% { transform: translate(-1px, 2px); filter: hue-rotate(-90deg); }
   97% { transform: translate(1px, 0); }
 }

 .hint {
   font-size: 11px;
   color: rgba(255,30,30,0.35);
   letter-spacing: 4px;
   text-transform: uppercase;
   margin-bottom: 28px;
   animation: pulse-hint 2s ease-in-out infinite;
 }

 @keyframes pulse-hint {
   0%, 100% { opacity: 0.35; }
   50% { opacity: 0.7; }
 }

 .denied-box {
   border: 1px solid rgba(255,30,30,0.4);
   padding: 20px 32px;
   position: relative;
   background: rgba(255,0,0,0.03);
   box-shadow: 0 0 30px rgba(255,0,0,0.1), inset 0 0 30px rgba(255,0,0,0.05);
 }

 .denied-box::before,
 .denied-box::after {
   content: '';
   position: absolute;
   width: 12px; height: 12px;
   border-color: #ff1a1a;
   border-style: solid;
 }
 .denied-box::before { top: -1px; left: -1px; border-width: 2px 0 0 2px; }
 .denied-box::after  { bottom: -1px; right: -1px; border-width: 0 2px 2px 0; }

 .label-top {
   font-size: 10px;
   color: rgba(255,30,30,0.5);
   letter-spacing: 6px;
   margin-bottom: 10px;
   text-transform: uppercase;
 }

 .main-text {
   font-family: 'Orbitron', sans-serif;
   font-size: clamp(22px, 5vw, 40px);
   font-weight: 900;
   color: #ff1a1a;
   letter-spacing: 6px;
   text-shadow: 0 0 15px #ff1a1a, 0 0 40px #ff000066;
   animation: text-flicker 3s infinite;
   text-transform: uppercase;
 }

 @keyframes text-flicker {
   0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
     opacity: 1;
     text-shadow: 0 0 15px #ff1a1a, 0 0 40px #ff000066;
   }
   20%, 24%, 55% {
     opacity: 0.6;
     text-shadow: none;
   }
 }

 .sub-text {
   margin-top: 12px;
   font-size: 11px;
   color: rgba(255,30,30,0.45);
   letter-spacing: 3px;
 }

 .scan-line {
   position: fixed;
   top: -4px;
   left: 0; right: 0;
   height: 4px;
   background: linear-gradient(transparent, rgba(255,30,30,0.15), transparent);
   animation: scan 5s linear infinite;
   pointer-events: none;
   z-index: 99;
 }

 @keyframes scan {
   from { top: -4px; }
   to   { top: 100vh; }
 }

 .grid-bg {
   position: fixed;
   inset: 0;
   background-image:
     linear-gradient(rgba(255,30,30,0.04) 1px, transparent 1px),
     linear-gradient(90deg, rgba(255,30,30,0.04) 1px, transparent 1px);
   background-size: 40px 40px;
   pointer-events: none;
   z-index: 0;
 }

 .scene { position: relative; z-index: 10; }
</style>
</head>
<body>

<div class="grid-bg"></div>
<div class="scan-line"></div>

<div class="scene">

 <div class="letter-wrap">
   <div class="letter-bg">X</div>
   <div class="letter-hidden">X</div>
 </div>

 <p class="hint">[ hover the letter to reveal ]</p>

 <div class="denied-box">
   <div class="label-top">system alert</div>
   <div class="main-text">ACCESS DENIED</div>
   <div class="sub-text">authorization level: 0x00 &nbsp;|&nbsp; threat detected</div>
 </div>

</div>

</body>
</html>
```


---

| | |
|---|---|
| ![your image](https://i.ibb.co/V0hSQ2Pw/IMG-2185.jpg) | ![](https://img.shields.io/badge/Name-Lara-555555?style=flat-square&labelColor=333333) <br><br> ![](https://img.shields.io/badge/Location-Saudi_Arabia-ffffff?style=flat-square&labelColor=444444&color=666666) <br> ![](https://img.shields.io/badge/Spoken-Arabic_%7C_English-ffffff?style=flat-square&labelColor=444444&color=666666) <br><br> ![](https://img.shields.io/badge/Expertise-555555?style=flat-square&labelColor=333333) <br> ![](https://img.shields.io/badge/Cybersecurity-ffffff?style=flat-square&labelColor=444444&color=666666) ![](https://img.shields.io/badge/Programming-ffffff?style=flat-square&labelColor=444444&color=666666) ![](https://img.shields.io/badge/Artificial_Intelligence-ffffff?style=flat-square&labelColor=444444&color=666666) <br><br> ![](https://img.shields.io/badge/Languages.Programming-555555?style=flat-square&labelColor=333333) <br> ![](https://img.shields.io/badge/C++-ffffff?style=flat-square&labelColor=444444&color=666666) ![](https://img.shields.io/badge/Python-ffffff?style=flat-square&labelColor=444444&color=666666) ![](https://img.shields.io/badge/Java-ffffff?style=flat-square&labelColor=444444&color=666666) ![](https://img.shields.io/badge/HTML-ffffff?style=flat-square&labelColor=444444&color=666666) ![](https://img.shields.io/badge/CSS-ffffff?style=flat-square&labelColor=444444&color=666666) |

