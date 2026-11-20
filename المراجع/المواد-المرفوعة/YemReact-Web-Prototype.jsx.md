import { useState, useRef } from "react";
import { Search, Bookmark, BookmarkCheck, Download, Play, ChevronRight, Check } from "lucide-react";

/* ============================================================
   DESIGN TOKENS — YemReact Brand v1.0 LOCKED. Do not add/change.
   ============================================================ */
const T = {
  ink: "#121214", ink2: "#1a1a1d", ink3: "#232327",
  amber: "#c1592e", amberLight: "#e0824b",
  paper: "#f3eae0", paperDim: "#c9bfb4",
  coral: "#ff5a36", grey: "#6b625c", greyLight: "#9c9289",
};

/* ============================================================
   CATEGORIES — the 9 locked categories. Edit labels only if a
   category name changes; never add/remove/recolor here.
   ============================================================ */
const CATEGORIES = [
  { id: "laugh", name: "ضحك", color: "#f4c430" },
  { id: "shock", name: "صدمة", color: "#7c5cff" },
  { id: "anger", name: "غضب", color: "#c81e3a" },
  { id: "surprise", name: "استغراب", color: "#2cb6c4" },
  { id: "embarrass", name: "إحراج/صمت", color: "#f17fb2" },
  { id: "approve", name: "موافقة", color: "#4caf6d" },
  { id: "reject", name: "رفض", color: "#6e8296" },
  { id: "sarcasm", name: "سخرية", color: "#d98e04" },
  { id: "hype", name: "حماس", color: "#e8712e" },
];
const catById = Object.fromEntries(CATEGORIES.map((c) => [c.id, c]));

const SITUATIONS = [
  "لما واحد يكذب عليك",
  "لما تسمع خبر صادم",
  "لما صاحبك يقول بكرة",
  "لما حد يهرّجك بموقف",
  "لما تشوف شي ما تصدق عيونك",
];

/* ============================================================
   MOCK REACTIONS — edit/add items here. All preview media is a
   placeholder (no real clips in this prototype, no external
   images/video — per spec, nothing is faked as "real content").
   Shape: id, title, category, duration(s), description, tags[], corner
   ============================================================ */
const REACTIONS = [
  { id: "YR-0001", title: "يا ساتر!",            category: "shock",     duration: 2, description: "لما تسمع خبر صادم",              tags: ["صدمة", "خبر", "مفاجأة"], corner: "tr" },
  { id: "YR-0002", title: "عاد شي عقل؟",          category: "reject",    duration: 3, description: "لما حد يقولك كلام مالوش داعي",   tags: ["رفض", "كلام", "رد"],     corner: "tl" },
  { id: "YR-0003", title: "قوية... قوية جدًا",     category: "sarcasm",   duration: 5, description: "لما حد يسولف عليك",              tags: ["سخرية", "تعليق"],        corner: "tr" },
  { id: "YR-0004", title: "قوية!",                category: "hype",      duration: 3, description: "لما فريقك يسجل هدف",             tags: ["حماس", "فرح"],           corner: "tl" },
  { id: "YR-0005", title: "صلّي على النبي",       category: "surprise",  duration: 4, description: "لما تشوف شي ما تصدق عيونك",      tags: ["استغراب", "انبهار"],     corner: "tr" },
  { id: "YR-0006", title: "ياخي وربي",            category: "laugh",     duration: 3, description: "لما صاحبك يقع بموقف محرج",       tags: ["ضحك", "موقف"],           corner: "tr" },
  { id: "YR-0007", title: "...",                  category: "embarrass", duration: 4, description: "لما ما تلقى رد على كلامك",       tags: ["إحراج", "صمت"],          corner: "tr" },
  { id: "YR-0008", title: "برضه؟",                category: "reject",    duration: 3, description: "لما صاحبك يقول بكرة أسددلك",     tags: ["رفض", "مماطلة"],         corner: "tr" },
  { id: "YR-0009", title: "معك حق",               category: "approve",   duration: 2, description: "لما حد يقنعك بفكرة",             tags: ["موافقة"],                corner: "tr" },
  { id: "YR-0010", title: "كفاية!",               category: "anger",     duration: 3, description: "لما حد يضيّع وقتك",              tags: ["غضب"],                   corner: "tr" },
  { id: "YR-0011", title: "بس بس بس",             category: "laugh",     duration: 3, description: "لما واحد يمزح وما يوقف",         tags: ["ضحك"],                   corner: "tr" },
  { id: "YR-0012", title: "يووه!",                category: "hype",      duration: 2, description: "لما تسمع خبر مفرحك",             tags: ["حماس", "فرح"],           corner: "tr" },
];

