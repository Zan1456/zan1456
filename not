# Útmutató
Mindenhol ez legyek legyenek beállítva:
- Font: Fredoka
- Font size: 42px

## Follows
- Text color: #FADCBD
- HTML
```HTML
<div id="wrap">
  <div id="alert-box">
    <div id="alert-inner">
      <div id="alert-icon">💜</div>
      <div id="alert-text-wrap">
        <div id="alert-label">Követő</div>
        <div id="alert-text">
          <div id="alert-message">{name}</div>
          <div id="alert-user">Köszönjük, hogy csatlakoztál! ⭐</div>
        </div>
      </div>
      <div id="sparks-container"></div>
    </div>
  </div>
</div>
```

- CSS
```CSS
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@700;800;900&display=swap');

/* ── Kötelező alap ──────────────────────── */
.widget-AlertBox { position: relative; }

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

body, html {
  height: 100%; width: 100%;
  overflow: hidden; background: transparent;
  font-family: 'Nunito', sans-serif;
}

#wrap {
  position: relative; height: 100%; width: 100%;
  display: flex; align-items: center; justify-content: center;
}

#alert-box {
  height: 100%; width: 100%; position: absolute;
  display: flex; align-items: center; justify-content: center;
}

#alert-box.hidden, .hidden { opacity: 0; pointer-events: none; }

/* Kép (ha be van állítva Streamlabsban) */
#alert-image-wrap { display: none; }
#alert-image-wrap:not(:empty) { display: block; }
#alert-image { position: relative; }
#alert-image video { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

/* Streamlabs kötelező IDs */
#alert-text       { z-index: 6; position: relative; }
#alert-text-wrap  { z-index: 6; position: relative; }
#alert-message > span > span { display: inline-block; }

/* ── Alert kártya ──────────────────────── */
#alert-inner {
  display: flex; align-items: center; gap: 14px;
  background: rgba(20, 20, 21, 0.97);
  border: 3px solid #FADCBD;
  border-radius: 14px;
  padding: 14px 22px 14px 16px;
  position: relative; overflow: hidden;
  box-shadow: 5px 5px 0 #44238E, 0 0 36px rgba(68,35,142,.55);
  opacity: 0;
  transform: scale(.7) translateY(32px);
  animation: alertIn .5s cubic-bezier(.22, 1, .36, 1) forwards,
             alertOut .4s ease-in 4.6s forwards;
}

@keyframes alertIn  { to { opacity: 1; transform: scale(1) translateY(0); } }
@keyframes alertOut { to { opacity: 0; transform: scale(.88) translateY(-24px); } }

#alert-inner::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background: radial-gradient(ellipse at 18% 50%, rgba(68,35,142,.2) 0%, transparent 60%);
}

/* ── Ikon ───────────────────────────────── */
#alert-icon {
  font-size: 32px; width: 64px; height: 64px;
  border-radius: 50%; flex-shrink: 0;
  background: #44238E; border: 2px solid #FADCBD;
  display: flex; align-items: center; justify-content: center;
  box-shadow: 0 0 22px rgba(68,35,142,.55);
  animation: iconBounce .5s cubic-bezier(.22, 1, .36, 1) .25s both;
}

@keyframes iconBounce {
  from { transform: scale(0) rotate(-20deg); }
  to   { transform: scale(1) rotate(0deg); }
}

/* ── Szöveg ─────────────────────────────── */
#alert-label {
  font-size: 11px; font-weight: 900;
  text-transform: uppercase; letter-spacing: 1.5px;
  color: rgba(250, 220, 189, 0.55); margin-bottom: 2px;
}

#alert-message {
  font-family: 'Fredoka One', cursive;
  font-size: 36px; line-height: 1;
  color: #FADCBD; text-align: left;
  text-shadow: 2px 2px 0 #44238E;
  animation: namePop .45s cubic-bezier(.22, 1, .36, 1) .35s both;
}

@keyframes namePop {
  from { transform: scale(.7); opacity: 0; }
  to   { transform: scale(1);  opacity: 1; }
}

#alert-user {
  font-size: 14px; font-weight: 700;
  color: rgba(250, 220, 189, 0.75);
  margin-top: 3px; font-style: italic; text-align: left;
}

#alert-user img { vertical-align: middle; height: 1em; }

/* ── Szikra effekt ──────────────────────── */
#sparks-container {
  position: absolute; top: 0; left: 0;
  width: 100%; height: 100%;
  pointer-events: none; z-index: 10;
}
.spark {
  position: absolute; width: 5px; height: 5px;
  border-radius: 50%; opacity: 0;
  animation: sparkFly 1s ease-out forwards;
}
@keyframes sparkFly {
  0%   { opacity: 1; transform: translate(0, 0) scale(1); }
  100% { opacity: 0; transform: translate(var(--tx), var(--ty)) scale(0); }
}
```

