

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>今週の文法 · Weekly Card</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+JP:wght@300;400;600&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
–ink: #1a1612;
–ink-mid: #5a4f47;
–ink-light: #9a8f87;
–paper: #f7f4f0;
–paper-warm: #ede8e2;
–rule: rgba(90,79,71,0.15);
–accent: #3d6b52;
–accent-light: rgba(61,107,82,0.08);
–done-bg: #2a4a38;
}

@media (prefers-color-scheme: dark) {
:root {
–ink: #e8e2da;
–ink-mid: #a89f97;
–ink-light: #6a6260;
–paper: #1a1714;
–paper-warm: #221f1c;
–rule: rgba(168,159,151,0.12);
–accent: #6a9e82;
–accent-light: rgba(106,158,130,0.1);
–done-bg: #1e3329;
}
}

@media (prefers-reduced-motion: reduce) {
* { transition: none !important; animation: none !important; }
}

html, body {
height: 100%;
background: var(–paper);
color: var(–ink);
font-family: ‘Libre Baskerville’, Georgia, serif;
-webkit-font-smoothing: antialiased;
}

body {
display: flex;
flex-direction: column;
align-items: center;
justify-content: flex-start;
min-height: 100vh;
padding: 40px 20px 60px;
}

.header {
width: 100%;
max-width: 480px;
display: flex;
justify-content: space-between;
align-items: baseline;
margin-bottom: 32px;
}

.header-title {
font-family: ‘Noto Serif JP’, serif;
font-size: 0.82rem;
font-weight: 300;
color: var(–ink-light);
letter-spacing: 0.12em;
}

.header-progress {
font-size: 0.78rem;
color: var(–ink-light);
font-style: italic;
}

.card {
width: 100%;
max-width: 480px;
background: var(–paper-warm);
border: 1px solid var(–rule);
border-radius: 2px;
padding: 36px 32px 28px;
transition: opacity 0.3s;
}

.card.fading { opacity: 0; }

/* Book label at top */
.book-label {
font-size: 0.72rem;
color: var(–ink-light);
letter-spacing: 0.1em;
margin-bottom: 20px;
font-style: italic;
}

/* Grammar pattern — the headline */
.pattern {
font-family: ‘Noto Serif JP’, serif;
font-size: 1.7rem;
font-weight: 400;
color: var(–ink);
line-height: 1.35;
margin-bottom: 6px;
}

.use {
font-size: 0.88rem;
color: var(–ink-mid);
line-height: 1.6;
margin-bottom: 24px;
}

.divider {
width: 32px;
height: 1px;
background: var(–rule);
margin-bottom: 24px;
}

/* Example sentence from notes */
.section-label {
font-size: 0.7rem;
color: var(–ink-light);
letter-spacing: 0.08em;
margin-bottom: 8px;
font-style: italic;
}

.example-jp {
font-family: ‘Noto Serif JP’, serif;
font-size: 1.05rem;
color: var(–ink);
line-height: 1.7;
margin-bottom: 4px;
}

.example-en {
font-size: 0.84rem;
color: var(–ink-mid);
font-style: italic;
margin-bottom: 28px;
line-height: 1.5;
}

/* Writing prompt area */
.prompt-block {
background: var(–accent-light);
border-left: 2px solid var(–accent);
padding: 14px 16px;
margin-bottom: 20px;
border-radius: 0 2px 2px 0;
}

.prompt-instruction {
font-size: 0.84rem;
color: var(–accent);
line-height: 1.6;
margin-bottom: 0;
}

.prompt-instruction strong {
font-weight: 700;
}

/* AI prompt generation */
.fixation-row {
display: flex;
gap: 8px;
margin-bottom: 20px;
align-items: stretch;
}

.fixation-input {
flex: 1;
background: var(–paper);
border: 1px solid var(–rule);
border-radius: 2px;
padding: 9px 12px;
font-family: ‘Libre Baskerville’, serif;
font-size: 0.84rem;
color: var(–ink);
outline: none;
transition: border-color 0.2s;
}

.fixation-input:focus {
border-color: var(–accent);
}

.fixation-input::placeholder {
color: var(–ink-light);
font-style: italic;
}

.gen-btn {
background: none;
border: 1px solid var(–rule);
border-radius: 2px;
padding: 9px 14px;
font-family: ‘Libre Baskerville’, serif;
font-size: 0.78rem;
color: var(–ink-mid);
cursor: pointer;
white-space: nowrap;
transition: all 0.2s;
}

.gen-btn:hover { border-color: var(–accent); color: var(–accent); }
.gen-btn:disabled { opacity: 0.4; cursor: not-allowed; }

.ai-prompt-result {
font-family: ‘Noto Serif JP’, serif;
font-size: 0.96rem;
color: var(–ink);
line-height: 1.75;
padding: 14px 16px;
background: var(–accent-light);
border-left: 2px solid var(–accent);
border-radius: 0 2px 2px 0;
margin-bottom: 20px;
display: none;
}

.ai-prompt-result.visible { display: block; }

/* Writing area */
.write-area {
width: 100%;
min-height: 80px;
background: var(–paper);
border: 1px solid var(–rule);
border-radius: 2px;
padding: 12px 14px;
font-family: ‘Noto Serif JP’, serif;
font-size: 1rem;
color: var(–ink);
resize: vertical;
outline: none;
line-height: 1.8;
transition: border-color 0.2s;
margin-bottom: 24px;
}

.write-area:focus { border-color: var(–accent); }
.write-area::placeholder { color: var(–ink-light); font-style: italic; }

/* Done button */
.done-btn {
width: 100%;
background: var(–done-bg);
color: #e8ede9;
border: none;
border-radius: 2px;
padding: 14px;
font-family: ‘Libre Baskerville’, serif;
font-size: 0.9rem;
cursor: pointer;
letter-spacing: 0.04em;
transition: opacity 0.2s;
}

.done-btn:hover { opacity: 0.88; }

/* Done state */
.done-state {
display: none;
text-align: center;
padding: 48px 32px;
}

.done-state.visible { display: block; }
.card.done-mode { display: none; }

.done-kanji {
font-family: ‘Noto Serif JP’, serif;
font-size: 4rem;
font-weight: 300;
color: var(–accent);
display: block;
margin-bottom: 16px;
line-height: 1;
}

.done-message {
font-size: 0.9rem;
color: var(–ink-mid);
line-height: 1.7;
margin-bottom: 28px;
}

.done-next {
font-family: ‘Noto Serif JP’, serif;
font-size: 0.82rem;
color: var(–ink-light);
margin-bottom: 24px;
}