/* ============================================================
   BRAND COMPONENTS — reused everywhere. Same path/geometry as
   Brand v1.0 LOCKED. Do not redraw.
   ============================================================ */
function QusasaMark({ size = 28, fill = T.amber, outline = false }) {
  return (
    <svg width={size} height={size} viewBox="0 0 120 120" style={{ display: "block", flexShrink: 0 }}>
      <path
        fill={outline ? "none" : fill}
        stroke={outline ? fill : "none"}
        strokeWidth={outline ? 7 : 0}
        fillRule="evenodd"
        d="M10,0 L86,0 L92,6 L98,1 L104,7 L110,3 L120,14 L120,106 L106,120 L14,120 L0,106 L0,10 Z M46,38 L46,82 L82,60 Z"
      />
    </svg>
  );
}

function TornFrame({ children, size = "lg", style = {} }) {
  return (
    <div className={size === "lg" ? "torn-lg" : "torn-sm"} style={{ position: "relative", overflow: "hidden", ...style }}>
      {children}
    </div>
  );
}

function PeelMark({ corner = "tr" }) {
  return (
    <div className={`peel ${corner === "tr" ? "peel-tr" : "peel-tl"}`}>
      <QusasaMark size={12} fill={T.ink} />
    </div>
  );
}

function DurationTag({ dur, corner = "tr" }) {
  const side = corner === "tr" ? "left" : "right";
  return <div className={`dur-tag mono ${side}`}>{dur}s</div>;
}

function CategoryDot({ cat, corner = "tr" }) {
  const side = corner === "tr" ? "left" : "right";
  return <div className={`cat-dot ${side}`} style={{ background: catById[cat].color }} />;
}

function ClipStage({ reaction, children }) {
  // Placeholder only — stands in for the real video frame. Labeled so it's
  // never mistaken for an actual clip.
  return (
    <div className="clip-stage">
      <PeelMark corner={reaction.corner} />
      <DurationTag dur={reaction.duration} corner={reaction.corner} />
      <CategoryDot cat={reaction.category} corner={reaction.corner} />
      <div className="mock-label mono">لقطة تجريبية</div>
      {children}
    </div>
  );
}

/* ============================================================
   CARDS
   ============================================================ */
function ReactionCard({ reaction, index, saved, onToggleSave, onOpen }) {
  const cat = catById[reaction.category];
  return (
    <div className="card-enter" style={{ animationDelay: `${index * 40}ms` }}>
      <TornFrame size="lg" style={{ cursor: "pointer" }}>
        <div onClick={() => onOpen(reaction.id)}>
          <ClipStage reaction={reaction}>
            <div className="play-veil">
              <Play size={22} color={T.paper} fill={T.paper} />
            </div>
          </ClipStage>
        </div>
      </TornFrame>
      <div className="card-meta">
        <div className="card-meta-top">
          <span className="cat-label" style={{ color: cat.color }}>{cat.name}</span>
          <button className="save-btn" onClick={() => onToggleSave(reaction.id)} aria-label="حفظ">
            {saved ? <BookmarkCheck size={16} color={T.amberLight} /> : <Bookmark size={16} color={T.greyLight} />}
          </button>
        </div>
        <div className="quote-line">{reaction.title}</div>
      </div>
    </div>
  );
}

