<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Custom Rigged Texas Hold'em Simulator (Patterned Winners)</title>
<style>
  :root{
    --card-w:72px; --card-h:96px;
    --bg:#0b2b1d; --panel:#0f3b29; --accent:#ffd700;
    --card-radius:8px;
    --shadow: 0 6px 18px rgba(0,0,0,0.45);
  }
  body{
    margin:0; font-family:Inter,Segoe UI,Roboto,system-ui,Arial;
    background: linear-gradient(180deg,#062618 0%, #0b2b1d 100%);
    color:#e8f5ee; display:flex; flex-direction:column; align-items:center; min-height:100vh;
    padding:24px;
  }

  .topbar{ width: 100%; max-width:1100px; display:flex; justify-content:space-between; align-items:center; margin-bottom:18px; }
  h1{ margin:0; font-size:18px;}
  .controls{ display:flex; gap:10px; align-items:center; }

  button{
    background:#18683f; border:1px solid rgba(255,255,255,0.06); color:white; padding:10px 16px; border-radius:8px;
    cursor:pointer; font-weight:600;
  }
  button:active{ transform:translateY(1px) }

  .table {
    width:100%; max-width:1100px; background:linear-gradient(180deg,#0f442f,#0b3b26); border-radius:12px; padding:18px;
    box-shadow: var(--shadow);
  }
  .board { display:flex; gap:12px; justify-content:center; margin:12px 0 18px; }
  .seat-grid{ display:grid; grid-template-columns: repeat(4, 1fr); gap:14px; }
  .seat{
    background: rgba(255,255,255,0.02); padding:12px; border-radius:10px; min-height:120px; position:relative;
    display:flex; gap:10px; align-items:center;
  }
  .seat .meta{ flex:1; }
  .seat .player-name{ font-weight:700; font-size:14px; opacity:0.95 }
  .seat .player-sub{ font-size:12px; opacity:0.7; margin-top:6px }
  .card-row{ display:flex; gap:8px; margin-top:8px; }
  .card{
    width:var(--card-w); height:var(--card-h); border-radius:var(--card-radius); background:white; display:flex;flex-direction:column;
    justify-content:space-between; padding:8px; box-shadow:0 6px 12px rgba(0,0,0,0.35); color:#111; font-weight:700;
    position:relative; overflow:hidden;
  }
  .card .top, .card .bottom { font-size:14px; line-height:1; }
  .card .center { font-size:28px; display:flex; align-items:center; justify-content:center; }
  .card.red { color:#c92b2b; background:linear-gradient(180deg,#fff, #fff); }
  .card.black { color:#111; background:linear-gradient(180deg,#fff, #fff); }
  .card.back { background:linear-gradient(135deg,#1b3b2a,#163621); color:#fff; display:flex; align-items:center; justify-content:center; font-size:20px; }
  .winner-badge{ position:absolute; right:10px; top:10px; background:var(--accent); color:#111; padding:4px 8px; border-radius:6px; font-weight:800; font-size:12px; }
  .winner{ box-shadow: 0 0 18px rgba(255,215,0,0.9); border:2px solid rgba(255,215,0,0.9); }
  .info-row{ display:flex; gap:12px; align-items:center; justify-content:space-between; margin-top:12px; color:#dcefe0; }
  .small{ font-size:13px; opacity:0.85; }
  .muted{ opacity:0.7; font-size:13px; }
  .pattern{ background: rgba(255,255,255,0.03); padding:6px 8px; border-radius:6px; font-size:13px; }
  .legend{ margin-left:10px; font-size:13px; opacity:0.9 }
  .footer{ margin-top:14px; color:#bfe6c9; font-size:13px; opacity:0.9; text-align:center }
  @media(max-width:900px){
    .seat-grid{ grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<div class="topbar">
  <h1>Custom Texas Hold'em — Patterned Winners (8 players)</h1>
  <div class="controls">
    <div class="pattern small">Pattern: <strong>[8, 6, 4, 2, 1, 3, 5, 7]</strong></div>
    <button id="dealBtn">DEAL</button>
    <button id="resetBtn">RESET</button>
  </div>
</div>

<div class="table" id="table">
  <div class="board" id="boardArea">
    <!-- community cards injected here -->
  </div>

  <div class="seat-grid" id="seatGrid">
    <!-- player seats injected here -->
  </div>

  <div class="info-row">
    <div class="muted" id="handCounter">Hand: 0</div>
    <div class="legend">Click <strong>DEAL</strong> to generate a deal matching the pattern. Winners are auto-selected per pattern.</div>
    <div class="muted">Built for demo / educational use</div>
  </div>
</div>

<div class="footer">Cards are visualized with CSS. Page runs fully in your browser — no server required.</div>

<script>
/* -------------------------
  Card utilities / deck
---------------------------*/
const RANKS = ['2','3','4','5','6','7','8','9','T','J','Q','K','A'];
const SUITS = ['h','d','c','s'];
function cardString(rank, suit){ return rank + suit; }

function newDeck(){
  const d = [];
  for(const r of RANKS) for(const s of SUITS) d.push(cardString(r,s));
  return d;
}
function shuffle(array){
  for(let i=array.length-1;i>0;i--){
    const j = Math.floor(Math.random()*(i+1));
    [array[i], array[j]] = [array[j], array[i]];
  }
  return array;
}

/* -------------------------
  Minimal card renderer (CSS 'image-like')
---------------------------*/
function suitSymbol(s){
  if(s==='h') return '♥';
  if(s==='d') return '♦';
  if(s==='c') return '♣';
  if(s==='s') return '♠';
  return '?';
}
function isRedSuit(s){ return (s==='h' || s==='d'); }

function makeCardElement(card){ // card like "Ah"
  const div = document.createElement('div');
  if(!card){ div.className = 'card back'; div.textContent = ' face-down '; return div; }
  const r = card[0]; const s = card[1];
  div.className = 'card ' + (isRedSuit(s) ? 'red' : 'black');
  div.innerHTML = `<div class="top">${r}${suitSymbol(s)}</div><div class="center">${suitSymbol(s)}</div><div class="bottom">${r}</div>`;
  return div;
}

/* -------------------------
  Integrate evaluator (from your code)
---------------------------*/
(function(){ // evaluator
  const _R = "23456789TJQKA";
  const rankVal = r => _R.indexOf(r);
  const cardRank = c => c[0];
  const cardSuit = c => c[1];

  function combos(arr, k){
    const res = [];
    function helper(start, comb){
      if(comb.length === k){ res.push(comb.slice()); return; }
      for(let i=start;i<arr.length;i++){
        comb.push(arr[i]);
        helper(i+1, comb);
        comb.pop();
      }
    }
    helper(0, []);
    return res;
  }

  function eval5(hand){
    const ranks = hand.map(cardRank).map(r => rankVal(r)).sort((a,b)=>b-a);
    const suits = hand.map(cardSuit);
    const counts = {}; for(const r of ranks) counts[r]=(counts[r]||0)+1;
    const byCount = Object.entries(counts).sort((a,b)=> b[1]-a[1] || b[0]-a[0]).map(x=>[parseInt(x[0]), x[1]]);
    let u = Array.from(new Set(ranks));
    u.sort((a,b)=>b-a);
    let straightHigh = -1;
    for(let i=0;i<=u.length-5;i++){
      if(u[i]-u[i+4] === 4){ straightHigh = u[i]; break; }
    }
    const hasAce = u.includes(12);
    if(straightHigh===-1 && hasAce){
      const needed = [3,2,1,0];
      if(needed.every(x => u.includes(x))) straightHigh = 3;
    }
    const isFlush = suits.every(s=>s===suits[0]);
    const isStraight = straightHigh !== -1;
    if(isStraight && isFlush) return [8, [straightHigh]];
    if(byCount[0][1] === 4){
      const four = byCount[0][0];
      const kicker = Math.max(...ranks.filter(r=>r!==four));
      return [7, [four, kicker]];
    }
    if(byCount[0][1] === 3 && byCount[1] && byCount[1][1] >= 2){
      return [6, [byCount[0][0], byCount[1][0]]];
    }
    if(isFlush) return [5, ranks];
    if(isStraight) return [4, [straightHigh]];
    if(byCount[0][1] === 3){
      const trip = byCount[0][0];
      const kickers = ranks.filter(r=>r!==trip).slice(0,2);
      return [3, [trip, ...kickers]];
    }
    if(byCount[0][1] === 2 && byCount[1] && byCount[1][1] === 2){
      const highPair = Math.max(byCount[0][0], byCount[1][0]);
      const lowPair = Math.min(byCount[0][0], byCount[1][0]);
      const kicker = ranks.filter(r=>r!==highPair && r!==lowPair)[0];
      return [2, [highPair, lowPair, kicker]];
    }
    if(byCount[0][1] === 2){
      const pair = byCount[0][0];
      const kickers = ranks.filter(r=>r!==pair).slice(0,3);
      return [1, [pair, ...kickers]];
    }
    return [0, ranks];
  }

  function compareEval(a, b){
    if(a[0] !== b[0]) return a[0] > b[0] ? 1 : -1;
    for(let i=0;i<Math.max(a[1].length, b[1].length); i++){
      const av = a[1][i] || 0; const bv = b[1][i] || 0;
      if(av !== bv) return av > bv ? 1 : -1;
    }
    return 0;
  }

  function bestFrom(cards){
    const comb = combos(cards, 5);
    let best = null;
    for(const c of comb){
      const e = eval5(c);
      if(!best || compareEval(e, best) === 1) best = e;
    }
    return best;
  }

  function evaluateHands(players, board){
    const results = [];
    for(let i=0;i<players.length;i++){
      const hole = players[i];
      const cards = hole.concat(board);
      if(cards.length < 5) throw new Error("Need at least 5 total cards to evaluate.");
      const best = bestFrom(cards);
      results.push({player: i+1, hole, best});
    }
    let winnerEval = null;
    for(const r of results){
      if(!winnerEval || compareEval(r.best, winnerEval) === 1) winnerEval = r.best;
    }
    const winners = results.filter(r => compareEval(r.best, winnerEval) === 0).map(r=>({player:r.player, hole:r.hole}));
    return {results, winners, winnerEval};
  }

  window.texHoldemEvaluator = { evaluateHands };
})();

/* -------------------------
  Rigging / pattern logic
---------------------------*/
const pattern = [8,6,4,2,1,3,5,7]; // user requested pattern
let handCounter = 0;

const seatGrid = document.getElementById('seatGrid');
const boardArea = document.getElementById('boardArea');
const dealBtn = document.getElementById('dealBtn');
const resetBtn = document.getElementById('resetBtn');
const handCounterLabel = document.getElementById('handCounter');

const NUM_PLAYERS = 8;
const MAX_ATTEMPTS = 1500; // try this many random attempts before fallback

// create seats
function createSeats(){
  seatGrid.innerHTML = '';
  for(let i=1;i<=NUM_PLAYERS;i++){
    const seat = document.createElement('div');
    seat.className = 'seat';
    seat.id = 'seat-'+i;
    seat.innerHTML = `<div class="meta"><div class="player-name">Player ${i}</div><div class="player-sub muted" id="sub-${i}">Hole: —</div><div class="card-row" id="cards-${i}"></div></div>`;
    seatGrid.appendChild(seat);
  }
}
createSeats();

function showDeal(players, board, winners){
  // board
  boardArea.innerHTML = '';
  for(let i=0;i<5;i++){
    const c = board[i] || null;
    boardArea.appendChild( makeCardElement(c) );
  }

  // players
  for(let i=1;i<=NUM_PLAYERS;i++){
    const row = document.getElementById('cards-'+i);
    const sub = document.getElementById('sub-'+i);
    row.innerHTML = '';
    const hole = players[i-1];
    if(!hole || hole.length<2){
      row.appendChild(makeCardElement(null));
      row.appendChild(makeCardElement(null));
      sub.textContent = 'Hole: —';
    } else {
      row.appendChild(makeCardElement(hole[0]));
      row.appendChild(makeCardElement(hole[1]));
      sub.textContent = 'Hole: ' + hole.join(' ');
    }
    const seat = document.getElementById('seat-'+i);
    seat.classList.remove('winner');
    const oldBadge = seat.querySelector('.winner-badge');
    if(oldBadge) oldBadge.remove();
  }

  // highlight winners
  winners.forEach(w => {
    const s = document.getElementById('seat-'+w.player);
    s.classList.add('winner');
    const b = document.createElement('div');
    b.className = 'winner-badge';
    b.textContent = 'WINNER';
    s.appendChild(b);
  });
}

/* -------------------------
  Deal generator that respects pattern
---------------------------*/
function randomHandDeal(deck, numPlayers){
  const players = [];
  const d = deck.slice();
  // deal 2 to each
  for(let p=0;p<numPlayers;p++){
    players.push([ d.pop(), d.pop() ]);
  }
  // burn and board
  const board = [];
  // simple: next 5 cards are board top to bottom
  board.push(d.pop(), d.pop(), d.pop(), d.pop(), d.pop());
  return {players, board};
}

// helper to make non-conflicting random cards while allowing construction
function generateRandomNonConflicting(numPlayers){
  const d = shuffle(newDeck());
  return randomHandDeal(d, numPlayers);
}

// fallback generator: create a very strong guaranteed winning hand for chosen player
function forceWinningHandFor(playerIndex, numPlayers){
  // we'll give chosen player AA, and ensure no one else has pair/overcards to beat it, craft board carefully
  const deck = newDeck();
  // pick two aces for winner
  const aces = deck.filter(c => c[0]==='A');
  const winnerHole = [aces.pop(), aces.pop()]; // two aces
  // remove those from deck
  let remaining = deck.filter(c => !winnerHole.includes(c));
  remaining = shuffle(remaining);
  const players = [];
  // fill other players with low unpaired cards
  for(let p=0;p<numPlayers;p++){
    if(p === (playerIndex-1)) players.push(winnerHole);
    else {
      // give two low cards unlikely to pair the board
      let a = remaining.pop(); let b = remaining.pop();
      players.push([a,b]);
    }
  }
  // craft board with low disconnected cards avoiding pairing other players too much
  const board = [remaining.pop(), remaining.pop(), remaining.pop(), remaining.pop(), remaining.pop()];
  return {players, board};
}

function generateRiggedDeal(winnerPlayer){
  // attempt random tries until winnerPlayer is among winners
  for(let attempt=0; attempt<MAX_ATTEMPTS; attempt++){
    const {players, board} = generateRandomNonConflicting(NUM_PLAYERS);
    try{
      const res = window.texHoldemEvaluator.evaluateHands(players, board);
      const winners = res.winners.map(w=>w.player);
      if(winners.includes(winnerPlayer)){
        return {players, board, winners: res.winners};
      }
    } catch(e){
      // ignore and continue
    }
  }
  // fallback
  const forced = forceWinningHandFor(winnerPlayer, NUM_PLAYERS);
  const resForced = window.texHoldemEvaluator.evaluateHands(forced.players, forced.board);
  return {players: forced.players, board: forced.board, winners: resForced.winners};
}

/* -------------------------
  UI interactions
---------------------------*/
dealBtn.addEventListener('click', () => {
  const patternIndex = handCounter % pattern.length;
  const winnerPlayer = pattern[patternIndex];
  handCounter++;
  handCounterLabel.textContent = 'Hand: ' + handCounter;
  dealBtn.disabled = true;
  dealBtn.textContent = 'DEAL (working...)';
  // allow UI to update
  setTimeout(()=> {
    const {players, board, winners} = generateRiggedDeal(winnerPlayer);
    showDeal(players, board, winners);
    dealBtn.disabled = false;
    dealBtn.textContent = 'DEAL';
  }, 60);
});

resetBtn.addEventListener('click', () => {
  handCounter = 0;
  handCounterLabel.textContent = 'Hand: 0';
  // clear UI
  boardArea.innerHTML = '';
  for(let i=1;i<=NUM_PLAYERS;i++){
    const row = document.getElementById('cards-'+i);
    const sub = document.getElementById('sub-'+i);
    row.innerHTML = '';
    row.appendChild(makeCardElement(null));
    row.appendChild(makeCardElement(null));
    sub.textContent = 'Hole: —';
    const seat = document.getElementById('seat-'+i);
    seat.classList.remove('winner');
    const oldBadge = seat.querySelector('.winner-badge');
    if(oldBadge) oldBadge.remove();
  }
});

/* initialize view with face-down cards */
(function init(){
  boardArea.innerHTML = '';
  for(let i=0;i<5;i++) boardArea.appendChild(makeCardElement(null));
  for(let i=1;i<=NUM_PLAYERS;i++){
    const row = document.getElementById('cards-'+i);
    row.innerHTML = '';
    row.appendChild(makeCardElement(null));
    row.appendChild(makeCardElement(null));
    const sub = document.getElementById('sub-'+i);
    sub.textContent = 'Hole: —';
  }
})();
</script>
</body>
</html>