.undo-btn {
background: none;
border: 1px solid var(–rule);
border-radius: 2px;
padding: 8px 20px;
font-family: ‘Libre Baskerville’, serif;
font-size: 0.78rem;
color: var(–ink-light);
cursor: pointer;
transition: all 0.2s;
}

.undo-btn:hover { color: var(–ink); border-color: var(–ink-mid); }

/* Reset link */
.reset-row {
width: 100%;
max-width: 480px;
text-align: right;
margin-top: 16px;
}

.reset-link {
font-size: 0.72rem;
color: var(–ink-light);
cursor: pointer;
font-style: italic;
text-decoration: underline;
text-underline-offset: 3px;
background: none;
border: none;
font-family: ‘Libre Baskerville’, serif;
}

.loading-note {
font-size: 0.78rem;
color: var(–ink-light);
font-style: italic;
text-align: center;
margin-top: 8px;
}
</style>

</head>
<body>

<div class="header">
  <span class="header-title">今週の文法</span>
  <span class="header-progress" id="progressLabel"></span>
</div>

<div class="card" id="mainCard">
  <div class="book-label" id="bookLabel"></div>
  <div class="pattern" id="patternEl"></div>
  <div class="use" id="useEl"></div>
  <div class="divider"></div>

  <div class="section-label">from your notes</div>
  <div class="example-jp" id="exampleJp"></div>
  <div class="example-en" id="exampleEn"></div>

  <div class="section-label">this week's prompt</div>
  <div class="prompt-block">
    <div class="prompt-instruction" id="defaultPrompt"></div>
  </div>

  <div class="fixation-row">
    <input class="fixation-input" id="fixationInput" type="text" placeholder="current obsession (e.g. Elden Ring, Dracula, The Bear…)" />
    <button class="gen-btn" id="genBtn" onclick="generatePrompt()">tune it →</button>
  </div>

  <div class="ai-prompt-result" id="aiPromptResult"></div>

  <textarea class="write-area" id="writeArea" placeholder="一文だけ書いてください…"></textarea>

<button class="done-btn" onclick="markDone()">完了 — done for this week</button>

</div>

<div class="done-state" id="doneState">
  <span class="done-kanji">完</span>
  <p class="done-message">That's this week's point. Anki handles the rest.</p>
  <p class="done-next" id="nextPreview"></p>
  <button class="undo-btn" onclick="undoDone()">undo — I'm not done yet</button>
</div>

<div class="reset-row">
  <button class="reset-link" onclick="confirmReset()">reset progress</button>
</div>