function MiniCard({ reaction, onOpen }) {
  const cat = catById[reaction.category];
  return (
    <div className="mini-card" onClick={() => onOpen(reaction.id)}>
      <TornFrame size="sm" style={{ cursor: "pointer" }}>
        <ClipStage reaction={reaction} />
      </TornFrame>
      <div className="mini-quote" style={{ color: cat.color }}>{reaction.title}</div>
    </div>
  );
}

/* ============================================================
   VIEWS
   ============================================================ */
function Header({ onSearchIconClick }) {
  return (
    <div className="header">
      <div className="header-brand">
        <QusasaMark size={26} />
        <span className="header-word">يمن رياكت</span>
      </div>
      <button className="header-search-btn" onClick={onSearchIconClick} aria-label="بحث">
        <Search size={18} color={T.greyLight} />
      </button>
    </div>
  );
}

function Home({ query, setQuery, activeCat, setActiveCat, saved, onToggleSave, onOpen, searchRef }) {
  const filtered = REACTIONS.filter((r) => {
    const matchesCat = !activeCat || r.category === activeCat;
    const q = query.trim();
    const matchesQuery =
      !q ||
      r.description.includes(q) ||
      r.title.includes(q) ||
      r.tags.some((t) => t.includes(q)) ||
      catById[r.category].name.includes(q);
    return matchesCat && matchesQuery;
  });

  return (
    <div className="view-enter">
      <div className="hero">
        <h1 className="hero-h1">رياكشنات يمنية<br />تتكلم بلسانك</h1>
        <p className="hero-sub">مكتبة رياكشنات يمنية قصيرة ونادرة، منتقاة من مواقف حقيقية — خذها. حطها. يمنية.</p>

        <div className="search-box">
          <Search size={17} color={T.greyLight} />
          <input
            ref={searchRef}
            className="search-input"
            placeholder="دوّر على الموقف..."
            value={query}
            onChange={(e) => setQuery(e.target.value)}
          />
        </div>

        <div className="chip-row">
          {SITUATIONS.map((s) => (
            <button key={s} className="chip" onClick={() => setQuery(s)}>{s}</button>
          ))}
        </div>
      </div>

      <div className="cat-rail">
        <button className={`cat-pill ${!activeCat ? "active" : ""}`} style={{ "--pc": T.paper }} onClick={() => setActiveCat(null)}>الكل</button>
        {CATEGORIES.map((c) => (
          <button
            key={c.id}
            className={`cat-pill ${activeCat === c.id ? "active" : ""}`}
            style={{ "--pc": c.color }}
            onClick={() => setActiveCat(activeCat === c.id ? null : c.id)}
          >
            {c.name}
          </button>
        ))}
      </div>

      {filtered.length === 0 ? (
        <div className="empty-state">مافي رياكشن يطابق البحث... جرّب كلمة ثانية.</div>
      ) : (
        <div className="grid" key={activeCat + "|" + query}>
          {filtered.map((r, i) => (
            <ReactionCard key={r.id} reaction={r} index={i} saved={saved.has(r.id)} onToggleSave={onToggleSave} onOpen={onOpen} />
          ))}
        </div>
      )}
    </div>
  );
}

