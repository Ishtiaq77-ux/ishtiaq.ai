<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ishtiaq AI — Your Free AI Assistant</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --white: #ffffff;
    --off-white: #f8f7f4;
    --light: #f0ede8;
    --border: #e0dcd5;
    --text: #1a1916;
    --text2: #5a5751;
    --text3: #9e9b96;
    --accent: #185FA5;
    --accent-light: #E6F1FB;
    --accent-dark: #0C447C;
    --green: #3B6D11;
    --green-light: #EAF3DE;
    --green-border: #C0DD97;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--white);
    color: var(--text);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    -webkit-font-smoothing: antialiased;
  }

  /* NAV */
  nav {
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 6vw;
    height: 62px;
    border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(10px);
    position: sticky; top: 0; z-index: 100;
  }
  .nav-logo {
    font-family: 'DM Serif Display', serif;
    font-size: 1.3rem;
    color: var(--text);
    text-decoration: none;
    letter-spacing: -0.02em;
  }
  .nav-logo span { color: var(--accent); }
  .nav-badge {
    font-size: 11px; font-weight: 500;
    padding: 4px 12px; border-radius: 100px;
    background: var(--green-light); color: var(--green);
    border: 1px solid var(--green-border);
  }

  /* HERO */
  .hero {
    text-align: center;
    padding: 70px 6vw 50px;
    background: var(--white);
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; top: -120px; left: 50%; transform: translateX(-50%);
    width: 800px; height: 500px;
    background: radial-gradient(ellipse, #e8edf7 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-tag {
    display: inline-block;
    font-size: 0.8rem; font-weight: 500;
    letter-spacing: 0.1em; text-transform: uppercase;
    color: var(--accent); background: var(--accent-light);
    padding: 6px 16px; border-radius: 100px;
    margin-bottom: 1.5rem;
    position: relative;
  }
  .hero h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(2.5rem, 6vw, 4.2rem);
    line-height: 1.1; letter-spacing: -0.03em;
    color: var(--text);
    margin-bottom: 1rem;
    position: relative;
  }
  .hero h1 em { font-style: italic; color: var(--accent); }
  .hero-sub {
    font-size: 1.1rem; color: var(--text2);
    font-weight: 300; line-height: 1.7;
    max-width: 520px; margin: 0 auto 2rem;
    position: relative;
  }
  .hero-stats {
    display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap;
    margin-bottom: 2.5rem; position: relative;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: 'DM Serif Display', serif;
    font-size: 1.8rem; color: var(--accent); line-height: 1;
  }
  .stat-label { font-size: 0.8rem; color: var(--text3); margin-top: 2px; }

  /* MAIN LAYOUT */
  .main {
    flex: 1;
    display: grid;
    grid-template-columns: 280px 1fr;
    gap: 0;
    max-width: 1100px;
    margin: 0 auto;
    width: 100%;
    padding: 0 4vw 40px;
    align-items: start;
  }

  /* SIDEBAR */
  .sidebar { padding: 24px 20px 24px 0; position: sticky; top: 80px; }
  .sidebar-section { margin-bottom: 2rem; }
  .sidebar-title {
    font-size: 0.72rem; font-weight: 500; letter-spacing: 0.1em;
    text-transform: uppercase; color: var(--text3); margin-bottom: 0.8rem;
  }
  .api-card {
    background: var(--off-white);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.2rem;
    margin-bottom: 1rem;
  }
  .api-card p {
    font-size: 0.85rem; color: var(--text2); line-height: 1.6;
    margin-bottom: 0.8rem; font-weight: 300;
  }
  .api-card p strong { color: var(--text); font-weight: 500; }
  .api-input-wrap { display: flex; flex-direction: column; gap: 6px; }
  .api-inp {
    width: 100%; padding: 8px 12px; font-size: 13px;
    font-family: monospace; border: 1px solid var(--border);
    border-radius: 8px; background: var(--white); color: var(--text);
    outline: none; transition: border-color 0.2s;
  }
  .api-inp:focus { border-color: var(--accent); }
  .btn-row { display: flex; gap: 6px; }
  .btn-save {
    flex: 1; padding: 8px; font-size: 13px; font-weight: 500;
    border-radius: 8px; background: var(--accent); color: #fff;
    border: none; cursor: pointer; font-family: 'DM Sans', sans-serif;
    transition: background 0.2s;
  }
  .btn-save:hover { background: var(--accent-dark); }
  .btn-get {
    flex: 1; padding: 8px; font-size: 12px; font-weight: 500;
    border-radius: 8px; background: var(--green-light); color: var(--green);
    border: 1px solid var(--green-border); cursor: pointer;
    text-decoration: none; text-align: center;
    font-family: 'DM Sans', sans-serif; transition: background 0.2s;
  }
  .btn-get:hover { background: var(--green-border); }
  .status-pill {
    display: inline-flex; align-items: center; gap: 5px;
    font-size: 12px; padding: 4px 10px; border-radius: 100px;
    background: var(--off-white); color: var(--text3);
    border: 1px solid var(--border); margin-top: 6px;
  }
  .status-pill.active { background: var(--green-light); color: var(--green); border-color: var(--green-border); }
  .status-dot { width: 6px; height: 6px; border-radius: 50%; background: currentColor; }

  .topic-grid { display: flex; flex-direction: column; gap: 6px; }
  .topic-btn {
    display: flex; align-items: center; gap: 8px;
    padding: 9px 12px; border-radius: 10px;
    background: var(--off-white); border: 1px solid var(--border);
    font-size: 13px; color: var(--text2); cursor: pointer;
    font-family: 'DM Sans', sans-serif; transition: all 0.15s;
    text-align: left;
  }
  .topic-btn:hover { background: var(--accent-light); border-color: var(--accent); color: var(--accent); }
  .topic-icon { font-size: 16px; }

  /* CHAT AREA */
  .chat-area { padding: 24px 0 0 20px; border-left: 1px solid var(--border); }
  .chat-box {
    border: 1px solid var(--border); border-radius: 18px;
    overflow: hidden; background: var(--white);
    display: flex; flex-direction: column;
    height: 560px;
  }
  .chat-header {
    padding: 14px 18px; border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 10px;
    background: var(--off-white);
  }
  .chat-avatar {
    width: 36px; height: 36px; border-radius: 50%;
    background: var(--accent-light); display: flex;
    align-items: center; justify-content: center; font-size: 18px;
  }
  .chat-name { font-size: 14px; font-weight: 500; }
  .chat-status { font-size: 12px; color: var(--green); display: flex; align-items: center; gap: 4px; }
  .chat-dot { width: 6px; height: 6px; border-radius: 50%; background: #639922; }
  .clear-btn {
    margin-left: auto; font-size: 12px; padding: 5px 12px;
    border-radius: 8px; background: transparent;
    border: 1px solid var(--border); color: var(--text3);
    cursor: pointer; font-family: 'DM Sans', sans-serif;
    transition: all 0.15s;
  }
  .clear-btn:hover { border-color: #E24B4A; color: #E24B4A; }

  .messages {
    flex: 1; overflow-y: auto; padding: 16px;
    display: flex; flex-direction: column; gap: 12px;
    scroll-behavior: smooth;
  }
  .messages::-webkit-scrollbar { width: 3px; }
  .messages::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }

  .msg { display: flex; gap: 8px; align-items: flex-end; max-width: 80%; }
  .msg.user { align-self: flex-end; flex-direction: row-reverse; }
  .msg.bot { align-self: flex-start; }
  .msg-av {
    width: 28px; height: 28px; border-radius: 50%;
    background: var(--accent-light); display: flex;
    align-items: center; justify-content: center;
    font-size: 13px; flex-shrink: 0;
  }
  .msg.user .msg-av { background: var(--accent); color: #fff; font-size: 11px; font-weight: 500; }
  .bubble {
    padding: 10px 15px; font-size: 14px; line-height: 1.65;
    word-break: break-word; white-space: pre-wrap;
  }
  .msg.bot .bubble {
    background: var(--off-white); color: var(--text);
    border: 1px solid var(--border); border-radius: 16px 16px 16px 4px;
  }
  .msg.user .bubble {
    background: var(--accent); color: #fff;
    border-radius: 16px 16px 4px 16px;
  }
  .typing { display: flex; gap: 5px; align-items: center; padding: 13px 15px; }
  .typing span {
    width: 7px; height: 7px; border-radius: 50%;
    background: var(--text3); animation: boing 1.2s infinite;
  }
  .typing span:nth-child(2) { animation-delay: 0.2s; }
  .typing span:nth-child(3) { animation-delay: 0.4s; }
  @keyframes boing { 0%,60%,100%{transform:translateY(0)} 30%{transform:translateY(-7px)} }

  .input-row {
    display: flex; gap: 8px; padding: 12px 14px;
    border-top: 1px solid var(--border); background: var(--white);
    align-items: flex-end;
  }
  #chat-input {
    flex: 1; resize: none; padding: 10px 16px;
    border: 1px solid var(--border); border-radius: 22px;
    font-size: 14px; font-family: 'DM Sans', sans-serif;
    line-height: 1.5; background: var(--off-white);
    color: var(--text); outline: none; max-height: 120px;
    transition: border-color 0.2s, background 0.2s;
  }
  #chat-input:focus { border-color: var(--accent); background: var(--white); }
  #chat-input:disabled { opacity: 0.45; cursor: not-allowed; }
  #send-btn {
    width: 40px; height: 40px; border-radius: 50%;
    background: var(--accent); border: none; cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0; color: #fff; font-size: 18px;
    transition: background 0.2s, transform 0.1s;
  }
  #send-btn:hover { background: var(--accent-dark); }
  #send-btn:active { transform: scale(0.92); }
  #send-btn:disabled { background: var(--border); cursor: not-allowed; }

  /* FEATURES SECTION */
  .features {
    padding: 80px 6vw;
    background: var(--off-white);
    border-top: 1px solid var(--border);
  }
  .features-inner { max-width: 1100px; margin: 0 auto; }
  .section-label {
    font-size: 0.78rem; font-weight: 500; letter-spacing: 0.12em;
    text-transform: uppercase; color: var(--text3); margin-bottom: 0.5rem;
  }
  .section-title {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(1.6rem, 3vw, 2.4rem);
    letter-spacing: -0.02em; margin-bottom: 2.5rem; line-height: 1.2;
  }
  .feat-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1.2rem;
  }
  .feat-card {
    background: var(--white); border: 1px solid var(--border);
    border-radius: 14px; padding: 1.5rem;
    transition: border-color 0.2s;
  }
  .feat-card:hover { border-color: var(--accent); }
  .feat-icon {
    font-size: 1.6rem; margin-bottom: 0.8rem;
    width: 44px; height: 44px; border-radius: 10px;
    background: var(--accent-light); display: flex;
    align-items: center; justify-content: center;
  }
  .feat-title { font-size: 0.95rem; font-weight: 500; margin-bottom: 0.4rem; }
  .feat-desc { font-size: 0.875rem; color: var(--text2); line-height: 1.65; font-weight: 300; }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem 6vw;
    display: flex; align-items: center; justify-content: space-between;
    flex-wrap: wrap; gap: 1rem;
    font-size: 0.87rem; color: var(--text3);
  }
  footer a { color: var(--accent); text-decoration: none; }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    .main { grid-template-columns: 1fr; padding: 0 4vw 30px; }
    .sidebar { position: static; padding: 20px 0 0; border-right: none; }
    .chat-area { padding: 20px 0 0; border-left: none; border-top: 1px solid var(--border); }
    .hero { padding: 50px 5vw 30px; }
    .hero-stats { gap: 1.2rem; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a class="nav-logo" href="#">Ishtiaq <span>AI</span></a>
  <span class="nav-badge">100% Free</span>
</nav>

<!-- HERO -->
<div class="hero">
  <span class="hero-tag">AI Assistant by Ishtiaq</span>
  <h1>Ask me <em>anything</em></h1>
  <p class="hero-sub">A free AI assistant built by Ishtiaq — an ambitious AI student from Faisalabad, Pakistan. Powered by Groq
  <div class="hero-stats">
    <div class="stat"><div class="stat-num">Free</div><div class="stat-label">No cost ever</div></div>
    <div class="stat"><div class="stat-num">Fast</div><div class="stat-label">Groq powered</div></div>
    <div class="stat"><div class="stat-num">Smart</div><div class="stat-label">LLaMA 3 model</div></div>
    <div class="stat"><div class="stat-num">24/7</div><div class="stat-label">Always available</div></div>
  </div>
</div>

<!-- MAIN -->
<div class="main">

  <!-- SIDEBAR -->
  <div class="sidebar">

    <div class="sidebar-section">
      <div class="sidebar-title">API Setup</div>
      <div class="api-card">
        <p>Get your <strong>free</strong> Groq API key — no credit card needed.</p>
        <div class="api-input-wrap">
          <input type="password" id="api-key" class="api-inp" placeholder="gsk_..." autocomplete="off"/>
          <div class="btn-row">
            <button class="btn-save" onclick="saveKey()">Save Key</button>
            <a href="https://console.groq.com/keys" target="_blank" class="btn-get">Get Free Key</a>
          </div>
        </div>
        <div id="status-pill" class="status-pill">
          <span class="status-dot"></span> Not connected
        </div>
      </div>
    </div>

    <div class="sidebar-section">
      <div class="sidebar-title">Quick Topics</div>
      <div class="topic-grid">
        <button class="topic-btn" onclick="quickAsk('Explain machine learning in simple words')"><span class="topic-icon">🧠</span> Machine Learning</button>
        <button class="topic-btn" onclick="quickAsk('What is a neural network and how does it work?')"><span class="topic-icon">🔬</span> Neural Networks</button>
        <button class="topic-btn" onclick="quickAsk('How do I start learning Python from scratch for free?')"><span class="topic-icon">🐍</span> Learn Python</button>
        <button class="topic-btn" onclick="quickAsk('What are the best free resources to learn AI?')"><span class="topic-icon">📚</span> Free AI Resources</button>
        <button class="topic-btn" onclick="quickAsk('What is the difference between AI, ML, and deep learning?')"><span class="topic-icon">🤖</span> AI vs ML vs DL</button>
        <button class="topic-btn" onclick="quickAsk('Give me a motivational quote about learning and success')"><span class="topic-icon">💡</span> Motivation</button>
        <button class="topic-btn" onclick="quickAsk('What programming language should I learn first for AI?')"><span class="topic-icon">💻</span> Best AI Language</button>
        <button class="topic-btn" onclick="quickAsk('Explain transformers and how ChatGPT works')"><span class="topic-icon">⚡</span> How ChatGPT works</button>
      </div>
    </div>

  </div>

  <!-- CHAT -->
  <div class="chat-area">
    <div class="chat-box">
      <div class="chat-header">
        <div class="chat-avatar">🤖</div>
        <div>
          <div class="chat-name">Ishtiaq AI</div>
          <div class="chat-status"><span class="chat-dot"></span> Online — Groq + LLaMA 3</div>
        </div>
        <button class="clear-btn" onclick="clearChat()">Clear chat</button>
      </div>

      <div class="messages" id="messages">
        <div class="msg bot">
          <div class="msg-av">🤖</div>
          <div class="bubble">Assalamu Alaikum! 👋 I'm Ishtiaq AI, built by Ishtiaq — an AI student from Faisalabad, Pakistan.

To activate me, get your free API key from console.groq.com/keys and paste it in the sidebar. It takes 1 minute and costs nothing!</div>
        </div>
      </div>

      <div class="input-row">
        <textarea id="chat-input" rows="1" placeholder="Ask me anything..." disabled></textarea>
        <button id="send-btn" onclick="sendMessage()" aria-label="Send" disabled>&#9650;</button>
      </div>
    </div>
  </div>

</div>

<!-- FEATURES -->
<div class="features">
  <div class="features-inner">
    <p class="section-label">Why Ishtiaq AI</p>
    <h2 class="section-title">Built different</h2>
    <div class="feat-grid">
      <div class="feat-card">
        <div class="feat-icon">🆓</div>
        <div class="feat-title">Completely free</div>
        <div class="feat-desc">No subscriptions, no credit card, no hidden fees. Groq's free tier gives you thousands of messages per day.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">⚡</div>
        <div class="feat-title">Lightning fast</div>
        <div class="feat-desc">Groq's custom hardware makes responses appear almost instantly — faster than most AI tools you've tried.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">🧠</div>
        <div class="feat-title">Powered by 
        <div class="feat-desc">Meta's powerful open source model — the same technology behind some of the world's best AI assistants.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">💬</div>
        <div class="feat-title">Remembers context</div>
        <div class="feat-desc">Keeps track of your full conversation so you can ask follow-up questions naturally, just like talking to a person.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">📱</div>
        <div class="feat-title">Works on any device</div>
        <div class="feat-desc">Fully responsive — works perfectly on your phone, tablet, or desktop browser. No app download needed.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">🇵🇰</div>
        <div class="feat-title">Made in Pakistan</div>
        <div class="feat-desc">Built by Ishtiaq, an AI student from Faisalabad — proving world-class tech can come from anywhere.</div>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <span>© 2026 Ishtiaq AI — Built with 💙 in Faisalabad, Pakistan 🇵🇰</span>
  <span>Powered by <a href="https://groq.com" target="_blank">Groq</a> + LLaMA 3 — <a href="https://console.groq.com/keys" target="_blank">Get free API key</a></span>
</footer>

<script>
  let apiKey = '';
  let history = [];
  const messagesEl = document.getElementById('messages');
  const inputEl = document.getElementById('chat-input');
  const sendBtn = document.getElementById('send-btn');

  function saveKey() {
    const val = document.getElementById('api-key').value.trim();
    if (!val.startsWith('gsk_')) {
      alert('Please enter a valid Groq API key.\nIt starts with "gsk_"\n\nGet it free at: console.groq.com/keys');
      return;
    }
    apiKey = val;
    sendBtn.disabled = false;
    inputEl.disabled = false;
    document.getElementById('api-key').value = '••••••••••••••••••••';
    const pill = document.getElementById('status-pill');
    pill.className = 'status-pill active';
    pill.innerHTML = '<span class="status-dot"></span> Connected & ready!';
    addMessage('bot', '✅ Connected! I am fully activated.\n\nAsk me anything — AI, coding, science, math, daily questions, career advice, whatever you want. This is 100% free!');
    inputEl.focus();
  }

  function quickAsk(text) {
    if (!apiKey) {
      alert('Please save your free Groq API key first!\nGet it at: console.groq.com/keys');
      return;
    }
    inputEl.value = text;
    sendMessage();
  }

  function clearChat() {
    history = [];
    messagesEl.innerHTML = '';
    addMessage('ishtiaq', 'Chat cleared! Ask me anything. 😊');
  }

  function addMessage(role, text) {
    const div = document.createElement('div');
    div.className = 'msg ' + role;
    const av = document.createElement('div');
    av.className = 'msg-av';
    av.textContent = role === 'ishtiaq' ? '🤖' : 'You';
    const bubble = document.createElement('div');
    bubble.className = 'bubble';
    bubble.textContent = text;
    div.appendChild(av);
    div.appendChild(bubble);
    messagesEl.appendChild(div);
    messagesEl.scrollTop = messagesEl.scrollHeight;
  }

  function showTyping() {
    const div = document.createElement('div');
    div.className = 'msg bot'; div.id = 'typing';
    const av = document.createElement('div');
    av.className = 'msg-av'; av.textContent = '🤖';
    const b = document.createElement('div');
    b.className = 'bubble typing';
    b.innerHTML = '<span></span><span></span><span></span>';
    div.appendChild(av); div.appendChild(b);
    messagesEl.appendChild(div);
    messagesEl.scrollTop = messagesEl.scrollHeight;
  }

  function removeTyping() {
    const t = document.getElementById('typing');
    if (t) t.remove();
  }

  async function sendMessage() {
    const text = inputEl.value.trim();
    if (!text || !apiKey) return;
    inputEl.value = '';
    inputEl.style.height = 'auto';
    sendBtn.disabled = true;
    addMessage('user', text);
    history.push({ role: 'user', content: text });
    showTyping();

    try {
      const res = await fetch('https://api.groq.com/openai/v1/chat/completions', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer ' + apiKey
        },
        body: JSON.stringify({
          model: 'llama3-8b-8192',
          messages: [
            {
              role: 'system',
              content: 'You are Ishtiaq AI, a helpful, friendly, and knowledgeable AI assistant created by Ishtiaq — an ambitious AI student from Faisalabad, Pakistan who is working hard to master AI and make an impact on the world. Answer all questions clearly, helpfully, and concisely. Be warm and encouraging. If someone asks who made you, say Ishtiaq made you.'
            },
            ...history
          ],
          max_tokens: 1024,
          temperature: 0.7
        })
      });

      const data = await res.json();
      removeTyping();

      if (data.error) {
        addMessage('bot', '⚠️ Error: ' + data.error.message + '\n\nPlease check your API key.');
        history.pop();
      } else {
        const reply = data.choices[0].message.content;
        history.push({ role: 'assistant', content: reply });
        addMessage('bot', reply);
      }
    } catch(e) {
      removeTyping();
      addMessage
      history.pop();
    }

    sendBtn.disabled = false;
    inputEl.focus();
  }

  inputEl.addEventListener('keydown', e => {
    if (e.key === 'Enter' && !e.shiftKey) { e.preventDefault(); sendMessage(); }
  });

  inputEl.addEventListener('input', function() {
    this.style.height = 'auto';
    this.style.height = Math.min(this.scrollHeight, 120) + 'px';
  });
</script>

</body>
</html>
import os
import openai

client = openai.OpenAI(
    base_url="https://api.groq.com/openai/v1",
    api_key=os.environ.get("GROQ_API_KEY")
)
from groq import Groq

client = Groq()
completion = client.chat.completions.create(
    model="openai/gpt-oss-120b",
    messages=[
      {
        "role": "user",
        "content": ""
      }
    ],
    temperature=1,
    max_completion_tokens=8192,
    top_p=1,
    reasoning_effort="medium",
    stream=True,
    stop=None
)

for chunk in completion:
    print(chunk.choices[0].delta.content or "", end="")