<script>
// ── ALL 152 GRAMMAR POINTS ────────────────────────────────────────────────────
const ALL_POINTS = [
  // GENKI I
  { id:"g1-01", book:"Genki I · Ch.1",  pattern:"X は Y です",              use:"X is Y (copula, present)",                    ex:"ここは有名なお寺です。",           exEn:"This is a famous temple." },
  { id:"g1-02", book:"Genki I · Ch.1",  pattern:"Question Sentences",       use:"か ending for yes/no questions",               ex:"これは何ですか。",                 exEn:"What is this?" },
  { id:"g1-03", book:"Genki I · Ch.1",  pattern:"Noun1 の Noun2",           use:"Possession / noun modification",               ex:"友達の写真を撮りました。",         exEn:"I took a photo of my friend." },
  { id:"g1-04", book:"Genki I · Ch.2",  pattern:"これ・この・ここ",          use:"This thing / this [noun] / this place",        ex:"このお寺はとても古いです。",       exEn:"This temple is very old." },
  { id:"g1-05", book:"Genki I · Ch.2",  pattern:"Noun も",                  use:"X too / also",                                 ex:"奈良にも行きました。",             exEn:"I also went to Nara." },
  { id:"g1-06", book:"Genki I · Ch.2",  pattern:"Noun じゃないです",         use:"X is not Y (negative copula)",                 ex:"ここはホテルじゃないです。旅館です。", exEn:"This is not a hotel. It's a Japanese inn." },
  { id:"g1-07", book:"Genki I · Ch.2",  pattern:"〜ね・〜よ",               use:"Seeking agreement (ね) / asserting info (よ)",  ex:"この景色、きれいですね。",         exEn:"This scenery is beautiful, isn't it." },
  { id:"g1-08", book:"Genki I · Ch.3",  pattern:"Verb Conjugation",         use:"ます form — present/future polite",             ex:"明日、京都に行きます。",           exEn:"I'm going to Kyoto tomorrow." },
  { id:"g1-09", book:"Genki I · Ch.3",  pattern:"Verb Types & Present",     use:"Godan vs ichidan — dictionary form",            ex:"毎日日本語を勉強します。",         exEn:"I study Japanese every day." },
  { id:"g1-10", book:"Genki I · Ch.3",  pattern:"Particles を・に・で・へ",  use:"Object (を) / direction (に) / location of action (で) / toward (へ)", ex:"電車で京都に行きました。", exEn:"I went to Kyoto by train." },
  { id:"g1-11", book:"Genki I · Ch.3",  pattern:"Time Reference",           use:"Specific times + に / relative times no に",    ex:"三時に神社に着きました。",         exEn:"I arrived at the shrine at 3 o'clock." },
  { id:"g1-12", book:"Genki I · Ch.3",  pattern:"〜ませんか",               use:"Invitation — won't you do X?",                  ex:"一緒に抹茶を飲みませんか。",       exEn:"Would you like to drink matcha together?" },
  { id:"g1-13", book:"Genki I · Ch.3",  pattern:"Word Order",               use:"Time → place → verb (SOV)",                    ex:"昨日、嵐山で写真をたくさん撮りました。", exEn:"Yesterday I took lots of photos in Arashiyama." },
  { id:"g1-14", book:"Genki I · Ch.3",  pattern:"Frequency Adverbs",        use:"いつも・よく・時々・あまり・全然",               ex:"旅行中、いつも早起きしました。",   exEn:"I always woke up early during the trip." },
  { id:"g1-15", book:"Genki I · Ch.3",  pattern:"Topic Particle は",        use:"Marks topic — contrast or general statement",   ex:"バスに乗りましょう。タクシーは高いですから。", exEn:"Let's take the bus. Taxis are expensive." },
  { id:"g1-16", book:"Genki I · Ch.4",  pattern:"X が あります・います",     use:"There is X — inanimate あります / animate います", ex:"駅の近くにコンビニがあります。", exEn:"There's a convenience store near the station." },
  { id:"g1-17", book:"Genki I · Ch.4",  pattern:"Describing Where Things Are", use:"X は Y の〔location〕です",                 ex:"宿は駅のとなりにあります。",       exEn:"The inn is next to the station." },
  { id:"g1-18", book:"Genki I · Ch.4",  pattern:"Past Tense of です",       use:"〜でした / 〜じゃなかったです",                  ex:"あのお寺はとても静かでした。",     exEn:"That temple was very quiet." },
  { id:"g1-19", book:"Genki I · Ch.4",  pattern:"Past Tense of Verbs",      use:"〜ました / 〜ませんでした",                      ex:"昨日、金閣寺に行きました。",       exEn:"Yesterday I went to Kinkakuji." },
  { id:"g1-20", book:"Genki I · Ch.4",  pattern:"も (also/either)",         use:"X も Y — extends topic to another item",        ex:"奈良にも行きました。とても良かったです。", exEn:"I also went to Nara. It was wonderful." },
  { id:"g1-21", book:"Genki I · Ch.4",  pattern:"〜時間 (duration)",        use:"Duration counter — 一時間、二時間",              ex:"バスで二時間かかりました。",       exEn:"It took two hours by bus." },
  { id:"g1-22", book:"Genki I · Ch.4",  pattern:"たくさん",                 use:"Many / a lot",                                  ex:"旅行中、写真をたくさん撮りました。", exEn:"I took lots of photos during the trip." },
  { id:"g1-23", book:"Genki I · Ch.4",  pattern:"と (together with)",       use:"With [person] — accompaniment",                 ex:"友達と一緒に旅行しました。",       exEn:"I traveled together with a friend." },
  { id:"g1-24", book:"Genki I · Ch.5",  pattern:"Adjectives (い・な)",      use:"い-adj conjugate / な-adj + noun",              ex:"あの温泉はとても気持ちよかったです。", exEn:"That hot spring felt really good." },
  { id:"g1-25", book:"Genki I · Ch.5",  pattern:"好き・嫌い",               use:"好きです / 嫌いです — が marks the object",       ex:"日本食が大好きです。特にラーメンが好きです。", exEn:"I love Japanese food. Especially ramen." },
  { id:"g1-26", book:"Genki I · Ch.5",  pattern:"ましょう・ましょうか",      use:"Let's do X / Shall I do X?",                    ex:"そろそろ出発しましょうか。",       exEn:"Shall we head out soon?" },
  { id:"g1-27", book:"Genki I · Ch.5",  pattern:"Counting",                 use:"Number + counter — 〜枚、〜本、〜冊",             ex:"お土産を三つ買いました。",         exEn:"I bought three souvenirs." },
  { id:"g1-28", book:"Genki I · Ch.6",  pattern:"て form",                  use:"Base for many patterns — conjugation rules",     ex:"カメラを出して、写真を撮りました。", exEn:"I took out the camera and took photos." },
  { id:"g1-29", book:"Genki I · Ch.6",  pattern:"〜てください",             use:"Please do X",                                   ex:"ゆっくり話してください。",         exEn:"Please speak slowly." },
  { id:"g1-30", book:"Genki I · Ch.6",  pattern:"〜てもいいです",           use:"May I / it's okay to do X",                      ex:"ここで写真を撮ってもいいですか。", exEn:"Is it okay to take photos here?" },
  { id:"g1-31", book:"Genki I · Ch.6",  pattern:"〜てはいけません",         use:"Must not do X (prohibition)",                    ex:"境内では飲食してはいけません。",   exEn:"You must not eat or drink inside the shrine grounds." },
  { id:"g1-32", book:"Genki I · Ch.6",  pattern:"Describing Two Activities", use:"て form chains two actions — A て B",           ex:"朝早く起きて、神社に行きました。", exEn:"I woke up early and went to the shrine." },
  { id:"g1-33", book:"Genki I · Ch.6",  pattern:"〜から (because)",         use:"(situation)。(explanation)から。",               ex:"バスに乗りましょう。タクシーは高いですから。", exEn:"Let's take the bus. Because taxis are expensive." },
  { id:"g1-34", book:"Genki I · Ch.6",  pattern:"〜ましょうか (shall I)",   use:"Shall I do X? — offering help",                  ex:"写真を撮りましょうか。",           exEn:"Shall I take a photo?" },
  { id:"g1-35", book:"Genki I · Ch.7",  pattern:"〜ている",                 use:"Action in progress / past connected to present",  ex:"今、嵐山を歩いています。",         exEn:"I am walking through Arashiyama right now." },
  { id:"g1-36", book:"Genki I · Ch.7",  pattern:"Topic は + subject が",    use:"Two-noun sentences — topic vs subject",          ex:"あの山は雪が白くてきれいです。",   exEn:"That mountain's snow is white and beautiful." },
  { id:"g1-37", book:"Genki I · Ch.7",  pattern:"て forms for Joining",     use:"〜て to list actions or states in sequence",      ex:"バスに乗って、お寺に行って、写真を撮りました。", exEn:"I took the bus, went to the temple, and took photos." },
  { id:"g1-38", book:"Genki I · Ch.7",  pattern:"verb stem + に行く",       use:"Go somewhere to do X",                           ex:"ラーメンを食べに行きました。",     exEn:"I went to eat ramen." },
  { id:"g1-39", book:"Genki I · Ch.7",  pattern:"Counting People",          use:"〜人 counter — 一人、二人、三人",                  ex:"友達と二人で旅行しました。",       exEn:"I traveled with a friend, just the two of us." },
  { id:"g1-40", book:"Genki I · Ch.8",  pattern:"Short Forms",              use:"Plain/dictionary form — informal speech base",   ex:"昨日、すごくいい景色を見た。",     exEn:"Yesterday I saw a really great view." },
  { id:"g1-41", book:"Genki I · Ch.8",  pattern:"Informal Speech",          use:"Short form in casual conversation",              ex:"あのお寺、めちゃくちゃきれいだった！", exEn:"That temple was incredibly beautiful!" },
  { id:"g1-42", book:"Genki I · Ch.8",  pattern:"〜と思います",             use:"I think that X",                                 ex:"また日本に来たいと思います。",     exEn:"I think I want to come to Japan again." },
  { id:"g1-43", book:"Genki I · Ch.8",  pattern:"〜と言っていました",        use:"Someone said that X (reported speech)",          ex:"ガイドさんは明日雨が降ると言っていました。", exEn:"The guide said it would rain tomorrow." },
  { id:"g1-44", book:"Genki I · Ch.8",  pattern:"〜ないでください",         use:"Please don't do X",                              ex:"ここでは写真を撮らないでください。", exEn:"Please don't take photos here." },
  { id:"g1-45", book:"Genki I · Ch.8",  pattern:"verb の が好きです",       use:"Like doing X — verb nominalised with の",         ex:"旅行中、散歩するのが好きです。",   exEn:"I like taking walks during trips." },
  { id:"g1-46", book:"Genki I · Ch.8",  pattern:"が (subject marker)",      use:"が marks subject — contrast with は",             ex:"あそこに富士山が見えます。",       exEn:"Mt. Fuji can be seen over there." },
  { id:"g1-47", book:"Genki I · Ch.8",  pattern:"何か・何も",               use:"Something / nothing (+ neg.)",                   ex:"お土産に何か買いましたか。いいえ、何も買いませんでした。", exEn:"Did you buy anything as a souvenir? No, I bought nothing." },
  // GENKI II
  { id:"g2-01", book:"Genki II · Ch.9",  pattern:"Past Tense Short Forms",  use:"Plain past — verb た / なかった",                ex:"昨日、金閣寺に行った。最高だった。", exEn:"Yesterday I went to Kinkakuji. It was the best." },
  { id:"g2-02", book:"Genki II · Ch.9",  pattern:"Qualifying Nouns",        use:"Verb/adj clause before noun (relative clause)",   ex:"昨日食べたラーメンがとても美味しかった。", exEn:"The ramen I ate yesterday was really delicious." },
  { id:"g2-03", book:"Genki II · Ch.9",  pattern:"まだ〜ていません",         use:"Have not done X yet",                             ex:"まだ京都のお寺を全部見ていません。", exEn:"I still haven't seen all of Kyoto's temples." },
  { id:"g2-04", book:"Genki II · Ch.9",  pattern:"〜から (reason first)",   use:"Explanation comes before situation",              ex:"足が痛かったから、タクシーに乗りました。", exEn:"My feet hurt, so I took a taxi." },
  { id:"g2-05", book:"Genki II · Ch.10", pattern:"Comparison: two items",   use:"A のほうが B より (property)",                    ex:"京都のほうが大阪より静かだと思います。", exEn:"I think Kyoto is quieter than Osaka." },
  { id:"g2-06", book:"Genki II · Ch.10", pattern:"Comparison: 3+ items",    use:"(class)の中でAがいちばん(property)",              ex:"行った場所の中で、京都が一番好きです。", exEn:"Among all the places I went, I like Kyoto best." },
  { id:"g2-07", book:"Genki II · Ch.10", pattern:"adjective/noun + の",     use:"の replaces a repeated noun",                     ex:"どのお寺が一番好きですか。古いのが好きです。", exEn:"Which temple do you like best? I like the old ones." },
  { id:"g2-08", book:"Genki II · Ch.10", pattern:"〜つもりだ",              use:"Intend to / plan to",                              ex:"来年また日本に来るつもりです。",   exEn:"I plan to come to Japan again next year." },
  { id:"g2-09", book:"Genki II · Ch.10", pattern:"adjective + なる",        use:"Become [adjective] — change of state",             ex:"旅行中に日本語が少し上手になりました。", exEn:"My Japanese got a little better during the trip." },
  { id:"g2-10", book:"Genki II · Ch.10", pattern:"どこかに・どこにも",       use:"Somewhere (pos.) / nowhere (neg.)",                ex:"どこかに温泉があると聞きました。", exEn:"I heard there's a hot spring somewhere." },
  { id:"g2-11", book:"Genki II · Ch.10", pattern:"で (scope)",              use:"で marks scope for superlatives",                  ex:"日本で一番古いお寺はどこですか。", exEn:"Where is Japan's oldest temple?" },
  { id:"g2-12", book:"Genki II · Ch.11", pattern:"〜たい",                  use:"Want to do X — verb stem + たい",                  ex:"また京都に行きたいです。",         exEn:"I want to go to Kyoto again." },
  { id:"g2-13", book:"Genki II · Ch.11", pattern:"〜たり〜たりする",         use:"Do things like X and Y (non-exhaustive list)",     ex:"旅行中、写真を撮ったり、お土産を買ったりしました。", exEn:"During the trip I did things like taking photos and buying souvenirs." },
  { id:"g2-14", book:"Genki II · Ch.11", pattern:"〜ことがある",            use:"Have experience of X (ever)",                      ex:"新幹線に乗ったことがあります。",   exEn:"I have ridden the Shinkansen before." },
  { id:"g2-15", book:"Genki II · Ch.11", pattern:"noun A や noun B",        use:"A and B, for example (non-exhaustive)",            ex:"京都や奈良に行きました。",         exEn:"I went to places like Kyoto and Nara." },
  { id:"g2-16", book:"Genki II · Ch.12", pattern:"〜んです",                use:"Explanation sentence — explains/contextualizes",   ex:"疲れたんです。昨日たくさん歩いたから。", exEn:"The thing is, I'm tired. I walked a lot yesterday." },
  { id:"g2-17", book:"Genki II · Ch.12", pattern:"〜すぎる",                use:"Too much / too [adj]",                             ex:"歩きすぎて足が痛いです。",         exEn:"I walked too much and my feet hurt." },
  { id:"g2-18", book:"Genki II · Ch.12", pattern:"〜ほうがいいです",        use:"It is better to do X (advice)",                    ex:"早めに宿に戻ったほうがいいですよ。", exEn:"You'd better get back to the inn early." },
  { id:"g2-19", book:"Genki II · Ch.12", pattern:"〜ので",                  use:"Because (formal, written — softer than から)",     ex:"疲れていたので、早めに宿に戻りました。", exEn:"Because I was tired, I returned to the inn early." },
  { id:"g2-20", book:"Genki II · Ch.12", pattern:"〜なければいけません",    use:"Must do X / have to",                              ex:"明日は早起きしなければいけません。", exEn:"I have to wake up early tomorrow." },
  { id:"g2-21", book:"Genki II · Ch.12", pattern:"〜でしょう",              use:"Probably / I suppose — conjecture",                ex:"明日は晴れるでしょう。",           exEn:"It will probably be sunny tomorrow." },
  { id:"g2-22", book:"Genki II · Ch.13", pattern:"Potential Verbs",         use:"Can do X — 〜られる / godan vowel shift + る",      ex:"日本語で少し話せるようになりました。", exEn:"I've become able to speak a little Japanese." },
  { id:"g2-23", book:"Genki II · Ch.13", pattern:"〜し",                    use:"Listing reasons — X し、Y し、so (situation)",      ex:"景色もきれいだし、食べ物も美味しいし、また来たいです。", exEn:"The scenery is beautiful, the food is delicious, I want to come again." },
  { id:"g2-24", book:"Genki II · Ch.13", pattern:"〜そうです (looks like)", use:"It looks like X — based on direct appearance",     ex:"あのラーメン、美味しそうです。",   exEn:"That ramen looks delicious." },
  { id:"g2-25", book:"Genki II · Ch.13", pattern:"〜てみる",                use:"Try doing X tentatively",                          ex:"着物を着てみました。とても楽しかったです。", exEn:"I tried wearing a kimono. It was a lot of fun." },
  { id:"g2-26", book:"Genki II · Ch.13", pattern:"なら (conditional)",      use:"If that's the case / as for X specifically",       ex:"京都に行くなら、早朝に金閣寺を見に行くといいですよ。", exEn:"If you're going to Kyoto, you should go see Kinkakuji early in the morning." },
  { id:"g2-27", book:"Genki II · Ch.13", pattern:"〜週間に〜回",            use:"Frequency — X times per Y period",                 ex:"一週間に二回、日本語の練習をします。", exEn:"I practice Japanese twice a week." },
  { id:"g2-28", book:"Genki II · Ch.14", pattern:"ほしい",                  use:"Want X (thing) — noun が欲しい",                   ex:"旅の記念に、素敵なお土産が欲しいです。", exEn:"I want a nice souvenir as a memento of the trip." },
  { id:"g2-29", book:"Genki II · Ch.14", pattern:"〜かもしれません",        use:"Might be / maybe — possibility",                   ex:"明日は雨が降るかもしれません。",   exEn:"It might rain tomorrow." },
  { id:"g2-30", book:"Genki II · Ch.14", pattern:"あげる・くれる・もらう",  use:"Give away / give to me / receive",                  ex:"地元の方が道を教えてくれました。", exEn:"A local person told me the way." },
  { id:"g2-31", book:"Genki II · Ch.14", pattern:"〜たらどうですか",        use:"How about doing X? (advice/suggestion)",            ex:"疲れたら、少し休んだらどうですか。", exEn:"If you're tired, how about resting a bit?" },
  { id:"g2-32", book:"Genki II · Ch.14", pattern:"number も・number しか",  use:"As many as (も) / only surprisingly few (しか+neg)", ex:"写真を百枚も撮ってしまいました。", exEn:"I ended up taking as many as 100 photos." },
  { id:"g2-33", book:"Genki II · Ch.15", pattern:"Volitional Form",         use:"〜よう / 〜ましょう — let's / I'll do X",           ex:"明日は早起きして、朝の神社を見に行こう。", exEn:"Let's wake up early tomorrow and go see the morning shrine." },
  { id:"g2-34", book:"Genki II · Ch.15", pattern:"Volitional + と思っています", use:"Have already decided to — firm intention",      ex:"来年また日本に来ようと思っています。", exEn:"I've decided I'm going to come to Japan again next year." },
  { id:"g2-35", book:"Genki II · Ch.15", pattern:"〜ておく",                use:"Do in advance / in preparation for something",     ex:"出発前に宿を予約しておきました。", exEn:"I reserved the inn in advance before leaving." },
  { id:"g2-36", book:"Genki II · Ch.15", pattern:"Sentences Qualifying Nouns", use:"Plain form clause + noun (relative clause)",    ex:"昨日食べたラーメンは最高でした。", exEn:"The ramen I ate yesterday was the best." },
  { id:"g2-37", book:"Genki II · Ch.16", pattern:"〜てあげる・くれる・もらう", use:"Do X for someone / someone does X for me",      ex:"ガイドさんが写真を撮ってくれました。", exEn:"The guide took a photo for me." },
  { id:"g2-38", book:"Genki II · Ch.16", pattern:"〜ていただけませんか",    use:"Would you kindly do X? (very polite)",              ex:"もう一度説明していただけませんか。", exEn:"Would you kindly explain it once more?" },
  { id:"g2-39", book:"Genki II · Ch.16", pattern:"〜といい",                use:"I hope X happens (out of speaker's control)",      ex:"明日、天気がいいといいですね。",   exEn:"I hope the weather is good tomorrow." },
  { id:"g2-40", book:"Genki II · Ch.16", pattern:"〜時",                    use:"When A, B — specific past moment",                 ex:"初めて富士山を見た時、感動しました。", exEn:"When I first saw Mt. Fuji, I was deeply moved." },
  { id:"g2-41", book:"Genki II · Ch.16", pattern:"〜てすみませんでした",    use:"I'm sorry for having done X",                      ex:"遅くなってすみませんでした。",     exEn:"I'm sorry for being late." },
  { id:"g2-42", book:"Genki II · Ch.17", pattern:"〜そうです (hearsay)",    use:"I hear that X — reportedly",                       ex:"あのお寺は夜もきれいだそうです。", exEn:"I hear that temple is beautiful at night too." },
  { id:"g2-43", book:"Genki II · Ch.17", pattern:"〜って (informal quote)", use:"Informal reported speech",                         ex:"あの店、予約が必要だって聞きました。", exEn:"I heard that restaurant requires reservations." },
  { id:"g2-44", book:"Genki II · Ch.17", pattern:"〜たら",                  use:"When/if/after X — conditional/sequence",           ex:"京都に着いたら、まず金閣寺に行きました。", exEn:"After arriving in Kyoto, I first went to Kinkakuji." },
  { id:"g2-45", book:"Genki II · Ch.17", pattern:"〜なくてもいいです",      use:"Don't need to do X",                               ex:"予約しなくてもいいと言われました。", exEn:"I was told I didn't need a reservation." },
  { id:"g2-46", book:"Genki II · Ch.17", pattern:"〜みたいです",            use:"Looks like / seems — based on observation",         ex:"あの店、閉まっているみたいです。", exEn:"That shop seems to be closed." },
  { id:"g2-47", book:"Genki II · Ch.17", pattern:"〜前に・〜てから",        use:"Before A (前に) / after doing A (てから)",          ex:"出発する前に、地図を確認しました。", exEn:"I checked the map before setting out." },
  { id:"g2-48", book:"Genki II · Ch.18", pattern:"Transitivity Pairs",      use:"Transitive vs intransitive verb pairs",             ex:"窓が開いています。景色がよく見えます。", exEn:"The window is open. You can see the scenery well." },
  { id:"g2-49", book:"Genki II · Ch.18", pattern:"〜てしまう",              use:"End up doing X / regrettable completion",           ex:"道に迷ってしまいました。",         exEn:"I ended up getting lost." },
  { id:"g2-50", book:"Genki II · Ch.18", pattern:"〜と (automatic result)", use:"Whenever A, automatically B happens",              ex:"この道をまっすぐ行くと、駅に着きます。", exEn:"If you go straight down this road, you'll reach the station." },
  { id:"g2-51", book:"Genki II · Ch.18", pattern:"〜ながら",                use:"Two things at the same time (same subject)",        ex:"音楽を聴きながら、景色を楽しみました。", exEn:"I enjoyed the scenery while listening to music." },
  { id:"g2-52", book:"Genki II · Ch.18", pattern:"〜ばよかったです",        use:"I wish I had done X (regret)",                      ex:"もっと早く来ればよかったです。",   exEn:"I wish I had come earlier." },
  { id:"g2-53", book:"Genki II · Ch.19", pattern:"Honorific Verbs",         use:"Special polite verbs — いらっしゃる、おっしゃる",   ex:"店員さんはとても丁寧にいらっしゃいました。", exEn:"The shop attendant was very polite." },
  { id:"g2-54", book:"Genki II · Ch.19", pattern:"〜てくれてありがとう",    use:"Thank you for doing X",                             ex:"道を教えてくれてありがとうございました。", exEn:"Thank you for telling me the way." },
  { id:"g2-55", book:"Genki II · Ch.19", pattern:"〜てよかったです",        use:"I'm glad that I did X",                             ex:"日本に来てよかったです。",         exEn:"I'm glad I came to Japan." },
  { id:"g2-56", book:"Genki II · Ch.19", pattern:"〜はずです",              use:"It is supposed to be / should logically be X",      ex:"このバスは八時に来るはずです。",   exEn:"This bus should arrive at 8 o'clock." },
  { id:"g2-57", book:"Genki II · Ch.20", pattern:"Extra-modest Expressions", use:"〜ております、〜いたします — very formal",           ex:"お世話になっております。",         exEn:"Thank you for your continued support." },
  { id:"g2-58", book:"Genki II · Ch.20", pattern:"Humble Expressions",      use:"〜させていただく、参る、おる — humble speech",        ex:"写真を撮らせていただけますか。",   exEn:"Would you allow me to take a photo?" },
  { id:"g2-59", book:"Genki II · Ch.20", pattern:"〜ないで",                use:"Without doing X",                                  ex:"地図を使わないで、駅まで歩けました。", exEn:"I was able to walk to the station without using a map." },
  { id:"g2-60", book:"Genki II · Ch.20", pattern:"Questions within Sentences", use:"Embedded question — 〜か + verb / かどうか for yes/no", ex:"何時に出発するか分かりません。", exEn:"I don't know what time we depart." },
  { id:"g2-61", book:"Genki II · Ch.20", pattern:"name という item",        use:"Item called [name]",                               ex:"嵐山という場所がとても好きです。", exEn:"I really like a place called Arashiyama." },
  { id:"g2-62", book:"Genki II · Ch.20", pattern:"〜やすい・にくい",        use:"Easy to do (やすい) / hard to do (にくい)",          ex:"この地図は読みやすいですね。",     exEn:"This map is easy to read." },
  { id:"g2-63", book:"Genki II · Ch.21", pattern:"Passive Sentences",       use:"〜られる — X is done to subject by agent",          ex:"その写真はガイドさんに撮られました。", exEn:"That photo was taken by the guide." },
  { id:"g2-64", book:"Genki II · Ch.21", pattern:"〜てある",                use:"X has been done intentionally and remains so",      ex:"予約がしてありました。",           exEn:"The reservation had been made." },
  { id:"g2-65", book:"Genki II · Ch.21", pattern:"〜間に",                  use:"B takes place while A is ongoing",                 ex:"休憩している間に、雨が上がりました。", exEn:"While I was resting, the rain stopped." },
  { id:"g2-66", book:"Genki II · Ch.21", pattern:"adjective + する",        use:"Make something [adjective] — 〜くする・〜にする",   ex:"部屋を綺麗にしてから、出かけました。", exEn:"After making the room clean, I went out." },
  { id:"g2-67", book:"Genki II · Ch.21", pattern:"〜てほしい",              use:"I want someone to do X for me",                     ex:"もう少しゆっくり話してほしいです。", exEn:"I want you to speak a little more slowly." },
  { id:"g2-68", book:"Genki II · Ch.22", pattern:"Causative Sentences",     use:"〜させる — make/let someone do X",                  ex:"友達を先に行かせました。",         exEn:"I let my friend go first." },
  { id:"g2-69", book:"Genki II · Ch.22", pattern:"verb stem + なさい",      use:"Command (parent/teacher tone)",                     ex:"早く起きなさい、もうすぐ出発ですよ。", exEn:"Get up, we're leaving soon." },
  { id:"g2-70", book:"Genki II · Ch.22", pattern:"〜ば (conditional)",      use:"If A then B — この薬を飲めば大丈夫です",             ex:"晴れれば、富士山が見えるはずです。", exEn:"If it clears up, you should be able to see Mt. Fuji." },
  { id:"g2-71", book:"Genki II · Ch.22", pattern:"〜のに (despite)",        use:"Contrary to expectations — frustration or irony",   ex:"疲れているのに、眠れませんでした。", exEn:"Even though I was tired, I couldn't sleep." },
  { id:"g2-72", book:"Genki II · Ch.22", pattern:"〜のように・のような",    use:"Like A / as if A",                                  ex:"お寺の庭は絵のように美しかったです。", exEn:"The temple garden was beautiful like a painting." },
  { id:"g2-73", book:"Genki II · Ch.23", pattern:"Causative-passive",       use:"〜させられる — be made to do X (against will)",     ex:"長い時間、外で待たされました。",   exEn:"I was made to wait outside for a long time." },
  { id:"g2-74", book:"Genki II · Ch.23", pattern:"〜ても",                  use:"Even if A, B — 雨が降ってもピクニックに行きます",    ex:"雨が降っても、出かけます。",       exEn:"Even if it rains, I will go out." },
  { id:"g2-75", book:"Genki II · Ch.23", pattern:"〜ことにする",            use:"Decide to do X (speaker's active decision)",        ex:"毎日日記を書くことにしました。",   exEn:"I decided to write in my journal every day." },
  { id:"g2-76", book:"Genki II · Ch.23", pattern:"〜まで",                  use:"Until X / up to X",                                 ex:"晴れるまで、カフェで待ちました。", exEn:"I waited at the café until it cleared up." },
  { id:"g2-77", book:"Genki II · Ch.23", pattern:"verb stem + 方",          use:"How to / the way to do X",                          ex:"この漢字の読み方を教えていただけますか。", exEn:"Could you tell me how to read this kanji?" },
  // QUARTET I
  { id:"q1-01", book:"Quartet I · Ch.1", pattern:"N といえば",              use:"Speaking of N / N reminds me of…",                 ex:"京都といえば、やはりお寺ですね。", exEn:"Speaking of Kyoto, it's the temples after all." },
  { id:"q1-02", book:"Quartet I · Ch.1", pattern:"〜なら (conditional)",    use:"If that's the case / as for X specifically",        ex:"京都に行くなら、早朝に金閣寺を見に行くといいですよ。", exEn:"If you're going to Kyoto, you should go see Kinkakuji early." },
  { id:"q1-03", book:"Quartet I · Ch.1", pattern:"〜通り（に）",            use:"Exactly as / in the same way as",                   ex:"地図の通りに歩いたら、お寺に着きました。", exEn:"Walking exactly as the map showed, I arrived at the temple." },
  { id:"q1-04", book:"Quartet I · Ch.1", pattern:"〜らしい",                use:"Apparently (hearsay) OR typical of N",              ex:"あのお寺は夜景がきれいらしいです。", exEn:"Apparently the night view from that temple is beautiful." },
  { id:"q1-05", book:"Quartet I · Ch.1", pattern:"〜ために",                use:"In order to do X / 〜ためのN = N for the purpose of", ex:"写真を撮るために、早起きしました。", exEn:"I woke up early in order to take photos." },
  { id:"q1-06", book:"Quartet I · Ch.1", pattern:"〜がきっかけで",          use:"The trigger / initial reason that led to X",        ex:"友達の話がきっかけで、日本に興味を持ちました。", exEn:"My friend's story was the trigger for my interest in Japan." },
  { id:"q1-07", book:"Quartet I · Ch.1", pattern:"〜ようになる",            use:"Come to do X / gradually began doing X",            ex:"旅行を重ねるうちに、日本語が読めるようになりました。", exEn:"As I traveled more, I came to be able to read Japanese." },
  { id:"q1-08", book:"Quartet I · Ch.1", pattern:"〜ようにする",            use:"Make sure to do X / make an effort to do X",        ex:"旅行中は毎日日記を書くようにしています。", exEn:"I make sure to write in my journal every day during trips." },
  { id:"q1-09", book:"Quartet I · Ch.1", pattern:"N によると",              use:"According to N",                                    ex:"ガイドブックによると、このお寺は世界遺産だそうです。", exEn:"According to the guidebook, this temple is a World Heritage site." },
  { id:"q1-10", book:"Quartet I · Ch.2", pattern:"て-form フォーマルな表現",  use:"Formal て-form — V ます stem / おり for いて / ずに for ないで", ex:"荷物を持ち、電車に乗りました。", exEn:"I took my luggage and boarded the train." },
  { id:"q1-11", book:"Quartet I · Ch.2", pattern:"〜てくる・〜ていく",      use:"Has begun to (くる, usually past) / will begin to (いく)", ex:"旅行を続けるうちに、日本語が上手になってきました。", exEn:"As the trip went on, my Japanese got better and better." },
  { id:"q1-12", book:"Quartet I · Ch.2", pattern:"しか〜ない",              use:"Only (surprisingly small amount)",                  ex:"時間が一時間しかなかったので、急ぎました。", exEn:"There was only one hour, so I hurried." },
  { id:"q1-13", book:"Quartet I · Ch.2", pattern:"〜ことにする・している",  use:"Decide to (ことにする) / make it a rule (ことにしている)", ex:"旅行中は毎日歩くことにしています。", exEn:"I make it a rule to walk every day during trips." },
  { id:"q1-14", book:"Quartet I · Ch.2", pattern:"「気」を使った表現",      use:"気がつく (notice) / 気をつける (be careful) / 気に入る (like)", ex:"その庭がとても気に入りました。また行きたいです。", exEn:"I really took a liking to that garden. I want to go again." },
  { id:"q1-15", book:"Quartet I · Ch.2", pattern:"「おかげ」を使った表現",  use:"Thanks to X — positive result / おかげさまで (set phrase)", ex:"地元の方のおかげで、無事に宿に着きました。", exEn:"Thanks to the local person, I safely reached the inn." },
  { id:"q1-16", book:"Quartet I · Ch.2", pattern:"X ば X ほど Y",           use:"The more X, the more Y",                            ex:"旅行すればするほど、日本が好きになります。", exEn:"The more I travel, the more I love Japan." },
  { id:"q1-17", book:"Quartet I · Ch.2", pattern:"(まるで) N のようだ",     use:"(Just) like N / as if it were N",                   ex:"その庭は、まるで絵のようでした。",  exEn:"The garden was just like a painting." },
  { id:"q1-18", book:"Quartet I · Ch.2", pattern:"〜ことになる・なっている",  use:"It has been decided that (by someone else) / it is expected that (rule/plan)", ex:"明日、奈良に行くことになっています。", exEn:"It's been decided that I'll go to Nara tomorrow." },
  { id:"q1-19", book:"Quartet I · Ch.3", pattern:"〜うちに",                use:"While X is still the case (before it changes)",      ex:"明るいうちに、お寺を見ておきましょう。", exEn:"Let's see the temple while it's still light." },
  { id:"q1-20", book:"Quartet I · Ch.3", pattern:"何と言っても",            use:"No matter what / undeniably / above all else",       ex:"京都の魅力は何と言っても、歴史的な建物ですね。", exEn:"The charm of Kyoto is, no matter what you say, the historical buildings." },
  { id:"q1-21", book:"Quartet I · Ch.3", pattern:"N にとって",              use:"For N / from N's perspective",                      ex:"私にとって、日本旅行は最高の経験でした。", exEn:"For me, the trip to Japan was the best experience." },
  { id:"q1-22", book:"Quartet I · Ch.3", pattern:"N として",                use:"As N / in the capacity of N",                       ex:"観光客として、マナーを守ることが大切です。", exEn:"As a tourist, it's important to observe manners." },
  { id:"q1-23", book:"Quartet I · Ch.3", pattern:"〜ため（に）",            use:"Due to / because of (formal reason)",                ex:"雨のため、外出できませんでした。",  exEn:"Due to the rain, I wasn't able to go out." },
  { id:"q1-24", book:"Quartet I · Ch.3", pattern:"N によって",              use:"Depending on N / by means of N",                    ex:"季節によって、景色が全然違います。", exEn:"Depending on the season, the scenery is completely different." },
  { id:"q1-25", book:"Quartet I · Ch.3", pattern:"〜べきだ・べきではない",  use:"Should / shouldn't (moral or logical opinion)",      ex:"旅行中は、地元のルールを守るべきだと思います。", exEn:"I think you should follow local rules while traveling." },
  { id:"q1-26", book:"Quartet I · Ch.3", pattern:"〜からといって",          use:"Just because X doesn't mean Y",                     ex:"有名だからといって、必ずしも美味しいとは限りません。", exEn:"Just because it's famous doesn't mean it's necessarily delicious." },
  { id:"q1-27", book:"Quartet I · Ch.3", pattern:"〜とは限らない",          use:"It's not always the case that X",                   ex:"人気のお店が、いつも美味しいとは限りません。", exEn:"A popular restaurant isn't always delicious." },
  { id:"q1-28", book:"Quartet I · Ch.3", pattern:"〜のに (purpose)",        use:"For the purpose of / in order to (V dictionary + のに)", ex:"写真を撮るのに、このカメラがとても便利です。", exEn:"This camera is very convenient for taking photos." },
];

