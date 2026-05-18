<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ishtiaq AI</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet"/>
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg: #f7f7f8;
  --sidebar-bg: #ffffff;
  --chat-bg: #ffffff;
  --border: #e5e5e5;
  --accent: #185FA5;
  --accent-dark: #0C447C;
  --accent-light: #e8f0fb;
  --text: #0d0d0d;
  --text2: #444;
  --text3: #888;
  --user-bubble: #185FA5;
  --bot-bubble: #f4f4f5;
  --green: #16a34a;
  --green-light: #dcfce7;
  --font: 'DM Sans', sans-serif;
}

body {
  font-family: var(--font);
  background: var(--bg);
  color: var(--text);
  height: 100vh;
  display: flex;
  overflow: hidden;
  -webkit-font-smoothing: antialiased;
}

/* ── SIDEBAR ── */
.sidebar {
  width: 260px;
  background: var(--sidebar-bg);
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
  height: 100vh;
  flex-shrink: 0;
}

.sidebar-top {
  padding: 18px 16px 12px;
  border-bottom: 1px solid var(--border);
}

.logo {
  font-family: 'DM Serif Display', serif;
  font-size: 1.4rem;
  color: var(--text);
  letter-spacing: -0.02em;
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 14px;
}
.logo-icon {
  width: 32px; height: 32px; border-radius: 8px;
  background: var(--accent); display: flex;
  align-items: center; justify-content: center;
  font-size: 16px; color: #fff;
}
.logo span { color: var(--accent); }

.new-chat-btn {
  width: 100%; padding: 9px 14px;
  background: var(--accent); color: #fff;
  border: none; border-radius: 10px;
  font-size: 13px; font-weight: 500;
  font-family: var(--font); cursor: pointer;
  display: flex; align-items: center; gap: 8px;
  transition: background 0.2s;
}
.new-chat-btn:hover { background: var(--accent-dark); }

.sidebar-section {
  padding: 14px 16px;
  flex: 1;
  overflow-y: auto;
}

.section-label {
  font-size: 11px; font-weight: 500;
  letter-spacing: 0.08em; text-transform: uppercase;
  color: var(--text3); margin-bottom: 8px;
}

.topic-list { display: flex; flex-direction: column; gap: 2px; }

.topic-item {
  display: flex; align-items: center; gap: 9px;
  padding: 8px 10px; border-radius: 8px;
  font-size: 13px; color: var(--text2);
  cursor: pointer; transition: background 0.15s;
  border: none; background: transparent;
  font-family: var(--font); text-align: left; width: 100%;
}
.topic-item:hover { background: var(--bg); color: var(--text); }
.topic-item .ti { font-size: 15px; opacity: 0.7; }

.sidebar-bottom {
  padding: 14px 16px;
  border-top: 1px solid var(--border);
}

.api-section { display: flex; flex-direction: column; gap: 6px; }
.api-label-row {
  display: flex; align-items: center; justify-content: space-between;
}
.api-label { font-size: 11px; font-weight: 500; color: var(--text3); letter-spacing: 0.06em; text-transform: uppercase; }
.get-key-link {
  font-size: 11px; color: var(--accent); text-decoration: none;
  font-weight: 500;
}
.get-key-link:hover { text-decoration: underline; }

.api-input-wrap { position: relative; }
.api-key-input {
  width: 100%; padding: 8px 36px 8px 10px;
  font-size: 12px; font-family: monospace;
  border: 1px solid var(--border); border-radius: 8px;
  background: var(--bg); color: var(--text); outline: none;
  transition: border-color 0.2s;
}
.api-key-input:focus { border-color: var(--accent); }
.api-toggle {
  position: absolute; right: 8px; top: 50%; transform: translateY(-50%);
  background: none; border: none; cursor: pointer; font-size: 14px;
  color: var(--text3); padding: 2px;
}