- JS
```Js
function resetAnimation() {
  var inner = document.getElementById('alert-inner');
  inner.style.animation = 'none';
  void inner.offsetHeight;
  inner.style.animation = '';
}

function spawnSparks() {
  var c = document.getElementById('sparks-container');
  c.innerHTML = '';
  var COLORS = ['#FADCBD', '#44238E', '#DA77F2', '#fff'];
  for (var i = 0; i < 14; i++) {
    var s = document.createElement('div');
    s.className = 'spark';
    var angle = Math.random() * 360;
    var dist  = 50 + Math.random() * 70;
    s.style.setProperty('--tx', Math.cos(angle * Math.PI / 180) * dist + 'px');
    s.style.setProperty('--ty', Math.sin(angle * Math.PI / 180) * dist + 'px');
    s.style.left  = (36 + Math.random() * 16) + 'px';
    s.style.top   = (36 + Math.random() * 16) + 'px';
    s.style.animationDelay = (Math.random() * 0.3) + 's';
    s.style.background = COLORS[Math.floor(Math.random() * COLORS.length)];
    c.appendChild(s);
  }
}

window.addEventListener('onEventReceived', function(obj) {
  if (!obj || !obj.detail || !obj.detail.event) return;
  resetAnimation();
  spawnSparks();
  document.getElementById('alert-box').classList.remove('hidden');
});

window.addEventListener('onAlertEnd', function() {
  document.getElementById('alert-box').classList.add('hidden');
});
```

## Subscriptions

- Text color: #DA77F2

- HTML
```html
<div id="wrap">
  <div id="alert-box">
    <div id="alert-inner">
      <div id="alert-icon">⭐</div>
      <div id="alert-text-wrap">
        <div id="alert-label">Feliratkozó</div>
        <div id="alert-text">
          <div id="alert-message">{name}</div>
          <div id="alert-user">Köszönjük a feliratkozást! 🎉</div>
        </div>
      </div>
    </div>

  </div>
</div>
```

- CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@700;800;900&display=swap');

/* ── Kötelező alap ──────────────────────── */
.widget-AlertBox { position: relative; }

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

body, html {
  height: 100%; width: 100%;
  overflow: hidden; background: transparent;
  font-family: 'Nunito', sans-serif;
}

#wrap {
  position: relative; height: 100%; width: 100%;
  display: flex; align-items: center; justify-content: center;
}

#alert-box {
  height: 100%; width: 100%; position: absolute;
  display: flex; align-items: center; justify-content: center;
}

#alert-box.hidden, .hidden { opacity: 0; pointer-events: none; }

/* Kép (ha be van állítva Streamlabsban) */
#alert-image-wrap { display: none; }
#alert-image-wrap:not(:empty) { display: block; }
#alert-image { position: relative; }
#alert-image video { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

/* Streamlabs kötelező IDs */
#alert-text       { z-index: 6; position: relative; }
#alert-text-wrap  { z-index: 6; position: relative; }
#alert-message > span > span { display: inline-block; }

/* ── Alert kártya ──────────────────────── */
#alert-inner {
  display: flex; align-items: center; gap: 14px;
  background: rgba(20, 20, 21, 0.97);
  border: 3px solid #DA77F2;
  border-radius: 14px;
  padding: 14px 22px 14px 16px;
  position: relative; overflow: hidden;
  box-shadow: 5px 5px 0 #4A1570, 0 0 36px rgba(218,119,242,.45);
  opacity: 0;
  transform: scale(.7) translateY(32px);
  animation: alertIn .5s cubic-bezier(.22, 1, .36, 1) forwards,
             alertOut .4s ease-in 4.6s forwards;
}