// ── PROMPT TEMPLATES (hyper-fixation aware) ───────────────────────────────────
const PROMPT_TEMPLATES = [
  "Write one sentence about a character you've been thinking about lately. Use {pattern}.",
  "Describe something that happened in what you're reading/watching/playing, using {pattern}.",
  "Write one sentence about a place or setting from your current obsession. Use {pattern}.",
  "How does a character you love feel right now? One sentence using {pattern}.",
  "Write one sentence about something you're looking forward to — real or fictional. Use {pattern}.",
  "Describe a moment from whatever you're into lately. Use {pattern} at least once.",
  "Write one sentence about what you did today (or wish you did). Use {pattern}.",
];

// ── STATE ─────────────────────────────────────────────────────────────────────
let currentIdx = 0;
let isDone = false;
let fixation = '';

async function loadState() {
  try {
    const idxRes = await window.storage.get('grammar_idx');
    if (idxRes) currentIdx = parseInt(idxRes.value) || 0;
  } catch(e) { currentIdx = 0; }

  try {
    const doneRes = await window.storage.get('week_done');
    if (doneRes) isDone = doneRes.value === 'true';
  } catch(e) { isDone = false; }

  try {
    const fixRes = await window.storage.get('fixation');
    if (fixRes) fixation = fixRes.value || '';
  } catch(e) { fixation = ''; }

  renderCard();
}