.connect-btn {
  width: 100%; padding: 8px; font-size: 13px; font-weight: 500;
  border-radius: 8px; background: var(--accent); color: #fff;
  border: none; cursor: pointer; font-family: var(--font);
  transition: background 0.2s;
}
.connect-btn:hover { background: var(--accent-dark); }

.status-badge {
  display: flex; align-items: center; gap: 5px;
  font-size: 11px; color: var(--text3);
  padding: 4px 0;
}
.status-badge.connected { color: var(--green); }
.status-dot {
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--text3);
}
.status-badge.connected .status-dot { background: var(--green); }

/* ── MAIN CHAT ── */
.main {
  flex: 1;
  display: flex;
  flex-direction: column;
  height: 100vh;
  background: var(--chat-bg);
  overflow: hidden;
}

.chat-topbar {
  padding: 14px 24px;
  border-bottom: 1px solid var(--border);
  display: flex; align-items: center; gap: 10px;
  background: var(--chat-bg);
}
.topbar-title { font-size: 15px; font-weight: 500; }
.topbar-sub { font-size: 12px; color: var(--text3); }
.topbar-right { margin-left: auto; display: flex; gap: 8px; }
.icon-btn {
  width: 32px; height: 32px; border-radius: 8px;
  background: transparent; border: 1px solid var(--border);
  cursor: pointer; display: flex; align-items: center;
  justify-content: center; font-size: 15px;
  color: var(--text3); transition: all 0.15s;
}
.icon-btn:hover { background: var(--bg); color: var(--text); }

/* MESSAGES */
.messages-wrap {
  flex: 1;
  overflow-y: auto;
  padding: 24px 0;
  scroll-behavior: smooth;
}
.messages-wrap::-webkit-scrollbar { width: 4px; }
.messages-wrap::-webkit-scrollbar-thumb { background: var(--border); border-radius: 4px; }

.messages-inner {
  max-width: 720px;
  margin: 0 auto;
  padding: 0 24px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* WELCOME */
.welcome {
  text-align: center;
  padding: 60px 20px 40px;
}
.welcome-icon {
  width: 64px; height: 64px; border-radius: 16px;
  background: var(--accent); display: flex;
  align-items: center; justify-content: center;
  font-size: 32px; margin: 0 auto 20px;
  box-shadow: 0 4px 20px rgba(24,95,165,0.25);
}
.welcome h2 {
  font-family: 'DM Serif Display', serif;
  font-size: 2rem; letter-spacing: -0.02em;
  margin-bottom: 8px;
}
.welcome h2 em { font-style: italic; color: var(--accent); }
.welcome p { font-size: 15px; color: var(--text2); font-weight: 300; line-height: 1.7; max-width: 400px; margin: 0 auto 30px; }

.starter-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  max-width: 500px;
  margin: 0 auto;
}
.starter-card {
  padding: 14px 16px; border-radius: 12px;
  border: 1px solid var(--border); background: var(--bg);
  text-align: left; cursor: pointer; font-family: var(--font);
  transition: all 0.15s; color: var(--text);
}
.starter-card:hover { border-color: var(--accent); background: var(--accent-light); }
.starter-card .s-icon { font-size: 18px; margin-bottom: 6px; }
.starter-card .s-title { font-size: 13px; font-weight: 500; margin-bottom: 2px; }
.starter-card .s-sub { font-size: 12px; color: var(--text3); }

/* MESSAGE ROWS */
.msg-row { display: flex; gap: 12px; align-items: flex-start; }
.msg-row.user { flex-direction: row-reverse; }

