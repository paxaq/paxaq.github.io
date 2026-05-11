<div class="screen">
  <div class="terminal" id="terminal">
    <header class="titlebar">
      <div class="dots" aria-hidden="true">
        <span class="dot red"></span>
        <span class="dot yellow"></span>
        <span class="dot green"></span>
      </div>
      <div class="title">jason@tmenu — zsh — 100×40</div>
      <button class="skip" id="skip" type="button" aria-label="Skip animation">skip ▸</button>
    </header>
    <div class="body" id="termBody" aria-live="polite" aria-busy="true">
      <noscript>
        <p># paxaq.dev — Jason Pan, founder of T-Menu.</p>
        <p>Email: <a href="mailto:jason@tmenu.ai">jason@tmenu.ai</a></p>
        <p>Links: <a href="https://tmenu.ai">tmenu.ai</a> · <a href="https://github.com/paxaq">github.com/paxaq</a> · <a href="https://www.linkedin.com/in/paxaq/">linkedin.com/in/paxaq</a></p>
        <p>Writing:</p>
        <ul>
          <li><a href="https://www.qsrmagazine.com/story/why-most-restaurant-ai-investments-fail-to-deliver-roi/">Why Most Restaurant AI Investments Fail to Deliver ROI</a></li>
          <li><a href="https://www.restobiz.ca/how-canadian-restaurants-are-preparing-for-ai-powered-ordering/">How Canadian Restaurants Are Preparing for AI-Powered Ordering</a></li>
          <li><a href="https://www.linkedin.com/pulse/trillion-dollar-question-why-north-american-payments-zhiqiang-pan-kp9oe/">The Trillion-Dollar Question</a></li>
          <li><a href="https://tmenu.ai/2025/12/04/is-the-japanese-model-the-future-of-small-restaurants-in-north-america-2/?lang=en_US">Is the "Japanese Model" the Future of Small Restaurants in North America?</a></li>
        </ul>
      </noscript>
    </div>
  </div>
  <p class="hint">tip: hit <kbd>skip ▸</kbd> if streaming is too slow · this terminal isn't real, but the links are</p>
</div>