async function saveIdx(idx) {
  try { await window.storage.set('grammar_idx', String(idx)); } catch(e) {}
}

async function saveDone(val) {
  try { await window.storage.set('week_done', String(val)); } catch(e) {}
}

async function saveFixation(val) {
  try { await window.storage.set('fixation', val); } catch(e) {}
}

// ── RENDER ─────────────────────────────────────────────────────────────────────
function renderCard() {
  const point = ALL_POINTS[currentIdx % ALL_POINTS.length];
  const next = ALL_POINTS[(currentIdx + 1) % ALL_POINTS.length];

  document.getElementById('progressLabel').textContent =
    `${currentIdx + 1} of ${ALL_POINTS.length}`;
  document.getElementById('bookLabel').textContent = point.book;
  document.getElementById('patternEl').textContent = point.pattern;
  document.getElementById('useEl').textContent = point.use;
  document.getElementById('exampleJp').textContent = point.ex;
  document.getElementById('exampleEn').textContent = point.exEn;

  // Default prompt
  const templateIdx = currentIdx % PROMPT_TEMPLATES.length;
  const prompt = PROMPT_TEMPLATES[templateIdx].replace('{pattern}', point.pattern);
  document.getElementById('defaultPrompt').innerHTML =
    `<strong>Write one sentence</strong> — ${prompt.replace('Write one sentence — ', '').replace('Write one sentence about', 'about').replace('Write one sentence', '')} Use <em>${point.pattern}</em>.`;

  // Restore fixation input
  if (fixation) document.getElementById('fixationInput').value = fixation;

  // Next preview
  document.getElementById('nextPreview').textContent =
    `Next up: ${next.pattern} (${next.book})`;

  // Show/hide done state
  if (isDone) {
    document.getElementById('mainCard').classList.add('done-mode');
    document.getElementById('doneState').classList.add('visible');
  } else {
    document.getElementById('mainCard').classList.remove('done-mode');
    document.getElementById('doneState').classList.remove('visible');
    document.getElementById('aiPromptResult').classList.remove('visible');
    document.getElementById('aiPromptResult').textContent = '';
    document.getElementById('writeArea').value = '';
  }
}