.msg-avatar {
  width: 32px; height: 32px; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 14px; flex-shrink: 0; margin-top: 2px;
}
.msg-row.bot .msg-avatar { background: var(--accent); color: #fff; font-size: 16px; }
.msg-row.user .msg-avatar {
  background: #e0e0e0; color: var(--text);
  font-size: 11px; font-weight: 600;
}

.msg-content { max-width: 80%; display: flex; flex-direction: column; gap: 4px; }
.msg-row.user .msg-content { align-items: flex-end; }

.msg-name { font-size: 11px; color: var(--text3); font-weight: 500; }

.bubble {
  padding: 12px 16px;
  font-size: 14px; line-height: 1.7;
  word-break: break-word; white-space: pre-wrap;
}
.msg-row.bot .bubble {
  background: var(--bot-bubble); color: var(--text);
  border-radius: 4px 16px 16px 16px;
}
.msg-row.user .bubble {
  background: var(--user-bubble); color: #fff;
  border-radius: 16px 4px 16px 16px;
}

/* TYPING */
.typing-bubble {
  background: var(--bot-bubble);
  border-radius: 4px 16px 16px 16px;
  padding: 14px 18px;
  display: flex; gap: 5px; align-items: center;
}
.typing-bubble span {
  width: 7px; height: 7px; border-radius: 50%;
  background: var(--text3); animation: pulse 1.3s infinite;
}
.typing-bubble span:nth-child(2) { animation-delay: 0.2s; }
.typing-bubble span:nth-child(3) { animation-delay: 0.4s; }
@keyframes pulse { 0%,60%,100%{transform:translateY(0);opacity:0.5} 30%{transform:translateY(-6px);opacity:1} }

/* INPUT AREA */
.input-area {
  padding: 16px 24px 20px;
  border-top: 1px solid var(--border);
  background: var(--chat-bg);
}
.input-inner {
  max-width: 720px; margin: 0 auto;
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 16px; overflow: hidden;
  transition: border-color 0.2s, box-shadow 0.2s;
}
.input-inner:focus-within {
  border-color: var(--accent);
  box-shadow: 0 0 0 3px rgba(24,95,165,0.08);
}
.input-top {
  display: flex; align-items: flex-end; gap: 8px; padding: 12px 14px 10px;
}
#chat-input {
  flex: 1; background: transparent; border: none; outline: none;
  font-size: 15px; font-family: var(--font); color: var(--text);
  resize: none; line-height: 1.5; max-height: 160px;
  overflow-y: auto;
}
#chat-input::placeholder { color: var(--text3); }
#chat-input:disabled { cursor: not-allowed; }
#send-btn {
  width: 36px; height: 36px; border-radius: 10px;
  background: var(--accent); border: none; cursor: pointer;
  display: flex; align-items: center; justify-content: center;
  color: #fff; font-size: 16px; flex-shrink: 0;
  transition: background 0.2s, transform 0.1s;
}
#send-btn:hover:not(:disabled) { background: var(--accent-dark); }
#send-btn:active:not(:disabled) { transform: scale(0.92); }
#send-btn:disabled { background: var(--border); cursor: not-allowed; }

.input-footer {
  padding: 6px 14px 10px;
  font-size: 11px; color: var(--text3); text-align: center;
}

/* MOBILE SIDEBAR TOGGLE */
.mobile-toggle {
  display: none; width: 36px; height: 36px;
  border-radius: 8px; background: transparent;
  border: 1px solid var(--border); cursor: pointer;
  align-items: center; justify-content: center; font-size: 18px;
}

@media (max-width: 700px) {
  .sidebar { position: fixed; left: -260px; top: 0; z-index: 200; transition: left 0.25s; }
  .sidebar.open { left: 0; box-shadow: 4px 0 20px rgba(0,0,0,0.1); }
  .mobile-toggle { display: flex; }
  .starter-grid { grid-template-columns: 1fr; }
  .messages-inner { padding: 0 16px; }
}
</style>
</head>
<body>