function ReactionDetail({ reaction, saved, onToggleSave, onBack, onOpen }) {
  const [downloading, setDownloading] = useState(false);
  const [done, setDone] = useState(false);
  const cat = catById[reaction.category];
  const related = REACTIONS.filter((r) => r.category === reaction.category && r.id !== reaction.id).slice(0, 5);

  function handleUse() {
    if (downloading || done) return;
    setDownloading(true);
    setTimeout(() => {
      setDownloading(false);
      setDone(true);
      setTimeout(() => setDone(false), 1600);
    }, 900);
  }

  return (
    <div className="view-enter">
      <button className="back-btn" onClick={onBack}>
        <ChevronRight size={16} />
        رجوع
      </button>

      <div className="detail-layout">
        <TornFrame size="lg" style={{ width: "min(320px, 100%)", aspectRatio: "9/16", margin: "0 auto" }}>
          <ClipStage reaction={reaction}>
            <div className="play-veil static">
              <Play size={26} color={T.paper} fill={T.paper} />
            </div>
          </ClipStage>
        </TornFrame>

        <div className="detail-meta">
          <span className="cat-label lg" style={{ color: cat.color }}>{cat.name}</span>
          <div className="situation">{reaction.description}</div>
          <div className="quote-big">{reaction.title}</div>
          <div className="rid mono">{reaction.id}</div>
          <div className="tag-row">
            {reaction.tags.map((t) => <span key={t} className="tag-pill">{t}</span>)}
          </div>

          <div className="action-row">
            <button className="btn-primary" onClick={handleUse}>
              {done ? <><Check size={16} /> جاهزة</> : downloading ? "جاري التجهيز..." : <><Download size={16} /> خذها</>}
            </button>
            <button className="btn-secondary" onClick={() => onToggleSave(reaction.id)}>
              {saved ? <BookmarkCheck size={16} color={T.amberLight} /> : <Bookmark size={16} />}
              {saved ? "محفوظة" : "احفظها"}
            </button>
          </div>
        </div>
      </div>

      {related.length > 0 && (
        <div className="related">
          <div className="related-title">رياكشنات قريبة</div>
          <div className="related-row">
            {related.map((r) => <MiniCard key={r.id} reaction={r} onOpen={onOpen} />)}
          </div>
        </div>
      )}
    </div>
  );
}

/* ============================================================
   APP — entry point. State + routing between Home and Detail.
   ============================================================ */