// ── AI PROMPT GENERATION ──────────────────────────────────────────────────────
async function generatePrompt() {
  const input = document.getElementById('fixationInput').value.trim();
  if (!input) return;

  fixation = input;
  await saveFixation(fixation);

  const point = ALL_POINTS[currentIdx % ALL_POINTS.length];
  const btn = document.getElementById('genBtn');
  btn.disabled = true;
  btn.textContent = '…';

  const aiResult = document.getElementById('aiPromptResult');
  aiResult.classList.remove('visible');

  try {
    const res = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-6',
        max_tokens: 150,
        messages: [{
          role: 'user',
          content: `You are giving a Japanese writing prompt to an N3-level learner. Their current obsession is: "${input}". The grammar point this week is: ${point.pattern} (${point.use}). Write ONE short, specific, fun writing prompt in English that asks them to write ONE Japanese sentence using this grammar point, referencing something from their current obsession. The prompt should feel personal and interesting, not generic. Keep it to 1-2 sentences max. Do not include the Japanese sentence yourself — just the prompt.`
        }]
      })
    });
    const data = await res.json();
    const text = data.content?.map(c => c.text || '').join('') || '';
    if (text) {
      aiResult.textContent = text.trim();
      aiResult.classList.add('visible');
    }
  } catch(e) {
    aiResult.textContent = 'Could not generate — try again.';
    aiResult.classList.add('visible');
  }

  btn.disabled = false;
  btn.textContent = 'tune it →';
}

// ── DONE / UNDO ────────────────────────────────────────────────────────────────
async function markDone() {
  const card = document.getElementById('mainCard');
  card.classList.add('fading');

  await new Promise(r => setTimeout(r, 300));

  // Advance index
  const newIdx = (currentIdx + 1) % ALL_POINTS.length;
  currentIdx = newIdx;
  isDone = true;

  await saveIdx(newIdx);
  await saveDone(true);

  card.classList.remove('fading');
  renderCard();
}

async function undoDone() {
  // Step back one
  currentIdx = Math.max(0, currentIdx - 1);
  isDone = false;
  await saveIdx(currentIdx);
  await saveDone(false);
  renderCard();
}

// ── RESET ─────────────────────────────────────────────────────────────────────
async function confirmReset() {
  if (!confirm('Reset all progress back to point 1?')) return;
  currentIdx = 0;
  isDone = false;
  await saveIdx(0);
  await saveDone(false);
  renderCard();
}

// ── INIT ──────────────────────────────────────────────────────────────────────
loadState();
</script>

</body>
</html>