<!-- SIDEBAR -->
<div class="sidebar" id="sidebar">
  <div class="sidebar-top">
    <div class="logo">
      <div class="logo-icon">🤖</div>
      Ishtiaq <span>AI</span>
    </div>
    <button class="new-chat-btn" onclick="newChat()">
      ✏️ New Chat
    </button>
  </div>

  <div class="sidebar-section">
    <div class="section-label">Quick Questions</div>
    <div class="topic-list">
      <button class="topic-item" onclick="startChat('What is machine learning and how does it work?')">🧠 Machine Learning</button>
      <button class="topic-item" onclick="startChat('Explain neural networks in simple words')">🔬 Neural Networks</button>
      <button class="topic-item" onclick="startChat('How do I start learning Python for free?')">🐍 Learn Python</button>
      <button class="topic-item" onclick="startChat('What is the difference between AI, ML, and deep learning?')">🤖 AI vs ML vs DL</button>
      <button class="topic-item" onclick="startChat('What are the best free resources to learn AI in 2024?')">📚 Free AI Resources</button>
      <button class="topic-item" onclick="startChat('How does ChatGPT work? Explain transformers')">⚡ How ChatGPT works</button>
      <button class="topic-item" onclick="startChat('Give me a motivational quote about learning and never giving up')">💡 Motivation</button>
      <button class="topic-item" onclick="startChat('What programming language should I learn first for AI?')">💻 Best AI Language</button>
      <button class="topic-item" onclick="startChat('What is reinforcement learning?')">🎮 Reinforcement Learning</button>
      <button class="topic-item" onclick="startChat('Explain large language models simply')">🗣️ Large Language Models</button>
    </div>
  </div>

  <div class="sidebar-bottom">
    <div class="api-section">
      <div class="api-label-row">
        <span class="api-label">API Key</span>
        <a href="https://console.groq.com/keys" target="_blank" class="get-key-link">Get free key →</a>
      </div>
      <div class="api-input-wrap">
        <input type="password" id="api-key" class="api-key-input" placeholder="gsk_..." autocomplete="off"/>
        <button class="api-toggle" onclick="toggleVisibility()" id="eye-btn">👁️</button>
      </div>
      <button class="connect-btn" onclick="connect()">Connect</button>
      <div class="status-badge" id="status-badge">
        <span class="status-dot"></span> Not connected
      </div>
    </div>
  </div>
</div>

<!-- MAIN -->
<div class="main">
  <div class="chat-topbar">
    <button class="mobile-toggle icon-btn" onclick="toggleSidebar()">☰</button>
    <div>
      <div class="topbar-title">Ishtiaq AI</div>
      <div class="topbar-sub" id="model-label">Connect your free Groq API key to start</div>
    </div>
    <div class="topbar-right">
      <button class="icon-btn" onclick="newChat()" title="New chat">✏️</button>
      <button class="icon-btn" onclick="clearChat()" title="Clear chat">🗑️</button>
    </div>
  </div>

  <div class="messages-wrap" id="messages-wrap">
    <div class="messages-inner" id="messages">

      <!-- WELCOME SCREEN -->
      <div class="welcome" id="welcome">
        <div class="welcome-icon">🤖</div>
        <h2>Hi, I'm <em>Ishtiaq AI</em></h2>
        <p>A free AI assistant built by Ishtiaq — an ambitious AI student from Faisalabad, Pakistan. Ask me anything!</p>
        <div class="starter-grid">
          <button class="starter-card" onclick="startChat('Explain artificial intelligence like I am 10 years old')">
            <div class="s-icon">🤖</div>
            <div class="s-title">What is AI?</div>
            <div class="s-sub">Simple explanation</div>
          </button>
          <button class="starter-card" onclick="startChat('How do I learn AI and machine learning from scratch for free?')">
            <div class="s-icon">📚</div>
            <div class="s-title">Learn AI free</div>
            <div class="s-sub">Beginner roadmap</div>
          </button>
          <button class="starter-card" onclick="startChat('Write me a Python hello world program and explain it')">
            <div class="s-icon">🐍</div>
            <div class="s-title">Python basics</div>
            <div class="s-sub">Code examples</div>
          </button>
          <button class="starter-card" onclick="startChat('Give me 5 motivational quotes about ambition and learning')">
            <div class="s-icon">💪</div>
            <div class="s-title">Motivation</div>
            <div class="s-sub">Stay inspired</div>
          </button>
        </div>
      </div>

    </div>
  </div>

  <div class="input-area">
    <div class="input-inner">
      <div class="input-top">
        <textarea id="chat-input" rows="1" placeholder="Message Ishtiaq AI..." disabled></textarea>
        <button id="send-btn" onclick="sendMessage()" disabled>▲</button>
      </div>
      <div class="input-footer">
        Powered by Groq + LLaMA 3 — 100% Free &nbsp;•&nbsp; Made in Pakistan 🇵🇰
      </div>
    </div>
  </div>
