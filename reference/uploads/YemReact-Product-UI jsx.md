import { useState, useEffect } from "react";
import { Search, Bookmark, BookmarkCheck, Download, Play, ChevronRight, Check } from "lucide-react";

/* ============================================================
   YemReact — Design tokens (locked in Brand v1.0, reused as-is)
   ============================================================ */
const T = {
  ink: "#121214", ink2: "#1a1a1d", ink3: "#232327",
  amber: "#c1592e", amberLight: "#e0824b",
  paper: "#f3eae0", paperDim: "#c9bfb4",
  coral: "#ff5a36", grey: "#6b625c", greyLight: "#9c9289",
};

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

const REACTIONS = [
  { id: "YR-0001", cat: "shock",     situation: "لما تسمع خبر صادم",              quote: "يا ساتر!",           dur: 2, corner: "tr", tags: ["خبر", "صدمة", "مفاجأة"] },
  { id: "YR-0002", cat: "reject",    situation: "لما حد يقولك كلام مالوش داعي",   quote: "عاد شي عقل؟",        dur: 3, corner: "tl", tags: ["رفض", "كلام فاضي"] },
  { id: "YR-0003", cat: "sarcasm",   situation: "لما حد يسولف عليك",              quote: "قوية... قوية جدًا",   dur: 5, corner: "tr", tags: ["سخرية", "تعليق"] },
  { id: "YR-0004", cat: "hype",      situation: "لما فريقك يسجل هدف",             quote: "قوية!",              dur: 3, corner: "tl", tags: ["حماس", "فرح", "رياضة"] },
  { id: "YR-0005", cat: "surprise",  situation: "لما تشوف شي ما تصدق عيونك",      quote: "صلّي على النبي",     dur: 4, corner: "tr", tags: ["استغراب", "انبهار"] },
  { id: "YR-0006", cat: "laugh",     situation: "لما صاحبك يقع بموقف محرج",       quote: "ياخي وربي",          dur: 3, corner: "tr", tags: ["ضحك", "موقف محرج"] },
  { id: "YR-0007", cat: "embarrass", situation: "لما ما تلقى رد على كلامك",       quote: "...",                dur: 4, corner: "tr", tags: ["إحراج", "صمت"] },
  { id: "YR-0008", cat: "reject",    situation: "لما صاحبك يقول بكرة أسددلك",     quote: "برضه؟",              dur: 3, corner: "tr", tags: ["رفض", "دين", "مماطلة"] },
  { id: "YR-0009", cat: "approve",   situation: "لما حد يقنعك بفكرة",             quote: "معك حق",             dur: 2, corner: "tr", tags: ["موافقة", "اقتناع"] },
  { id: "YR-0010", cat: "anger",     situation: "لما حد يضيّع وقتك",              quote: "كفاية!",             dur: 3, corner: "tr", tags: ["غضب", "ضيق"] },
  { id: "YR-0011", cat: "laugh",     situation: "لما واحد يمزح وما يوقف",         quote: "بس بس بس",           dur: 3, corner: "tr", tags: ["ضحك", "هزار"] },
  { id: "YR-0012", cat: "hype",      situation: "لما تسمع خبر مفرحك",             quote: "يووه!",              dur: 2, corner: "tr", tags: ["حماس", "فرح"] },
];

/* ============================================================
   Reusable brand components — the "asset system" as real code
   ============================================================ */