<script>
(function () {
  var body = document.getElementById('termBody');
  var skipBtn = document.getElementById('skip');
  if (!body) return;

  var reduceMotion = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  var skipped = reduceMotion;

  skipBtn.addEventListener('click', function () { skipped = true; });

  var PROMPT =
    '<span class="usr">jason</span><span class="dim">@</span><span class="host">tmenu</span> ' +
    '<span class="path">~/paxaq</span> <span class="dollar">$</span> ';

  function autoscroll() {
    var doc = document.scrollingElement || document.documentElement;
    doc.scrollTop = doc.scrollHeight;
  }

  function append(html) {
    body.insertAdjacentHTML('beforeend', html);
    autoscroll();
  }

  function sleep(ms) {
    if (skipped) return Promise.resolve();
    return new Promise(function (r) { setTimeout(r, ms); });
  }

  function typeCmd(text) {
    append(PROMPT);
    var span = document.createElement('span');
    span.className = 'cmd';
    body.appendChild(span);

    return new Promise(function (resolve) {
      var i = 0;
      function tick() {
        if (skipped) {
          span.textContent = text;
          append('\n');
          return resolve();
        }
        span.textContent += text.charAt(i);
        autoscroll();
        i++;
        if (i >= text.length) {
          append('\n');
          return resolve();
        }
        var jitter = 14 + Math.random() * 26;
        setTimeout(tick, jitter);
      }
      tick();
    });
  }

  var script = [
    ['comment', '# paxaq.dev — last login: 2026-05-11 — Homebrew-flavored portfolio'],
    ['blank'],
    ['cmd', 'whoami'],
    ['out', 'Jason Pan <span class="dim">(paxaq)</span>'],
    ['out', '<span class="amber">founder</span> · <a class="link" href="https://tmenu.ai" target="_blank" rel="noopener">T-Menu</a> · <a class="link" href="mailto:jason@tmenu.ai">jason@tmenu.ai</a>'],
    ['blank'],

    ['cmd', 'cat ./now.md'],
    ['header', 'Currently'],
    ['out', 'Building <span class="amber">T-Menu</span> — a digital menu &amp; QR-ordering platform for'],
    ['out', 'restaurants. Most days I&apos;m somewhere between menu schemas,'],
    ['out', 'kitchen-side latency, payments edge cases, and convincing an LLM'],
    ['out', 'to write better dish descriptions than I can.'],
    ['blank'],

    ['cmd', 'brew list paxaq/stack'],
    ['header', 'languages'],
    ['out', '  typescript  python  go  <span class="dim">rust*  swift*</span>'],
    ['header', 'runtimes &amp; data'],
    ['out', '  node  bun  postgres  sqlite  redis'],
    ['header', 'infra'],
    ['out', '  docker  wireguard  tailscale  caddy'],
    ['header', 'ai tooling'],
    ['out', '  claude-code  mcp  agent-skills  mlx'],
    ['out', '<span class="dim">                                                  * still learning</span>'],
    ['blank'],

    ['cmd', 'cat ./writing.md'],
    ['header', 'Writing'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://www.qsrmagazine.com/story/why-most-restaurant-ai-investments-fail-to-deliver-roi/" target="_blank" rel="noopener">Why Most Restaurant AI Investments Fail to Deliver ROI</a>'],
    ['out', '   <span class="dim">qsrmagazine.com</span>'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://www.restobiz.ca/how-canadian-restaurants-are-preparing-for-ai-powered-ordering/" target="_blank" rel="noopener">How Canadian Restaurants Are Preparing for AI-Powered Ordering</a>'],
    ['out', '   <span class="dim">restobiz.ca</span>'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://www.linkedin.com/pulse/trillion-dollar-question-why-north-american-payments-zhiqiang-pan-kp9oe/" target="_blank" rel="noopener">The Trillion-Dollar Question: Why North American Payments Are Behind Asia</a>'],
    ['out', '   <span class="dim">linkedin.com</span>'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://tmenu.ai/2025/12/04/is-the-japanese-model-the-future-of-small-restaurants-in-north-america-2/?lang=en_US" target="_blank" rel="noopener">Is the &ldquo;Japanese Model&rdquo; the Future of Small Restaurants in North America?</a>'],
    ['out', '   <span class="dim">tmenu.ai</span>'],
    ['blank'],

    ['cmd', 'cat ./tastes.txt'],
    ['header', 'What I reach for'],
    ['out', '  <span class="ok">✓</span> local-first, self-hostable, boring-on-purpose'],
    ['out', '  <span class="ok">✓</span> agents as teammates, not magic — small sharp tools'],
    ['out', '  <span class="ok">✓</span> open source as default; forks over rewrites'],
    ['out', '  <span class="ok">✓</span> native &gt; Electron, CLI &gt; dashboard'],
    ['out', '  <span class="ok">✓</span> aesthetic: quiet — restraint as a feature'],
    ['blank'],

    ['cmd', 'cat ./hobbies.txt'],
    ['header', 'Off-hours'],
    ['out', '  <span class="amber">·</span> retro gaming — Ultima Online, handheld emulation'],
    ['out', '  <span class="amber">·</span> homelab tinkering — VPN topologies, dashboards no one reads but me'],
    ['out', '  <span class="amber">·</span> new models the day they drop — image, voice, multimodal'],
    ['out', '  <span class="amber">·</span> food, both ends — restaurant software by day, recipe rabbit holes by night'],
    ['out', '  <span class="amber">·</span> bilingual reading — English tech writing + Chinese indie-dev communities'],
    ['blank'],

    ['cmd', 'contact --all'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://tmenu.ai" target="_blank" rel="noopener">tmenu.ai</a>           <span class="dim"># T-Menu</span>'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://www.linkedin.com/in/paxaq/" target="_blank" rel="noopener">linkedin.com/in/paxaq</a> <span class="dim"># LinkedIn</span>'],
    ['out', '<span class="arrow">→</span> <a class="link" href="https://github.com/paxaq" target="_blank" rel="noopener">github.com/paxaq</a>      <span class="dim"># GitHub</span>'],
    ['out', '<span class="arrow">→</span> <a class="link" href="mailto:jason@tmenu.ai">jason@tmenu.ai</a>        <span class="dim"># email</span>'],
    ['blank']
  ];

  async function run() {
    await sleep(300);
    for (var i = 0; i < script.length; i++) {
      var entry = script[i];
      var kind = entry[0];
      var text = entry[1];

      if (kind === 'comment') {
        append('<span class="comment">' + text + '</span>\n');
        await sleep(120);
      } else if (kind === 'blank') {
        append('\n');
        await sleep(40);
      } else if (kind === 'cmd') {
        await typeCmd(text);
        await sleep(180);
      } else if (kind === 'header') {
        append('<span class="arrow-h">==&gt;</span> <span class="amber">' + text + '</span>\n');
        await sleep(60);
      } else if (kind === 'out') {
        append(text + '\n');
        await sleep(skipped ? 0 : 28);
      }
    }
    append(PROMPT + '<span class="cursor" aria-hidden="true"></span>');
    body.setAttribute('aria-busy', 'false');
    autoscroll();
  }

  run();
})();
</script>