</div>

<script>
let apiKey = '';
let history = [];
let isTyping = false;

const inputEl = document.getElementById('chat-input');
const sendBtn = document.getElementById('send-btn');
const msgsEl = document.getElementById('messages');
const wrapEl = document.getElementById('messages-wrap');

// ── API KEY ──
function toggleVisibility() {
  const inp = document.getElementById('api-key');
  const btn = document.getElementById('eye-btn');
  if (inp.type === 'password') { inp.type = 'text'; btn.textContent = '🙈'; }
  else { inp.type = 'password'; btn.textContent = '👁️'; }
}

function connect() {
  const val = document.getElementById('api-key').value.trim();
  if (!val.startsWith('gsk_')) {
    showToast('⚠️ Enter a valid Groq key (starts with gsk_)\nGet it free at console.groq.com/keys');
    return;
  }
  apiKey = val;
  document.getElementById('api-key').value = '••••••••••••••••••••';
  const badge = document.getElementById('status-badge');
  badge.className = 'status-badge connected';
  badge.innerHTML = '<span class="status-dot"></span> Connected — LLaMA 3 ready';
  document.getElementById('model-label').textContent = 'LLaMA 3 (8B) via Groq — Free & Fast';
  inputEl.disabled = false;
  sendBtn.disabled = false;
  addBotMessage('✅ Connected! I am Ishtiaq AI, powered by LLaMA 3.\n\nAsk me anything — AI, coding, science, math, daily questions, career advice. I\'m here to help. What\'s on your mind?');
  hideWelcome();
  inputEl.focus();
}

// ── CHAT LOGIC ──
function newChat() {
  history = [];
  msgsEl.innerHTML = '';
  showWelcome();
  closeSidebar();
}

function clearChat() {
  history = [];
  msgsEl.innerHTML = '';
  if (apiKey) addBotMessage('Chat cleared! What would you like to talk about? 😊');
  else showWelcome();
}

function showWelcome() {
  msgsEl.innerHTML = `
    <div class="welcome" id="welcome">
      <div class="welcome-icon">🤖</div>
      <h2>Hi, I'm <em>Ishtiaq AI</em></h2>
      <p>A free AI assistant built by Ishtiaq — an ambitious AI student from Faisalabad, Pakistan. Ask me anything!</p>
      <div class="starter-grid">
        <button class="starter-card" onclick="startChat('Explain artificial intelligence like I am 10 years old')">
          <div class="s-icon">🤖</div><div class="s-title">What is AI?</div><div class="s-sub">Simple explanation</div>
        </button>
        <button class="starter-card" onclick="startChat('How do I learn AI and machine learning from scratch for free?')">
          <div class="s-icon">📚</div><div class="s-title">Learn AI free</div><div class="s-sub">Beginner roadmap</div>
        </button>
        <button class="starter-card" onclick="startChat('Write me a Python hello world program and explain it')">
          <div class="s-icon">🐍</div><div class="s-title">Python basics</div><div class="s-sub">Code examples</div>
        </button>
        <button class="starter-card" onclick="startChat('Give me 5 motivational quotes about ambition and learning')">
          <div class="s-icon">💪</div><div class="s-title">Motivation</div><div class="s-sub">Stay inspired</div>
        </button>
      </div>
    </div>`;
}

function hideWelcome() {
  const w = document.getElementById('welcome');
  if (w) w.remove();
}