function QusasaMark({ size = 28, fill = T.amber, outline = false }) {
  return (
    <svg width={size} height={size} viewBox="0 0 120 120" style={{ display: "block" }}>
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
  const side = corner === "tr" ? "left" : "right"; // opposite corner from the peel
  return <div className={`dur-tag mono ${side}`}>{dur}s</div>;
}

function CategoryDot({ cat, corner = "tr" }) {
  const side = corner === "tr" ? "left" : "right"; // bottom, opposite the top peel side
  return <div className={`cat-dot ${side}`} style={{ background: catById[cat].color }} />;
}

function ClipStage({ reaction, children }) {
  // Placeholder gradient standing in for the actual video frame — this prototype
  // has no real footage, and the UI says so instead of pretending otherwise.
  return (
    <div className="clip-stage">
      <span className="mock-label mono">MOCK PREVIEW</span>
      <PeelMark corner={reaction.corner} />
      <DurationTag dur={reaction.dur} corner={reaction.corner} />
      <CategoryDot cat={reaction.cat} corner={reaction.corner} />
      {children}
    </div>
  );
}

/* ============================================================
   Cards
   ============================================================ */
function ReactionCard({ reaction, index, saved, onToggleSave, onOpen }) {
  const cat = catById[reaction.cat];
  return (
    <div
      className="card-enter card-tap"
      style={{ animationDelay: `${index * 40}ms`, cursor: "pointer" }}
      onClick={() => onOpen(reaction.id)}
      role="button"
      tabIndex={0}
      onKeyDown={(e) => { if (e.key === "Enter") onOpen(reaction.id); }}
    >
      <TornFrame size="lg">
        <ClipStage reaction={reaction}>
          <div className="play-veil">
            <Play size={22} color={T.paper} fill={T.paper} />
          </div>
        </ClipStage>
      </TornFrame>
      <div className="card-meta">
        <div className="card-meta-top">
          <span className="cat-label" style={{ color: cat.color }}>{cat.name}</span>
          <button
            className="save-btn"
            onClick={(e) => { e.stopPropagation(); onToggleSave(reaction.id); }}
            aria-label="save"
          >
            {saved ? <BookmarkCheck size={16} color={T.amberLight} /> : <Bookmark size={16} color={T.greyLight} />}
          </button>
        </div>
        <div className="quote-line">{reaction.quote}</div>
      </div>
    </div>
  );
}

function MiniCard({ reaction, onOpen }) {
  const cat = catById[reaction.cat];
  return (
    <div className="mini-card" onClick={() => onOpen(reaction.id)}>
      <TornFrame size="sm" style={{ cursor: "pointer" }}>
        <ClipStage reaction={reaction} />
      </TornFrame>
      <div className="mini-quote" style={{ color: cat.color }}>{reaction.quote}</div>
    </div>
  );
}

/* ============================================================
   Views
   ============================================================ */
function Home({ query, setQuery, activeCat, setActiveCat, saved, onToggleSave, onOpen }) {
  const filtered = REACTIONS.filter((r) => {
    const matchesCat = !activeCat || r.cat === activeCat;
    const q = query.trim();
    const matchesQuery =
      !q ||
      r.situation.includes(q) ||
      r.quote.includes(q) ||
      catById[r.cat].name.includes(q) ||
      (r.tags || []).some((t) => t.includes(q));
    return matchesCat && matchesQuery;
  });

  return (
    <div className="view-enter">
      <div className="hero">
        <div className="hero-lockup">
          <QusasaMark size={30} />
          <span className="hero-word">يمن رياكت</span>
        </div>
        <h1 className="hero-h1">رياكشنات يمنية<br />تتكلم بلسانك.</h1>
        <p className="hero-sub">مكتبة رياكشنات يمنية قصيرة ونادرة — دوّر بالموقف اللي فيه، مو بالمشاعر.</p>
        <p className="hero-tagline">خذها. حطها. يمنية.</p>

        <div className="search-box">
          <Search size={17} color={T.greyLight} />
          <input
            className="search-input"
            placeholder="لما واحد يكذب عليك..."
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
  const cat = catById[reaction.cat];
  const related = REACTIONS.filter((r) => r.cat === reaction.cat && r.id !== reaction.id).slice(0, 5);

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
          <div className="situation">{reaction.situation}</div>
          <div className="quote-big">{reaction.quote}</div>
          <div className="rid mono">{reaction.id}</div>

          <div className="action-row">
            <button className="btn-primary" onClick={handleUse}>
              {done ? <><Check size={16} /> جاهزة</> : downloading ? "جاري التجهيز..." : <><Download size={16} /> استخدم / حمّل</>}
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
   App
   ============================================================ */
export default function App() {
  const [view, setView] = useState("home");
  const [selectedId, setSelectedId] = useState(null);
  const [query, setQuery] = useState("");
  const [activeCat, setActiveCat] = useState(null);
  const [saved, setSaved] = useState(new Set());

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

  useEffect(() => {
    window.scrollTo({ top: 0, behavior: "auto" });
  }, [view, selectedId]);

  const selected = REACTIONS.find((r) => r.id === selectedId);

  return (
    <div dir="rtl" className="app-root">
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Lalezar&family=Cairo:wght@400;600;700;800&family=IBM+Plex+Mono:wght@400;500;600&display=swap');

        .app-root{
          background:${T.ink}; color:${T.paper}; min-height:100vh;
          font-family:'Cairo',sans-serif; padding:20px 16px 60px;
        }
        .mono{ font-family:'IBM Plex Mono',monospace; direction:ltr; unicode-bidi:isolate; }

        .torn-lg{ clip-path: polygon(0% 6%, 6% 0%, 78% 0%, 83% 5%, 88% 1%, 93% 6%, 97% 2%, 100% 11%, 100% 94%, 94% 100%, 6% 100%, 0% 94%); background:${T.ink2}; }
        .torn-sm{ clip-path: polygon(0% 9%, 9% 0%, 76% 0%, 85% 7%, 100% 15%, 100% 92%, 92% 100%, 8% 100%, 0% 92%); background:${T.ink2}; }

        .clip-stage{ position:relative; width:100%; aspect-ratio:9/16; background:linear-gradient(160deg,#2a2320,#171412); display:flex; align-items:center; justify-content:center; }
        .mock-label{ position:absolute; top:16%; left:50%; transform:translateX(-50%); font-size:9px; letter-spacing:.08em; color:${T.grey}; opacity:.55; pointer-events:none; }
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
        .view-enter{ animation:viewFade .22s ease both; }
        @media (prefers-reduced-motion: reduce){ .card-enter,.view-enter{ animation:none; } }

        .hero{ text-align:center; max-width:520px; margin:10px auto 28px; }
        .hero-lockup{ display:flex; align-items:center; justify-content:center; gap:8px; margin-bottom:14px; }
        .hero-word{ font-family:'Lalezar',sans-serif; font-size:22px; }
        .hero-h1{ font-family:'Lalezar',sans-serif; font-weight:400; font-size:28px; line-height:1.4; margin-bottom:8px; }
        .hero-sub{ color:${T.greyLight}; font-size:13.5px; margin-bottom:10px; }
        .hero-tagline{ font-family:'Lalezar',sans-serif; font-size:17px; color:${T.amber}; margin-bottom:22px; }

        .search-box{ display:flex; align-items:center; gap:8px; background:${T.ink2}; border:1px solid rgba(243,234,224,.12); padding:11px 14px; margin-bottom:14px; }
        .search-input{ background:transparent; border:none; outline:none; color:${T.paper}; font-family:'Cairo',sans-serif; font-size:13.5px; width:100%; }
        .search-input::placeholder{ color:${T.grey}; }

        .chip-row{ display:flex; flex-wrap:wrap; gap:6px; justify-content:center; }
        .chip{ background:transparent; border:1px solid rgba(243,234,224,.14); color:${T.greyLight}; font-size:11.5px; padding:6px 11px; cursor:pointer; font-family:'Cairo',sans-serif; }
        .chip:hover{ border-color:${T.amberLight}; color:${T.paper}; }

        .cat-rail{ display:flex; gap:8px; overflow-x:auto; padding-bottom:14px; margin-bottom:18px; border-bottom:1px solid rgba(243,234,224,.07); }
        .cat-pill{ flex:0 0 auto; background:${T.ink2}; border:1px solid var(--pc); color:var(--pc); font-size:12px; padding:7px 13px; cursor:pointer; font-family:'Cairo',sans-serif; font-weight:600; opacity:.55; transition:opacity .15s; }
        .cat-pill.active{ opacity:1; background:color-mix(in srgb, var(--pc) 16%, transparent); }

        .grid{ display:grid; grid-template-columns:repeat(2,1fr); gap:16px; max-width:900px; margin:0 auto; }
        @media (min-width:640px){ .grid{ grid-template-columns:repeat(3,1fr);} }
        @media (min-width:900px){ .grid{ grid-template-columns:repeat(4,1fr);} }

        .card-meta{ padding:8px 2px 0; }
        .card-meta-top{ display:flex; align-items:center; justify-content:space-between; margin-bottom:3px; }
        .cat-label{ font-size:11px; font-weight:700; }
        .cat-label.lg{ font-size:13px; }
        .save-btn{ background:none; border:none; cursor:pointer; padding:2px; display:flex; }
        .quote-line{ font-size:13px; color:${T.paperDim}; }

        .empty-state{ text-align:center; color:${T.greyLight}; font-size:13.5px; padding:40px 0; }

        .back-btn{ display:flex; align-items:center; gap:4px; background:none; border:none; color:${T.greyLight}; font-family:'Cairo',sans-serif; font-size:13px; cursor:pointer; margin-bottom:18px; padding:6px 0; }
        .back-btn:hover{ color:${T.paper}; }

        .detail-layout{ display:grid; gap:24px; max-width:760px; margin:0 auto; }
        @media (min-width:640px){ .detail-layout{ grid-template-columns:280px 1fr; align-items:start; } }
        .detail-meta{ display:flex; flex-direction:column; gap:10px; padding-top:4px; }
        .situation{ font-size:14px; color:${T.greyLight}; }
        .quote-big{ font-family:'Lalezar',sans-serif; font-size:30px; color:${T.paper}; }
        .rid{ font-size:11px; color:${T.grey}; }
        .action-row{ display:flex; gap:10px; margin-top:10px; flex-wrap:wrap; }
        .btn-primary{ display:flex; align-items:center; gap:7px; background:${T.amber}; color:${T.ink}; border:none; padding:11px 18px; font-family:'Cairo',sans-serif; font-weight:700; font-size:13.5px; cursor:pointer; min-width:150px; justify-content:center; }
        .btn-primary:hover{ background:${T.amberLight}; }
        .btn-secondary{ display:flex; align-items:center; gap:7px; background:transparent; color:${T.paper}; border:1px solid rgba(243,234,224,.2); padding:11px 16px; font-family:'Cairo',sans-serif; font-size:13.5px; cursor:pointer; }
        .btn-secondary:hover{ border-color:${T.amberLight}; }

        .related{ max-width:760px; margin:40px auto 0; }
        .related-title{ font-size:13px; font-weight:700; color:${T.greyLight}; margin-bottom:12px; }
        .related-row{ display:flex; gap:12px; overflow-x:auto; padding-bottom:6px; }
        .mini-card{ flex:0 0 96px; cursor:pointer; }
        .mini-quote{ font-size:11px; margin-top:5px; text-align:center; }

        .proto-footer{ text-align:center; margin-top:56px; padding-top:20px; border-top:1px solid rgba(243,234,224,.06); }
        .proto-footer span{ font-size:10.5px; color:${T.grey}; }
      `}</style>

      {view === "home" ? (
        <Home
          query={query} setQuery={setQuery}
          activeCat={activeCat} setActiveCat={setActiveCat}
          saved={saved} onToggleSave={toggleSave} onOpen={openReaction}
        />
      ) : (
        selected && (
          <ReactionDetail
            reaction={selected}
            saved={saved.has(selected.id)}
            onToggleSave={toggleSave}
            onBack={() => setView("home")}
            onOpen={openReaction}
          />
        )
      )}

      <div className="proto-footer">
        <span className="mono">YEMREACT PROTOTYPE — MOCK DATA, NO BACKEND — BRAND v1.0</span>
      </div>
    </div>
  );
}