@keyframes alertIn  { to { opacity: 1; transform: scale(1) translateY(0); } }
@keyframes alertOut { to { opacity: 0; transform: scale(.88) translateY(-24px); } }

#alert-inner::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background: radial-gradient(ellipse at 18% 50%, rgba(218,119,242,.2) 0%, transparent 60%);
}

/* ── Ikon ───────────────────────────────── */
#alert-icon {
  font-size: 32px; width: 64px; height: 64px;
  border-radius: 50%; flex-shrink: 0;
  background: #7B2FA8; border: 2px solid #DA77F2;
  display: flex; align-items: center; justify-content: center;
  box-shadow: 0 0 22px rgba(218,119,242,.45);
  animation: iconBounce .5s cubic-bezier(.22, 1, .36, 1) .25s both;
}

@keyframes iconBounce {
  from { transform: scale(0) rotate(-20deg); }
  to   { transform: scale(1) rotate(0deg); }
}

/* ── Szöveg ─────────────────────────────── */
#alert-label {
  font-size: 11px; font-weight: 900;
  text-transform: uppercase; letter-spacing: 1.5px;
  color: rgba(250, 220, 189, 0.55); margin-bottom: 2px;
}

#alert-message {
  font-family: 'Fredoka One', cursive;
  font-size: 36px; line-height: 1;
  color: #DA77F2; text-align: left;
  text-shadow: 2px 2px 0 #4A1570;
  animation: namePop .45s cubic-bezier(.22, 1, .36, 1) .35s both;
}

@keyframes namePop {
  from { transform: scale(.7); opacity: 0; }
  to   { transform: scale(1);  opacity: 1; }
}

#alert-user {
  font-size: 14px; font-weight: 700;
  color: rgba(250, 220, 189, 0.75);
  margin-top: 3px; font-style: italic; text-align: left;
}

#alert-user img { vertical-align: middle; height: 1em; }
```

- JS
```js
function resetAnimation() {
  var inner = document.getElementById('alert-inner');
  inner.style.animation = 'none';
  void inner.offsetHeight;
  inner.style.animation = '';
}

window.addEventListener('onEventReceived', function(obj) {
  if (!obj || !obj.detail || !obj.detail.event) return;
  resetAnimation();
  document.getElementById('alert-box').classList.remove('hidden');
});

window.addEventListener('onAlertEnd', function() {
  document.getElementById('alert-box').classList.add('hidden');
});
```

## Bits

- Text color: #48DBFB

- HTML
```html
<div id="wrap">
  <div id="alert-box">
    <div id="alert-inner">
      <div id="alert-icon">🎉</div>
      <div id="alert-text-wrap">
        <div id="alert-label">Bits / Cheer</div>
        <div id="alert-text">
          <div id="alert-message">{name}</div>
          <div id="alert-user">{amount} Bits💎</div>
        </div>
      </div>
    </div>
  </div>