function startChat(text) {
  if (!apiKey) {
    showToast('⚠️ Please connect your free Groq API key first!\nGet it at console.groq.com/keys');
    return;
  }
  hideWelcome();
  inputEl.value = text;
  sendMessage();
  closeSidebar();
}

function addBotMessage(text) {
  const row = document.createElement('div');
  row.className = 'msg-row bot';
  row.innerHTML = `
    <div class="msg-avatar">🤖</div>
    <div class="msg-content">
      <div class="msg-name">Ishtiaq AI</div>
      <div class="bubble">${escHtml(text)}</div>
    </div>`;
  msgsEl.appendChild(row);
  scrollBottom();
}

function addUserMessage(text) {
  const row = document.createElement('div');
  row.className = 'msg-row user';
  row.innerHTML = `
    <div class="msg-avatar">You</div>
    <div class="msg-content">
      <div class="msg-name">You</div>
      <div class="bubble">${escHtml(text)}</div>
    </div>`;
  msgsEl.appendChild(row);
  scrollBottom();
}

function showTyping() {
  const row = document.createElement('div');
  row.className = 'msg-row bot'; row.id = 'typing-row';
  row.innerHTML = `
    <div class="msg-avatar">🤖</div>
    <div class="msg-content">
      <div class="msg-name">Ishtiaq AI</div>
      <div class="typing-bubble"><span></span><span></span><span></span></div>
    </div>`;
  msgsEl.appendChild(row);
  scrollBottom();
}

function removeTyping() {
  const t = document.getElementById('typing-row');
  if (t) t.remove();
}

async function sendMessage() {
  const text = inputEl.value.trim();
  if (!text || !apiKey || isTyping) return;
  hideWelcome();
  inputEl.value = '';
  inputEl.style.height = 'auto';
  isTyping = true;
  sendBtn.disabled = true;
  addUserMessage(text);
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
            content: `You are Ishtiaq AI, a smart, helpful, and friendly AI assistant created by Ishtiaq — an ambitious and hardworking AI student from Faisalabad, Pakistan who is dedicated to mastering AI and making an impact on the world.

Your personality:
- Warm, encouraging, and supportive
- Clear and easy to understand
- Honest and direct
- Knowledgeable about AI, coding, science, math, and daily life topics

Rules:
- Answer questions clearly and completely
- If asked who made you, say Ishtiaq made you
- Be concise but thorough
- Use examples when helpful
- Encourage learners who want to grow`
          },
          ...history
        ],
        max_tokens: 1024,
        temperature: 0.7,
        stream: false
      })
    });

    const data = await res.json();
    removeTyping();

    if (data.error) {
      addBotMessage('⚠️ Error: ' + data.error.message + '\n\nIf your key is wrong, get a new free one at console.groq.com/keys');
      history.pop();
    } else {
      const reply = data.choices[0].message.content;
      history.push({ role: 'assistant', content: reply });
      addBotMessage(reply);
    }
  } catch(e) {
    removeTyping();
    addBotMessage('⚠️ Connection error.\n\nThis usually happens when:\n1. The API key is wrong\n2. No internet connection\n\nGet a free key at: console.groq.com/keys');
    history.pop();
  }

  isTyping = false;
  sendBtn.disabled = false;
  inputEl.focus();
}

// ── UTILS ──
function escHtml(str) {
  return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function scrollBottom() {
  setTimeout(() => { wrapEl.scrollTop = wrapEl.scrollHeight; }, 50);
}

function showToast(msg) { alert(msg); }

function toggleSidebar() {
  document.getElementById('sidebar').classList.toggle('open');
}
function closeSidebar() {
  document.getElementById('sidebar').classList.remove('open');
}

// Auto-resize textarea
inputEl.addEventListener('input', function() {
  this.style.height = 'auto';
  this.style.height = Math.min(this.scrollHeight, 160) + 'px';
});

// Enter to send
inputEl.addEventListener('keydown', e => {
  if (e.key === 'Enter' && !e.shiftKey) {
    e.preventDefault();
    sendMessage();
  }
});
</script>
</body>
</html>
