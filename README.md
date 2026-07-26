<!DOCTYPE html>
<html lang="ur-Latn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SEO Audit Log — 125 Issues Resolved</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0E1113;
    --panel:#171B1E;
    --panel2:#1D2226;
    --border:#262B2F;
    --border-soft:#1F2427;
    --text:#ECE9E1;
    --text-dim:#9BA0A6;
    --text-faint:#5C6266;

    --c-meta:#E8B23D;
    --c-heading:#4FB8A6;
    --c-content:#E2673F;
    --c-linking:#6C8CE8;
    --c-media:#C77DE0;
    --c-url:#7FCB5B;
    --c-schema:#E85B8A;
  }

  *{box-sizing:border-box; margin:0; padding:0;}

  html{scroll-behavior:smooth;}

  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Inter', sans-serif;
    line-height:1.5;
    -webkit-font-smoothing:antialiased;
    padding-bottom:80px;
  }

  ::selection{ background:#3a3f2a; color:#fff; }

  a{color:inherit;}

  .noise{
    position:fixed; inset:0; pointer-events:none; opacity:.035; z-index:0;
    background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  }

  /* ---------- HERO ---------- */
  header.hero{
    position:relative;
    padding:64px 24px 40px;
    max-width:1180px;
    margin:0 auto;
    border-bottom:1px solid var(--border);
  }

  .eyebrow{
    font-family:'JetBrains Mono', monospace;
    font-size:12px;
    letter-spacing:.14em;
    text-transform:uppercase;
    color:var(--text-faint);
    display:flex;
    align-items:center;
    gap:10px;
    margin-bottom:22px;
  }
  .eyebrow .dot{width:6px; height:6px; border-radius:50%; background:#7FCB5B; box-shadow:0 0 8px #7FCB5B;}

  h1.title{
    font-family:'Space Grotesk', sans-serif;
    font-weight:700;
    font-size:clamp(34px, 5.2vw, 62px);
    letter-spacing:-0.02em;
    line-height:1.04;
    max-width:820px;
  }

  .title .accent{
    background:linear-gradient(90deg, var(--c-content), var(--c-schema));
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
  }

  p.subtitle{
    margin-top:18px;
    max-width:640px;
    color:var(--text-dim);
    font-size:16px;
  }
  p.subtitle b{ color:var(--text); font-weight:600; }

  /* stat strip */
  .stat-strip{
    display:flex;
    gap:0;
    margin-top:40px;
    border:1px solid var(--border);
    border-radius:10px;
    overflow:hidden;
    flex-wrap:wrap;
  }
  .stat{
    flex:1 1 140px;
    padding:18px 20px;
    border-right:1px solid var(--border);
    background:var(--panel);
  }
  .stat:last-child{border-right:none;}
  .stat .num{
    font-family:'Space Grotesk', sans-serif;
    font-weight:700;
    font-size:26px;
  }
  .stat .lbl{
    font-family:'JetBrains Mono', monospace;
    font-size:10.5px;
    letter-spacing:.08em;
    text-transform:uppercase;
    color:var(--text-faint);
    margin-top:4px;
  }

  /* ---------- CONTROLS ---------- */
  .controls{
    position:sticky;
    top:0;
    z-index:20;
    backdrop-filter:blur(14px);
    background:rgba(14,17,19,0.86);
    border-bottom:1px solid var(--border);
    padding:16px 24px;
  }
  .controls-inner{
    max-width:1180px;
    margin:0 auto;
    display:flex;
    gap:14px;
    align-items:center;
    flex-wrap:wrap;
  }

  #search{
    flex:1 1 220px;
    background:var(--panel);
    border:1px solid var(--border);
    color:var(--text);
    font-family:'Inter', sans-serif;
    font-size:14px;
    padding:11px 14px 11px 38px;
    border-radius:8px;
    outline:none;
    background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='none' stroke='%239BA0A6' stroke-width='1.6'%3E%3Ccircle cx='6.7' cy='6.7' r='5'/%3E%3Cline x1='10.5' y1='10.5' x2='15' y2='15'/%3E%3C/svg%3E");
    background-repeat:no-repeat;
    background-position:12px center;
    transition:border-color .15s;
  }
  #search:focus{ border-color:var(--text-faint); }
  #search::placeholder{ color:var(--text-faint); }

  .chips{
    display:flex;
    gap:8px;
    flex-wrap:wrap;
  }
  .chip{
    font-family:'JetBrains Mono', monospace;
    font-size:11.5px;
    letter-spacing:.02em;
    display:flex;
    align-items:center;
    gap:7px;
    padding:8px 12px;
    border-radius:20px;
    border:1px solid var(--border);
    background:var(--panel);
    color:var(--text-dim);
    cursor:pointer;
    user-select:none;
    transition:all .15s;
    white-space:nowrap;
  }
  .chip .swatch{ width:8px; height:8px; border-radius:50%; }
  .chip:hover{ border-color:var(--text-faint); color:var(--text); }
  .chip.active{
    background:var(--cat-color, #333);
    color:#0E1113;
    border-color:var(--cat-color, #333);
    font-weight:600;
  }
  .chip.active .swatch{ background:#0E1113; }

  .count-live{
    font-family:'JetBrains Mono', monospace;
    font-size:12px;
    color:var(--text-faint);
    margin-left:auto;
    white-space:nowrap;
  }

  /* ---------- SECTIONS ---------- */
  main{ max-width:1180px; margin:0 auto; padding:0 24px; position:relative; z-index:1;}

  .cat-section{ margin-top:52px; }

  .cat-head{
    display:flex;
    align-items:baseline;
    gap:14px;
    padding-bottom:14px;
    border-bottom:2px solid var(--cat-color);
    margin-bottom:22px;
  }
  .cat-head .range{
    font-family:'JetBrains Mono', monospace;
    font-size:12px;
    color:var(--cat-color);
    background:color-mix(in srgb, var(--cat-color) 14%, transparent);
    padding:4px 9px;
    border-radius:5px;
    font-weight:600;
  }
  .cat-head h2{
    font-family:'Space Grotesk', sans-serif;
    font-size:22px;
    font-weight:600;
  }
  .cat-head .cat-count{
    font-family:'JetBrains Mono', monospace;
    font-size:12px;
    color:var(--text-faint);
    margin-left:auto;
  }

  .card-grid{
    display:grid;
    grid-template-columns:repeat(auto-fill, minmax(330px, 1fr));
    gap:14px;
  }

  .card{
    background:var(--panel);
    border:1px solid var(--border);
    border-left:3px solid var(--cat-color);
    border-radius:8px;
    padding:16px 18px 17px;
    transition:transform .12s ease, border-color .12s ease, background .12s ease;
  }
  .card:hover{
    transform:translateY(-2px);
    background:var(--panel2);
    border-color:var(--border-soft);
    border-left-color:var(--cat-color);
  }

  .card-top{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:8px;
  }
  .ticket-id{
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    color:var(--cat-color);
    font-weight:600;
    letter-spacing:.03em;
  }
  .status{
    font-family:'JetBrains Mono', monospace;
    font-size:9.5px;
    letter-spacing:.08em;
    color:#7FCB5B;
    display:flex;
    align-items:center;
    gap:4px;
  }
  .status::before{ content:"✓"; font-size:10px; }

  .card h3{
    font-family:'Space Grotesk', sans-serif;
    font-size:15px;
    font-weight:600;
    line-height:1.32;
    margin-bottom:11px;
    color:var(--text);
  }

  .row{ display:flex; gap:8px; margin-top:7px; }
  .row .tag{
    font-family:'JetBrains Mono', monospace;
    font-size:9.5px;
    letter-spacing:.09em;
    color:var(--text-faint);
    flex:0 0 auto;
    padding-top:2px;
    min-width:44px;
  }
  .row.fix .tag{ color:var(--cat-color); }
  .row p{
    font-size:13px;
    color:var(--text-dim);
    line-height:1.45;
  }
  .row.fix p{ color:#c9cdd1; }

  .no-results{
    text-align:center;
    padding:60px 20px;
    color:var(--text-faint);
    font-family:'JetBrains Mono', monospace;
    font-size:13px;
    display:none;
  }

  footer{
    max-width:1180px;
    margin:70px auto 0;
    padding:24px 24px 0;
    border-top:1px solid var(--border);
    color:var(--text-faint);
    font-size:12.5px;
    font-family:'JetBrains Mono', monospace;
    display:flex;
    justify-content:space-between;
    flex-wrap:wrap;
    gap:8px;
  }

  @media (max-width:640px){
    header.hero{padding:44px 18px 30px;}
    .controls{padding:12px 16px;}
    main{padding:0 16px;}
    .cat-head{flex-wrap:wrap;}
    .cat-head .cat-count{ margin-left:0; }
  }

  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    .card{transition:none;}
  }
</style>
</head>
<body>

<div class="noise"></div>

<header class="hero">
  <div class="eyebrow"><span class="dot"></span> ON-PAGE SEO · CLOSED TICKET LOG</div>
  <h1 class="title">125 issues found.<br><span class="accent">125 issues fixed.</span></h1>
  <p class="subtitle">Pichle <b>3 saal</b> mein har live audit ke dauran flag hone wale on-page SEO masail ka pura record — Title &amp; Meta se le kar Schema tak, har entry apni <b>problem</b> aur apply ki gayi <b>solution</b> ke saath.</p>

  <div class="stat-strip">
    <div class="stat"><div class="num">125</div><div class="lbl">Total Issues</div></div>
    <div class="stat"><div class="num">7</div><div class="lbl">Categories</div></div>
    <div class="stat"><div class="num">3</div><div class="lbl">Years Covered</div></div>
    <div class="stat"><div class="num">100%</div><div class="lbl">Resolved</div></div>
  </div>
</header>

<div class="controls">
  <div class="controls-inner">
    <input id="search" type="text" placeholder="Issue, problem ya solution search karein…">
    <div class="chips" id="chips"></div>
    <div class="count-live" id="liveCount"></div>
  </div>
</div>

<main id="main"></main>

<div class="no-results" id="noResults">— koi matching issue nahi mila —</div>

<footer>
  <span>SEO AUDIT LOG · PART 1 OF 2 · ON-PAGE</span>
  <span>NEXT: OFF-PAGE SEO (125 ISSUES)</span>
</footer>

<script>
const categories = [
  {id:'meta',    name:'Title &amp; Meta Tags',            range:'01–15',  color:'var(--c-meta)'},
  {id:'heading', name:'Heading Tags Structure',            range:'16–30',  color:'var(--c-heading)'},
  {id:'content', name:'Content Quality &amp; Keywords',    range:'31–55',  color:'var(--c-content)'},
  {id:'linking', name:'Internal Linking &amp; Navigation', range:'56–75',  color:'var(--c-linking)'},
  {id:'media',   name:'Images &amp; Multimedia',           range:'76–95',  color:'var(--c-media)'},
  {id:'url',     name:'URL Structure &amp; Canonicalization', range:'96–110', color:'var(--c-url)'},
  {id:'schema',  name:'Schema &amp; Structured Data',      range:'111–125', color:'var(--c-schema)'}
];

const issues = [
{c:'meta',t:'Missing Primary Title Tag',p:'Search engines page ka topic identify nahi kar pa rahe the.',s:'Target keyword ke sath natural Title tag implement kiya.'},
{c:'meta',t:'Title Tag Exceeds Pixel Width (>600px)',p:'Search results mein title cut (truncate) ho raha tha.',s:'Titles ko 50–60 characters (580px) ke andar condense kiya.'},
{c:'meta',t:'Title Tag Too Short',p:'Context kam hone ki wajah se low CTR tha.',s:'Secondary keywords aur brand name add karke length optimize ki.'},
{c:'meta',t:'Duplicate Title Tags Across Pages',p:'Canonical confusion paida ho rahi thi.',s:'Har page ke liye unique, intent-driven titles assign kiye.'},
{c:'meta',t:'Title Keyword Stuffing',p:'Penalty ka risk tha.',s:'Natural language aur single primary keyword focus banaya.'},
{c:'meta',t:'Missing Meta Description',p:'Google random page snippets pick kar raha tha.',s:'High-converting 155-character meta descriptions compose kiye.'},
{c:'meta',t:'Duplicate Meta Descriptions',p:'Search visibility split ho rahi thi.',s:'Dynamic / unique meta templates set kiye.'},
{c:'meta',t:'Meta Description Too Long',p:'Search snippets mein truncated text show ho raha tha.',s:'Summary ko 150–160 characters mein fit kiya.'},
{c:'meta',t:'Missing Call-To-Action in Meta',p:'Organic Click-Through Rate (CTR) low tha.',s:'Meta mein "Get Quote", "Learn More" jaisi CTAs add kiye.'},
{c:'meta',t:'Meta Keywords Tag Present',p:'Deprecated tag jo competitor ko intelligence deta hai.',s:'HTML header se Meta Keywords tag remove kiya.'},
{c:'meta',t:'Page Title Matches H1 Exactly',p:'Variety aur semantic richness missing thi.',s:'Title tag aur H1 tag ko slightly vary karke secondary search intent wrap kiya.'},
{c:'meta',t:'Non-Localized Title Tags',p:'Local search queries par rank nahi kar raha tha.',s:'Title mein City/State modifiers add kiye.'},
{c:'meta',t:'Brand Name Missing in Titles',p:'Brand authority build nahi ho rahi thi.',s:'Title ke end par | Brand Name append kiya.'},
{c:'meta',t:'Title Tag Starts with Generic Words',p:'Primary keyword ki prominence kam thi.',s:'Front-load technique se main keyword ko start mein shift kiya.'},
{c:'meta',t:'Special Characters Breaking Titles',p:'Browsers mein HTML entities corrupt show ho rahi thin.',s:'Encodings UTF-8 par fix kiye.'},

{c:'heading',t:'Missing H1 Tag',p:'Search engine main heading detect nahi kar pa raha tha.',s:'Page par exact 1 unique H1 tag deploy kiya.'},
{c:'heading',t:'Multiple H1 Tags on Single Page',p:'Topical focus confuse ho raha tha.',s:'Secondary H1s ko H2 mein convert kiya.'},
{c:'heading',t:'Skipped Heading Levels (e.g., H1 to H3)',p:'Document outline structure broken tha.',s:'Hierarchical flow (H1 → H2 → H3) restore kiya.'},
{c:'heading',t:'H1 Tag Hidden via CSS (display:none)',p:'Black-hat signal lag raha tha.',s:'Hidden CSS classes remove karke visible structure banaya.'},
{c:'heading',t:'Empty Heading Tags (&lt;h2&gt;&lt;/h2&gt;)',p:'Clean HTML validation fail ho rahi thi.',s:'Code audit karke empty DOM nodes delete kiye.'},
{c:'heading',t:'Heading Tags Used for Styling/Font Size',p:'Semantics ruin ho rahe the.',s:'Styling CSS mein move ki aur heading tags ko content structure ke liye reserve kiya.'},
{c:'heading',t:'H2 Tags Missing Focus Keywords',p:'Sub-topics optimize nahi the.',s:'LSI aur semantic variants ko H2 tags mein blend kiya.'},
{c:'heading',t:'Non-Descriptive Headings (e.g., "Details")',p:'User aur bot dono ke liye zero context tha.',s:'Clear, informative sub-headings craft kiye.'},
{c:'heading',t:'H1 Tag Enclosed in Image',p:'Text content read nahi ho raha tha.',s:'Image ko proper HTML text element se replace kiya.'},
{c:'heading',t:'Too Many H2 Tags (>20 per article)',p:'Content over-fragmented tha.',s:'Logical sections merge kiye.'},
{c:'heading',t:'H3/H4 Tags Missing in Long Content',p:'Reading experience poor tha.',s:'Scannability ke liye multi-tier headings add kiye.'},
{c:'heading',t:'Anchor Links Missing in H2s',p:'Jump-links work nahi kar rahe the.',s:'Table of Contents ke liye H2 IDs assign kiye.'},
{c:'heading',t:'H1 Tag Placement Below the Fold',p:'Core relevance detect hone mein delay tha.',s:'H1 ko hero section (above-the-fold) shift kiya.'},
{c:'heading',t:'Generic Subheadings in Service Pages',p:'Context weak tha.',s:'Keyword-enriched service headings write kiye.'},
{c:'heading',t:'Duplicated Headings Across Sections',p:'Content repetitive lag raha tha.',s:'Unique phrasing implement ki.'},

{c:'content',t:'Keyword Cannibalization',p:'Multiple pages same target term ke liye fighting kar rahe the.',s:'Pages merge kiye aur 301 redirect / canonical set kiya.'},
{c:'content',t:'Thin Content (&lt;300 words)',p:'Indexability drop ho rahi thi.',s:'Comprehensive depth ke sath 1200+ words target page update kiya.'},
{c:'content',t:'Duplicate Content (Internal)',p:'URL parameters ki wajah se duplicate versions indexing ho rahe the.',s:'Self-referential canonical tags deploy kiye.'},
{c:'content',t:'Keyword Stuffing (>4% Density)',p:'Spam penalty score rise kar raha tha.',s:'Keyword density 1.5% tak la kar natural synonyms add kiye.'},
{c:'content',t:'Low Topical Authority',p:'Core entity coverage weak thi.',s:'Entity-based semantic content clusters create kiye.'},
{c:'content',t:'Outdated Content',p:'Information old hone se rankings drop hui thin.',s:'Current year facts, stats aur fresh data inject kiya.'},
{c:'content',t:'High Readability Grade Level',p:'Target audience ko content complex lag raha tha.',s:'Readability score improve karke Grade 7-8 level par laya.'},
{c:'content',t:'Unformatted Content Blocks (Wall of Text)',p:'High bounce rate tha.',s:'Bullet points, bold texts aur short paragraphs add kiye.'},
{c:'content',t:'Missing Target Keyword in First 100 Words',p:'Topic confirmation slow tha.',s:'Introduction paragraph mein seed keyword inject kiya.'},
{c:'content',t:'AI-Generated Spam Content',p:'Generic text index nahi ho raha tha.',s:'Human editorial pass, expert insights (E-E-A-T) aur custom visuals add kiye.'},
{c:'content',t:'Lack of Original Media',p:'Stock images search value destroy kar rahi thin.',s:'Custom infographics aur screenshots publish kiye.'},
{c:'content',t:'Search Intent Mismatch',p:'Transactional keyword par informational content rank karne ki koshish thi.',s:'Page layout ko product/service booking design mein rewrite kiya.'},
{c:'content',t:'Missing Author Byline (E-E-A-T issue)',p:'Trust score low tha.',s:'Verified author bio with social links attach kiya.'},
{c:'content',t:'No Table of Contents (ToC)',p:'Long-form content browse karna mushkil tha.',s:'Dynamic ToC plugin / script integrate kiya.'},
{c:'content',t:'Plagiarized Content Sections',p:'Web syndication issue tha.',s:'Content re-write karke 100% original copy ensure ki.'},
{c:'content',t:'Grammatical &amp; Spelling Errors',p:'Professional perception ruin ho raha tha.',s:'Proofreading tools se full site audit and cleanup kiya.'},
{c:'content',t:'Lack of LSI / NLP Keywords',p:'Search engine context capture nahi kar raha tha.',s:'SurferSEO/TF-IDF tools se NLP entities integrate kiye.'},
{c:'content',t:'Poor Call-to-Action (CTA) Placement',p:'Low conversions.',s:'Sticky aur mid-content CTA buttons insert kiye.'},
{c:'content',t:'Too Many Affiliate Links Above the Fold',p:'Ad-heavy penalization threat tha.',s:'Affiliate links ko balance kiya aur disclosure note top par add kiya.'},
{c:'content',t:'Missing FAQ Section',p:'Long-tail voice queries miss ho rahi thin.',s:'Accordion-style FAQ section page footer par design kiya.'},
{c:'content',t:'Duplicate H1/Title across Paginated Pages',p:'Pagination issues.',s:'Title mein "Page X of Y" pattern append kiya.'},
{c:'content',t:'Commercial Keywords on Informational Blog',p:'Bounce rate surge.',s:'Intent shift karke blog ko guide format diya aur service page link kiya.'},
{c:'content',t:'Text-To-HTML Ratio Low (&lt;10%)',p:'Excess DOM elements, low content.',s:'Bloated code clean karke text volume increase kiya.'},
{c:'content',t:'Un-targeted Geo-Keywords',p:'Local relevance drop.',s:'Service area localized keywords naturally weave kiye.'},
{c:'content',t:'Broken Embeds (YouTube / Maps)',p:'Poor UX.',s:'Updated iFrame sources fix kiye.'},

{c:'linking',t:'Orphan Pages',p:'Main site navigation se links isolated the.',s:'Category aur related blog posts se internal links connect kiye.'},
{c:'linking',t:'Generic Anchor Text (e.g., "Click Here")',p:'Keyword relevancy pass nahi ho rahi thi.',s:'Descriptive, keyword-rich anchor text update kiya.'},
{c:'linking',t:'Broken Internal Links (404 Errors)',p:'Crawl budget waste ho raha tha.',s:'Screaming Frog audit karke redirects / dead links update kiye.'},
{c:'linking',t:'Deep Link Depth (>4 Clicks from Home)',p:'Crawlers deep pages skip kar rahe the.',s:'Site architecture flat ki (3 clicks maximum).'},
{c:'linking',t:'Nofollow Tags on Internal Links',p:'Link equity flow block ho rahi thi.',s:'Internal links se rel="nofollow" attributes remove kiye.'},
{c:'linking',t:'Excessive Internal Links (>100 per page)',p:'Link juice dilute ho raha tha.',s:'Links prune karke contextual priority links rakhe.'},
{c:'linking',t:'Missing Breadcrumb Navigation',p:'User site location track nahi kar pa raha tha.',s:'Schema-supported breadcrumb trail implement kiya.'},
{c:'linking',t:'Links Opening in Wrong Target Tabs',p:'Navigat