</div>
```

- CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@700;800;900&display=swap');

/* ── Kötelező alap ──────────────────────── */
.widget-AlertBox { position: relative; }

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

body, html {
  height: 100%; width: 100%;
  overflow: hidden; background: transparent;
  font-family: 'Nunito', sans-serif;
}

#wrap {
  position: relative; height: 100%; width: 100%;
  display: flex; align-items: center; justify-content: center;
}

#alert-box {
  height: 100%; width: 100%; position: absolute;
  display: flex; align-items: center; justify-content: center;
}

#alert-box.hidden, .hidden { opacity: 0; pointer-events: none; }

/* Kép (ha be van állítva Streamlabsban) */
#alert-image-wrap { display: none; }
#alert-image-wrap:not(:empty) { display: block; }
#alert-image { position: relative; }
#alert-image video { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

/* Streamlabs kötelező IDs */
#alert-text       { z-index: 6; position: relative; }
#alert-text-wrap  { z-index: 6; position: relative; }
#alert-message > span > span { display: inline-block; }

/* ── Alert kártya ──────────────────────── */
#alert-inner {
  display: flex; align-items: center; gap: 14px;
  background: rgba(20, 20, 21, 0.97);
  border: 3px solid #48DBFB;
  border-radius: 14px;
  padding: 14px 22px 14px 16px;
  position: relative; overflow: hidden;
  box-shadow: 5px 5px 0 #0A6E8A, 0 0 36px rgba(72,219,251,.45);
  opacity: 0;
  transform: scale(.7) translateY(32px);
  animation: alertIn .5s cubic-bezier(.22, 1, .36, 1) forwards,
             alertOut .4s ease-in 4.6s forwards;
}

@keyframes alertIn  { to { opacity: 1; transform: scale(1) translateY(0); } }
@keyframes alertOut { to { opacity: 0; transform: scale(.88) translateY(-24px); } }

#alert-inner::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background: radial-gradient(ellipse at 18% 50%, rgba(72,219,251,.2) 0%, transparent 60%);
}

/* ── Ikon ───────────────────────────────── */
#alert-icon {
  font-size: 32px; width: 64px; height: 64px;
  border-radius: 50%; flex-shrink: 0;
  background: #0A6E8A; border: 2px solid #48DBFB;
  display: flex; align-items: center; justify-content: center;
  box-shadow: 0 0 22px rgba(72,219,251,.45);
  animation: iconBounce .5s cubic-bezier(.22, 1, .36, 1) .25s both;
}

@keyframes iconBounce {
  from { transform: scale(0) rotate(-20deg); }
  to   { transform: scale(1) rotate(0deg); }
}

/* ── Szöveg ─────────────────────────────── */
#alert-label {
  font-size: 11px; font-weight: 900;
  text-transform: uppercase; letter-spacing: 1.5px;
  color: rgba(250, 220, 189, 0.55); margin-bottom: 2px;
}

#alert-message {
  font-family: 'Fredoka One', cursive;
  font-size: 36px; line-height: 1;
  color: #48DBFB; text-align: left;
  text-shadow: 2px 2px 0 #0A6E8A;
  animation: namePop .45s cubic-bezier(.22, 1, .36, 1) .35s both;
}

@keyframes namePop {
  from { transform: scale(.7); opacity: 0; }
  to   { transform: scale(1);  opacity: 1; }
}

#alert-user {
  font-size: 14px; font-weight: 700;
  color: rgba(250, 220, 189, 0.75);
  margin-top: 3px; font-style: italic; text-align: left;
}

#alert-user img { vertical-align: middle; height: 1em; }
```

- JS
```js
function resetAnimation() {
  var inner = document.getElementById('alert-inner');
  inner.style.animation = 'none';
  void inner.offsetHeight;
  inner.style.animation = '';
}

window.addEventListener('onEventReceived', function(obj) {
  if (!obj || !obj.detail || !obj.detail.event) return;
  resetAnimation();
  document.getElementById('alert-box').classList.remove('hidden');
});

window.addEventListener('onAlertEnd', function() {
  document.getElementById('alert-box').classList.add('hidden');
});
```

## Raids

- Text color: #FF6B6B

- HTML
```html
<div id="wrap">
  <div id="alert-box">
    <div id="alert-inner">
      <div id="alert-icon">⚡</div>
      <div id="alert-text-wrap">
        <div id="alert-label">Raid / Host</div>
        <div id="alert-text">
          <div id="alert-message">{name}</div>
          <div id="alert-user">{count} nézővel raidelnek! 🔥</div>
        </div>
      </div>
    </div>
  </div>
</div>
```

- CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@700;800;900&display=swap');

/* ── Kötelező alap ──────────────────────── */
.widget-AlertBox { position: relative; }

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

body, html {
  height: 100%; width: 100%;
  overflow: hidden; background: transparent;
  font-family: 'Nunito', sans-serif;
}

#wrap {
  position: relative; height: 100%; width: 100%;
  display: flex; align-items: center; justify-content: center;
}