export default function App() {
  const [view, setView] = useState("home");
  const [selectedId, setSelectedId] = useState(null);
  const [query, setQuery] = useState("");
  const [activeCat, setActiveCat] = useState(null);
  const [saved, setSaved] = useState(new Set());
  const searchRef = useRef(null);

  function toggleSave(id) {
    setSaved((prev) => {
      const next = new Set(prev);
      next.has(id) ? next.delete(id) : next.add(id);
      return next;
    });
  }
  function openReaction(id) {
    setSelectedId(id);
    setView("detail");
  }
  function goHome() {
    setView("home");
  }
  function focusSearch() {
    if (view !== "home") setView("home");
    setTimeout(() => searchRef.current?.focus(), 50);
  }

  const selected = REACTIONS.find((r) => r.id === selectedId);

  return (
    <div dir="rtl" className="app-root">
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Lalezar&family=Cairo:wght@400;600;700;800&family=IBM+Plex+Mono:wght@400;500;600&display=swap');

        .app-root{ background:${T.ink}; color:${T.paper}; min-height:100vh; font-family:'Cairo',sans-serif; }
        .mono{ font-family:'IBM Plex Mono',monospace; direction:ltr; unicode-bidi:isolate; }
        .container{ padding:0 16px 60px; }

        /* ---- header ---- */
        .header{ position:sticky; top:0; z-index:10; display:flex; align-items:center; justify-content:space-between;
          padding:14px 16px; background:rgba(18,18,20,.92); backdrop-filter:blur(6px); border-bottom:1px solid rgba(243,234,224,.07); cursor:default; }
        .header-brand{ display:flex; align-items:center; gap:8px; }
        .header-word{ font-family:'Lalezar',sans-serif; font-size:19px; }
        .header-search-btn{ background:${T.ink2}; border:1px solid rgba(243,234,224,.1); border-radius:8px; width:38px; height:38px; display:flex; align-items:center; justify-content:center; cursor:pointer; }

        .torn-lg{ clip-path: polygon(0% 6%, 6% 0%, 78% 0%, 83% 5%, 88% 1%, 93% 6%, 97% 2%, 100% 11%, 100% 94%, 94% 100%, 6% 100%, 0% 94%); background:${T.ink2}; }
        .torn-sm{ clip-path: polygon(0% 9%, 9% 0%, 76% 0%, 85% 7%, 100% 15%, 100% 92%, 92% 100%, 8% 100%, 0% 92%); background:${T.ink2}; }

        .clip-stage{ position:relative; width:100%; aspect-ratio:9/16; background:linear-gradient(160deg,#2a2320,#171412); display:flex; align-items:center; justify-content:center; }
        .mock-label{ position:absolute; bottom:8px; left:50%; transform:translateX(-50%); font-size:9px; color:${T.grey}; opacity:.8; }
        .peel{ position:absolute; top:0; width:22%; aspect-ratio:1/1; background:${T.paper}; filter:drop-shadow(0 1px 2px rgba(0,0,0,.6)) drop-shadow(0 0 2px rgba(0,0,0,.4)); }
        .peel-tr{ right:0; clip-path:polygon(100% 0,0 0,100% 100%); }
        .peel-tl{ left:0; clip-path:polygon(0 0,100% 0,0 100%); }
        .peel svg{ position:absolute; top:18%; }
        .peel-tr svg{ right:14%; }
        .peel-tl svg{ left:14%; }

        .dur-tag{ position:absolute; top:6%; background:rgba(18,18,20,.75); color:${T.paper}; font-size:10px; padding:3px 7px; }
        .dur-tag.left{ left:6%; } .dur-tag.right{ right:6%; }
        .cat-dot{ position:absolute; bottom:6%; width:11px; height:11px; border-radius:50%; border:2px solid ${T.paper}; }
        .cat-dot.left{ left:6%; } .cat-dot.right{ right:6%; }

        .play-veil{ opacity:0; transition:opacity .18s ease; display:flex; align-items:center; justify-content:center; }
        .torn-lg:hover .play-veil{ opacity:.85; }
        .play-veil.static{ opacity:.7; }

        @keyframes settleIn{ from{ opacity:0; transform:translateY(10px) rotate(-2deg) scale(.96);} to{ opacity:1; transform:translateY(0) rotate(0) scale(1);} }
        .card-enter{ animation:settleIn .32s ease both; }
        @keyframes viewFade{ from{opacity:0; transform:translateY(6px);} to{opacity:1; transform:translateY(0);} }
        .view-enter{ animation:viewFade .22s ease both; padding:0 16px 60px; }
        @media (prefers-reduced-motion: reduce){ .card-enter,.view-enter{ animation:none; } }

        .hero{ text-align:center; max-width:520px; margin:28px auto 26px; }
        .hero-h1{ font-family:'Lalezar',sans-serif; font-weight:400; font-size:30px; line-height:1.4; margin-bottom:10px; color:${T.amber}; }
        .hero-sub{ color:${T.greyLight}; font-size:14px; margin-bottom:22px; line-height:1.7; }

        .search-box{ display:flex; align-items:center; gap:8px; background:${T.ink2}; border:1px solid rgba(243,234,224,.12); padding:13px 14px; margin-bottom:14px; border-radius:2px; }
        .search-input{ background:transparent; border:none; outline:none; color:${T.paper}; font-family:'Cairo',sans-serif; font-size:14px; width:100%; }
        .search-input::placeholder{ color:${T.grey}; }

        .chip-row{ display:flex; flex-wrap:wrap; gap:6px; justify-content:center; }
        .chip{ background:transparent; border:1px solid rgba(243,234,224,.14); color:${T.greyLight}; font-size:11.5px; padding:8px 12px; cursor:pointer; font-family:'Cairo',sans-serif; border-radius:2px; }
        .chip:hover{ border-color:${T.amberLight}; color:${T.paper}; }

        .cat-rail{ display:flex; gap:8px; overflow-x:auto; padding:2px 2px 14px; margin-bottom:18px; border-bottom:1px solid rgba(243,234,224,.07); scrollbar-width:none; }
        .cat-rail::-webkit-scrollbar{ display:none; }
        .cat-pill{ flex:0 0 auto; background:${T.ink2}; border:1px solid var(--pc); color:var(--pc); font-size:12.5px; padding:10px 15px; cursor:pointer; font-family:'Cairo',sans-serif; font-weight:600; opacity:.55; transition:opacity .15s; min-height:40px; }
        .cat-pill.active{ opacity:1; background:color-mix(in srgb, var(--pc) 16%, transparent); }

        .grid{ display:grid; grid-template-columns:repeat(2,1fr); gap:16px; max-width:900px; margin:0 auto; }
        @media (min-width:640px){ .grid{ grid-template-columns:repeat(3,1fr);} }
        @media (min-width:900px){ .grid{ grid-template-columns:repeat(4,1fr);} }

        .card-meta{ padding:8px 2px 0; }
        .card-meta-top{ display:flex; align-items:center; justify-content:space-between; margin-bottom:3px; }
        .cat-label{ font-size:11px; font-weight:700; }
        .cat-label.lg{ font-size:13px; }
        .save-btn{ background:none; border:none; cursor:pointer; padding:6px; display:flex; transition:transform .12s ease; border-radius:6px; }
        .save-btn:active{ transform:scale(.8); }
        .quote-line{ font-size:13px; color:${T.paperDim}; }

        .empty-state{ text-align:center; color:${T.greyLight}; font-size:13.5px; padding:40px 0; }

        .back-btn{ display:flex; align-items:center; gap:4px; background:none; border:none; color:${T.greyLight}; font-family:'Cairo',sans-serif; font-size:13px; cursor:pointer; margin:18px 0; padding:8px 4px; }
        .back-btn:hover{ color:${T.paper}; }

        .detail-layout{ display:grid; gap:24px; max-width:760px; margin:0 auto; }
        @media (min-width:640px){ .detail-layout{ grid-template-columns:280px 1fr; align-items:start; } }
        .detail-meta{ display:flex; flex-direction:column; gap:10px; padding-top:4px; }
        .situation{ font-size:14px; color:${T.greyLight}; }
        .quote-big{ font-family:'Lalezar',sans-serif; font-size:30px; color:${T.paper}; }
        .rid{ font-size:11px; color:${T.grey}; }
        .tag-row{ display:flex; flex-wrap:wrap; gap:8px; margin-top:2px; }
        .tag-pill{ font-size:11px; color:${T.greyLight}; background:${T.ink2}; border:1px solid rgba(243,234,224,.08); padding:4px 10px; border-radius:2px; }
        .action-row{ display:flex; gap:10px; margin-top:10px; flex-wrap:wrap; }
        .btn-primary{ display:flex; align-items:center; gap:7px; background:${T.amber}; color:${T.ink}; border:none; padding:12px 20px; font-family:'Cairo',sans-serif; font-weight:700; font-size:13.5px; cursor:pointer; min-width:150px; justify-content:center; min-height:44px; transition:background .15s; }
        .btn-primary:hover{ background:${T.amberLight}; }
        .btn-primary:active{ transform:scale(.98); }
        .btn-secondary{ display:flex; align-items:center; gap:7px; background:transparent; color:${T.paper}; border:1px solid rgba(243,234,224,.2); padding:12px 18px; font-family:'Cairo',sans-serif; font-size:13.5px; cursor:pointer; min-height:44px; transition:border-color .15s; }
        .btn-secondary:hover{ border-color:${T.amberLight}; }

        .related{ max-width:760px; margin:40px auto 0; }
        .related-title{ font-size:13px; font-weight:700; color:${T.greyLight}; margin-bottom:12px; }
        .related-row{ display:flex; gap:12px; overflow-x:auto; padding-bottom:6px; scrollbar-width:none; }
        .related-row::-webkit-scrollbar{ display:none; }
        .mini-card{ flex:0 0 96px; cursor:pointer; }
        .mini-quote{ font-size:11px; margin-top:5px; text-align:center; }
      `}</style>

      <Header onSearchIconClick={focusSearch} />

      <div className="container">
        {view === "home" ? (
          <Home
            query={query} setQuery={setQuery}
            activeCat={activeCat} setActiveCat={setActiveCat}
            saved={saved} onToggleSave={toggleSave} onOpen={openReaction}
            searchRef={searchRef}
          />
        ) : (
          selected && (
            <ReactionDetail
              reaction={selected}
              saved={saved.has(selected.id)}
              onToggleSave={toggleSave}
              onBack={goHome}
              onOpen={openReaction}
            />
          )
        )}
      </div>
    </div>
  );
}