#alert-box {
  height: 100%; width: 100%; position: absolute;
  display: flex; align-items: center; justify-content: center;
}

#alert-box.hidden, .hidden { opacity: 0; pointer-events: none; }

/* Kép (ha be van állítva Streamlabsban) */
#alert-image-wrap { display: none; }
#alert-image-wrap:not(:empty) { display: block; }
#alert-image { position: relative; }
#alert-image video { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

/* Streamlabs kötelező IDs */
#alert-text       { z-index: 6; position: relative; }
#alert-text-wrap  { z-index: 6; position: relative; }
#alert-message > span > span { display: inline-block; }

/* ── Alert kártya ──────────────────────── */
#alert-inner {
  display: flex; align-items: center; gap: 14px;
  background: rgba(20, 20, 21, 0.97);
  border: 3px solid #FF6B6B;
  border-radius: 14px;
  padding: 14px 22px 14px 16px;
  position: relative; overflow: hidden;
  box-shadow: 5px 5px 0 #5A1515, 0 0 36px rgba(255,107,107,.45);
  opacity: 0;
  transform: scale(.7) translateY(32px);
  animation: alertIn .5s cubic-bezier(.22, 1, .36, 1) forwards,
             alertOut .4s ease-in 4.6s forwards;
}

@keyframes alertIn  { to { opacity: 1; transform: scale(1) translateY(0); } }
@keyframes alertOut { to { opacity: 0; transform: scale(.88) translateY(-24px); } }

#alert-inner::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background: radial-gradient(ellipse at 18% 50%, rgba(255,107,107,.2) 0%, transparent 60%);
}

/* ── Ikon ───────────────────────────────── */
#alert-icon {
  font-size: 32px; width: 64px; height: 64px;
  border-radius: 50%; flex-shrink: 0;
  background: #A83030; border: 2px solid #FF6B6B;
  display: flex; align-items: center; justify-content: center;
  box-shadow: 0 0 22px rgba(255,107,107,.45);
  animation: iconBounce .5s cubic-bezier(.22, 1, .36, 1) .25s both;
}

@keyframes iconBounce {
  from { transform: scale(0) rotate(-20deg); }
  to   { transform: scale(1) rotate(0deg); }
}

/* ── Szöveg ─────────────────────────────── */
#alert-label {
  font-size: 11px; font-weight: 900;
  text-transform: uppercase; letter-spacing: 1.5px;
  color: rgba(250, 220, 189, 0.55); margin-bottom: 2px;
}

#alert-message {
  font-family: 'Fredoka One', cursive;
  font-size: 36px; line-height: 1;
  color: #FF6B6B; text-align: left;
  text-shadow: 2px 2px 0 #5A1515;
  animation: namePop .45s cubic-bezier(.22, 1, .36, 1) .35s both;
}

@keyframes namePop {
  from { transform: scale(.7); opacity: 0; }
  to   { transform: scale(1);  opacity: 1; }
}

#alert-user {
  font-size: 14px; font-weight: 700;
  color: rgba(250, 220, 189, 0.75);
  margin-top: 3px; font-style: italic; text-align: left;
}

#alert-user img { vertical-align: middle; height: 1em; }
```

- JS
```js
function resetAnimation() {
  var inner = document.getElementById('alert-inner');
  inner.style.animation = 'none';
  void inner.offsetHeight;
  inner.style.animation = '';
}

window.addEventListener('onEventReceived', function(obj) {
  if (!obj || !obj.detail || !obj.detail.event) return;
  resetAnimation();
  document.getElementById('alert-box').classList.remove('hidden');
});

window.addEventListener('onAlertEnd', function() {
  document.getElementById('alert-box').classList.add('hidden');
});
```

## Donations

- Text color: #FFD700

- HTML
```html
<div id="wrap">
  <div id="alert-box">
    <div id="alert-inner">
      <div id="alert-icon">💛</div>
      <div id="alert-text-wrap">
        <div id="alert-label">Tip / Donáció</div>
        <div id="alert-text">
          <div id="alert-message">{name}</div>
          <div id="alert-user">{amount}</div>
        </div>
      </div>
    </div>
  </div>
</div>
```

- CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@700;800;900&display=swap');

/* ── Kötelező alap ──────────────────────── */
.widget-AlertBox { position: relative; }

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

body, html {
  height: 100%; width: 100%;
  overflow: hidden; background: transparent;
  font-family: 'Nunito', sans-serif;
}

#wrap {
  position: relative; height: 100%; width: 100%;
  display: flex; align-items: center; justify-content: center;
}

#alert-box {
  height: 100%; width: 100%; position: absolute;
  display: flex; align-items: center; justify-content: center;
}

#alert-box.hidden, .hidden { opacity: 0; pointer-events: none; }

/* Kép (ha be van állítva Streamlabsban) */
#alert-image-wrap { display: none; }
#alert-image-wrap:not(:empty) { display: block; }
#alert-image { position: relative; }
#alert-image video { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

/* Streamlabs kötelező IDs */
#alert-text       { z-index: 6; position: relative; }
#alert-text-wrap  { z-index: 6; position: relative; }
#alert-message > span > span { display: inline-block; }

/* ── Alert kártya ──────────────────────── */
#alert-inner {
  display: flex; align-items: center; gap: 14px;
  background: rgba(20, 20, 21, 0.97);
  border: 3px solid #FFD700;
  border-radius: 14px;
  padding: 14px 22px 14px 16px;
  position: relative; overflow: hidden;
  box-shadow: 5px 5px 0 #7A5A00, 0 0 36px rgba(255,215,0,.45);
  opacity: 0;
  transform: scale(.7) translateY(32px);
  animation: alertIn .5s cubic-bezier(.22, 1, .36, 1) forwards,
             alertOut .4s ease-in 4.6s forwards;
}

@keyframes alertIn  { to { opacity: 1; transform: scale(1) translateY(0); } }
@keyframes alertOut { to { opacity: 0; transform: scale(.88) translateY(-24px); } }

#alert-inner::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background: radial-gradient(ellipse at 18% 50%, rgba(255,215,0,.2) 0%, transparent 60%);
}

/* ── Ikon ───────────────────────────────── */
#alert-icon {
  font-size: 32px; width: 64px; height: 64px;
  border-radius: 50%; flex-shrink: 0;
  background: #B8860B; border: 2px solid #FFD700;
  display: flex; align-items: center; justify-content: center;
  box-shadow: 0 0 22px rgba(255,215,0,.45);
  animation: iconBounce .5s cubic-bezier(.22, 1, .36, 1) .25s both;
}

@keyframes iconBounce {
  from { transform: scale(0) rotate(-20deg); }
  to   { transform: scale(1) rotate(0deg); }
}

/* ── Szöveg ─────────────────────────────── */
#alert-label {
  font-size: 11px; font-weight: 900;
  text-transform: uppercase; letter-spacing: 1.5px;
  color: rgba(250, 220, 189, 0.55); margin-bottom: 2px;
}

#alert-message {
  font-family: 'Fredoka One', cursive;
  font-size: 36px; line-height: 1;
  color: #FFD700; text-align: left;
  text-shadow: 2px 2px 0 #7A5A00;
  animation: namePop .45s cubic-bezier(.22, 1, .36, 1) .35s both;
}

@keyframes namePop {
  from { transform: scale(.7); opacity: 0; }
  to   { transform: scale(1);  opacity: 1; }
}

#alert-user {
  font-size: 14px; font-weight: 700;
  color: rgba(250, 220, 189, 0.75);
  margin-top: 3px; font-style: italic; text-align: left;
}

#alert-user img { vertical-align: middle; height: 1em; }
```

- JS
```js
function resetAnimation() {
  var inner = document.getElementById('alert-inner');
  inner.style.animation = 'none';
  void inner.offsetHeight;
  inner.style.animation = '';
}

window.addEventListener('onEventReceived', function(obj) {
  if (!obj || !obj.detail || !obj.detail.event) return;
  resetAnimation();
  document.getElementById('alert-box').classList.remove('hidden');
});

window.addEventListener('onAlertEnd', function() {
  document.getElementById('alert-box').classList.add('hidden');
});
```
