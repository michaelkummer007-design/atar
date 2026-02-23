import React, { useState, useEffect, useCallback } from 'react';
import { 
  Terminal, 
  Cpu, 
  ShieldCheck, 
  Zap, 
  LayoutDashboard, 
  Settings, 
  LogOut, 
  Lock, 
  User, 
  Sparkles, 
  Image as ImageIcon, 
  Send,
  Loader2,
  Menu,
  X,
  ChevronRight,
  TrendingUp,
  Globe,
  UserPlus
} from 'lucide-react';

// --- Configuration & API Logic ---
const apiKey = ""; 
const appId = typeof __app_id !== 'undefined' ? __app_id : 'biz-ai-platform';

// Admin Secret - Hidden in logic
const _A_H = "Nx92!Admin"; 

const API_RETRY_DELAY = [1000, 2000, 4000, 8000, 16000];

const callGemini = async (prompt) => {
  let lastError;
  for (let i = 0; i < 5; i++) {
    try {
      const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          contents: [{ parts: [{ text: prompt }] }],
          systemInstruction: { parts: [{ text: "אתה עוזר עסקי חכם. ענה בעברית בלבד. עזור למשתמש למקסם רווחים ולכתוב תוכן שיווקי מושלם." }] }
        })
      });
      const data = await response.json();
      return data.candidates?.[0]?.content?.parts?.[0]?.text;
    } catch (err) {
      lastError = err;
      await new Promise(r => setTimeout(r, API_RETRY_DELAY[i]));
    }
  }
  throw lastError;
};

const generateImage = async (prompt) => {
  try {
    const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/imagen-4.0-generate-001:predict?key=${apiKey}`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        instances: { prompt: prompt },
        parameters: { sampleCount: 1 }
      })
    });
    const data = await response.json();
    return `data:image/png;base64,${data.predictions[0].bytesBase64Encoded}`;
  } catch (err) {
    console.error("Image generation failed", err);
    return null;
  }
};

// --- Components ---

const Navbar = ({ user, onLogout, setView, currentView }) => {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <nav className="fixed w-full z-50 bg-white/80 dark:bg-slate-900/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-800">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="flex justify-between h-16 items-center">
          <div className="flex items-center gap-2 cursor-pointer" onClick={() => setView('landing')}>
            <div className="bg-indigo-600 p-2 rounded-lg">
              <Cpu className="text-white w-6 h-6" />
            </div>
            <span className="text-xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-indigo-600 to-purple-600">
              Nexus AI
            </span>
          </div>

          <div className="hidden md:flex items-center gap-8">
            <button onClick={() => setView('landing')} className={`text-sm font-medium ${currentView === 'landing' ? 'text-indigo-600' : 'text-slate-600 dark:text-slate-300'}`}>ראשי</button>
            {user && (
              <>
                <button onClick={() => setView('dashboard')} className={`text-sm font-medium ${currentView === 'dashboard' ? 'text-indigo-600' : 'text-slate-600 dark:text-slate-300'}`}>לוח בקרה</button>
                <button onClick={() => setView('ai-tools')} className={`text-sm font-medium ${currentView === 'ai-tools' ? 'text-indigo-600' : 'text-slate-600 dark:text-slate-300'}`}>כלי AI</button>
              </>
            )}
            {!user ? (
              <button 
                onClick={() => setView('auth')}
                className="bg-indigo-600 text-white px-5 py-2 rounded-full text-sm font-semibold hover:bg-indigo-700 transition-all shadow-lg shadow-indigo-200"
              >
                התחברות / הרשמה
              </button>
            ) : (
              <div className="flex items-center gap-4">
                <span className="text-sm font-medium text-slate-700 dark:text-slate-200">שלום, {user.name}</span>
                <button onClick={onLogout} className="p-2 text-slate-500 hover:text-red-500 transition-colors">
                  <LogOut className="w-5 h-5" />
                </button>
              </div>
            )}
          </div>

          <div className="md:hidden">
            <button onClick={() => setIsOpen(!isOpen)} className="p-2">
              {isOpen ? <X /> : <Menu />}
            </button>
          </div>
        </div>
      </div>
      {/* Mobile Menu */}
      {isOpen && (
        <div className="md:hidden bg-white border-b border-slate-200 p-4 space-y-4">
            <button onClick={() => {setView('landing'); setIsOpen(false)}} className="block w-full text-right py-2">ראשי</button>
            {user && (
              <>
                <button onClick={() => {setView('dashboard'); setIsOpen(false)}} className="block w-full text-right py-2">לוח בקרה</button>
                <button onClick={() => {setView('ai-tools'); setIsOpen(false)}} className="block w-full text-right py-2">כלי AI</button>
                <button onClick={() => {onLogout(); setIsOpen(false)}} className="block w-full text-right py-2 text-red-500">התנתק</button>
              </>
            )}
            {!user && <button onClick={() => {setView('auth'); setIsOpen(false)}} className="block w-full text-right py-2">התחברות</button>}
        </div>
      )}
    </nav>
  );
};

const AuthForm = ({ onLogin }) => {
  const [isLogin, setIsLogin] = useState(true);
  const [isAdmin, setIsAdmin] = useState(false);
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const [error, setError] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    setError('');

    if (isAdmin) {
      if (password === _A_H) {
        onLogin({ role: 'admin', name: 'מנהל מערכת', id: 'admin' });
      } else {
        setError('סיסמת מנהל שגויה.');
      }
      return;
    }

    // Customer Logic
    const users = JSON.parse(localStorage.getItem('biz_users') || '{}');
    
    if (isLogin) {
      if (users[username] && users[username].password === password) {
        onLogin({ role: 'user', name: username, id: username });
      } else {
        setError('שם משתמש או סיסמה שגויים.');
      }
    } else {
      if (users[username]) {
        setError('שם משתמש זה כבר קיים.');
      } else if (password.length < 4) {
        setError('הסיסמה חייבת להכיל לפחות 4 תווים.');
      } else {
        users[username] = { password };
        localStorage.setItem('biz_users', JSON.stringify(users));
        onLogin({ role: 'user', name: username, id: username });
      }
    }
  };

  return (
    <div className="min-h-screen flex items-center justify-center px-4 bg-slate-50 pt-20">
      <div className="max-w-md w-full bg-white rounded-3xl shadow-2xl p-8 border border-slate-100">
        <div className="text-center mb-8">
          <div className="inline-flex p-3 rounded-2xl bg-indigo-50 text-indigo-600 mb-4">
            {isAdmin ? <ShieldCheck className="w-8 h-8" /> : (isLogin ? <Lock className="w-8 h-8" /> : <UserPlus className="w-8 h-8" />)}
          </div>
          <h2 className="text-3xl font-bold text-slate-900">
            {isAdmin ? 'כניסת מנהל' : (isLogin ? 'התחברות לקוח' : 'הרשמת לקוח')}
          </h2>
        </div>

        <div className="flex p-1 bg-slate-100 rounded-xl mb-6">
          <button 
            onClick={() => {setIsAdmin(false); setIsLogin(true)}}
            className={`flex-1 py-2 rounded-lg text-sm font-semibold transition-all ${!isAdmin ? 'bg-white shadow-sm text-indigo-600' : 'text-slate-500'}`}
          >
            לקוח
          </button>
          <button 
            onClick={() => setIsAdmin(true)}
            className={`flex-1 py-2 rounded-lg text-sm font-semibold transition-all ${isAdmin ? 'bg-white shadow-sm text-indigo-600' : 'text-slate-500'}`}
          >
            אדמין
          </button>
        </div>

        <form onSubmit={handleSubmit} className="space-y-4">
          {!isAdmin && (
            <div>
              <label className="block text-sm font-medium text-slate-700 mb-1">שם משתמש</label>
              <input 
                type="text" 
                value={username}
                onChange={(e) => setUsername(e.target.value)}
                className="w-full px-4 py-3 rounded-xl border border-slate-200 focus:ring-2 focus:ring-indigo-500 outline-none transition-all"
                placeholder="הכנס שם משתמש"
                required
              />
            </div>
          )}
          <div>
            <label className="block text-sm font-medium text-slate-700 mb-1">סיסמה</label>
            <input 
              type="password" 
              value={password}
              onChange={(e) => setPassword(e.target.value)}
              className="w-full px-4 py-3 rounded-xl border border-slate-200 focus:ring-2 focus:ring-indigo-500 outline-none transition-all"
              placeholder={isAdmin ? "סיסמת מנהל סודית" : "הכנס סיסמה"}
              required
            />
          </div>
          {error && <p className="text-red-500 text-sm font-medium">{error}</p>}
          <button 
            type="submit"
            className="w-full py-4 bg-indigo-600 text-white rounded-xl font-bold hover:bg-indigo-700 transition-all shadow-lg shadow-indigo-200"
          >
            {isAdmin ? 'כניסת מנהל' : (isLogin ? 'התחבר' : 'הירשם עכשיו')}
          </button>
        </form>

        {!isAdmin && (
            <div className="mt-6 text-center">
                <button 
                    onClick={() => setIsLogin(!isLogin)}
                    className="text-indigo-600 text-sm font-medium hover:underline"
                >
                    {isLogin ? 'אין לך חשבון? הירשם כאן' : 'כבר רשום? התחבר כאן'}
                </button>
            </div>
        )}
      </div>
    </div>
  );
};

const Hero = ({ onStart }) => (
  <div className="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden">
    <div className="absolute top-0 left-1/2 -translate-x-1/2 w-full h-full -z-10">
      <div className="absolute top-[-10%] left-[-10%] w-[40%] h-[40%] bg-purple-200/50 rounded-full blur-3xl" />
      <div className="absolute bottom-[-10%] right-[-10%] w-[40%] h-[40%] bg-indigo-200/50 rounded-full blur-3xl" />
    </div>
    
    <div className="max-w-7xl mx-auto px-4 text-center">
      <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-indigo-50 border border-indigo-100 text-indigo-700 text-sm font-medium mb-6">
        <Sparkles className="w-4 h-4" />
        <span>העתיד של העסקים כבר כאן</span>
      </div>
      <h1 className="text-5xl lg:text-7xl font-extrabold text-slate-900 mb-6 leading-tight">
        בנה את האימפריה שלך <br />
        <span className="text-indigo-600 italic">בעזרת AI</span>
      </h1>
      <p className="text-xl text-slate-600 max-w-2xl mx-auto mb-10">
        פלטפורמת ה-AI המתקדמת בעולם לניהול עסקי, יצירת תוכן שיווקי ואוטומציה מלאה שמגדילה רווחים.
      </p>
      <div className="flex flex-col sm:flex-row gap-4 justify-center">
        <button 
          onClick={onStart}
          className="px-8 py-4 bg-indigo-600 text-white rounded-xl font-bold text-lg hover:bg-indigo-700 transition-all shadow-xl shadow-indigo-200 flex items-center justify-center gap-2"
        >
          מתחילים עכשיו <ChevronRight className="w-5 h-5" />
        </button>
        <button className="px-8 py-4 bg-white border border-slate-200 text-slate-700 rounded-xl font-bold text-lg hover:bg-slate-50 transition-all">
          צפה בדמו
        </button>
      </div>
    </div>
  </div>
);

const Features = () => {
  const items = [
    { icon: <Zap className="text-amber-500" />, title: "מהירות שיא", desc: "ביצועים אופטימליים לכל פעולה עסקית" },
    { icon: <ShieldCheck className="text-green-500" />, title: "אבטחה מקסימלית", desc: "הנתונים שלך מוגנים בסטנדרט הגבוה ביותר" },
    { icon: <Globe className="text-blue-500" />, title: "פריסה עולמית", desc: "העסק שלך זמין מכל מקום בעולם" },
    { icon: <TrendingUp className="text-rose-500" />, title: "ניתוח נתונים", desc: "תובנות מבוססות AI להגדלת המכירות" },
  ];

  return (
    <section className="py-20 bg-slate-50">
      <div className="max-w-7xl mx-auto px-4">
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          {items.map((item, i) => (
            <div key={i} className="p-8 bg-white rounded-2xl border border-slate-100 hover:shadow-xl transition-all group">
              <div className="w-12 h-12 rounded-lg bg-slate-50 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform">
                {item.icon}
              </div>
              <h3 className="text-xl font-bold text-slate-900 mb-3">{item.title}</h3>
              <p className="text-slate-600">{item.desc}</p>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
};

const AITools = () => {
  const [prompt, setPrompt] = useState('');
  const [loading, setLoading] = useState(false);
  const [result, setResult] = useState(null);
  const [mode, setMode] = useState('text');

  const handleGenerate = async () => {
    if (!prompt) return;
    setLoading(true);
    try {
      if (mode === 'text') {
        const text = await callGemini(prompt);
        setResult({ type: 'text', content: text });
      } else {
        const img = await generateImage(prompt);
        setResult({ type: 'image', content: img });
      }
    } catch (err) {
      console.error(err);
    } finally {
      setLoading(false);
    }
  };

  return (
    <div className="pt-24 max-w-4xl mx-auto px-4 pb-20">
      <div className="bg-white rounded-3xl shadow-xl p-8 border border-slate-100">
        <div className="flex items-center gap-4 mb-8">
          <div className="p-3 bg-purple-100 text-purple-600 rounded-2xl">
            <Sparkles className="w-6 h-6" />
          </div>
          <div>
            <h2 className="text-2xl font-bold text-slate-900">מעבדת ה-AI שלך</h2>
            <p className="text-slate-500">צור תוכן שיווקי או תמונות מרהיבות בשניות</p>
          </div>
        </div>

        <div className="flex gap-4 mb-6">
          <button 
            onClick={() => {setMode('text'); setResult(null)}}
            className={`flex items-center gap-2 px-6 py-3 rounded-xl font-semibold transition-all ${mode === 'text' ? 'bg-indigo-600 text-white' : 'bg-slate-100 text-slate-600'}`}
          >
            <Send className="w-4 h-4" /> יצירת תוכן
          </button>
          <button 
            onClick={() => {setMode('image'); setResult(null)}}
            className={`flex items-center gap-2 px-6 py-3 rounded-xl font-semibold transition-all ${mode === 'image' ? 'bg-indigo-600 text-white' : 'bg-slate-100 text-slate-600'}`}
          >
            <ImageIcon className="w-4 h-4" /> יצירת תמונה
          </button>
        </div>

        <div className="space-y-4">
          <textarea 
            value={prompt}
            onChange={(e) => setPrompt(e.target.value)}
            className="w-full p-4 rounded-2xl border border-slate-200 focus:ring-2 focus:ring-indigo-500 outline-none min-h-[120px]"
            placeholder={mode === 'text' ? "תאר את המוצר שלך וה-AI יכתוב פוסט שיווקי..." : "תאר תמונה עסקית שתרצה ליצור..."}
          />
          <button 
            onClick={handleGenerate}
            disabled={loading}
            className="w-full py-4 bg-gradient-to-r from-indigo-600 to-purple-600 text-white rounded-2xl font-bold flex items-center justify-center gap-2 disabled:opacity-50"
          >
            {loading ? <Loader2 className="animate-spin w-5 h-5" /> : <Zap className="w-5 h-5" />}
            {loading ? 'ה-AI חושב...' : 'צור עכשיו'}
          </button>
        </div>

        {result && (
          <div className="mt-10 p-6 bg-slate-50 rounded-2xl border border-dashed border-slate-300">
            <h4 className="text-sm font-bold text-slate-400 uppercase tracking-wider mb-4">התוצאה:</h4>
            {result.type === 'text' ? (
              <p className="text-slate-800 leading-relaxed whitespace-pre-wrap text-lg">{result.content}</p>
            ) : (
              <div className="flex justify-center">
                {result.content ? (
                  <img src={result.content} alt="Generated AI" className="rounded-xl shadow-lg max-w-full h-auto" />
                ) : (
                  <p className="text-red-500">שגיאה ביצירת התמונה. נסה שוב.</p>
                )}
              </div>
            )}
          </div>
        )}
      </div>
    </div>
  );
};

const Dashboard = ({ user }) => {
  const stats = [
    { label: 'רווחים החודש', value: '₪45,200', icon: <TrendingUp className="text-green-500" /> },
    { label: 'לקוחות פעילים', value: '1,284', icon: <User className="text-blue-500" /> },
    { label: 'פניות AI', value: '452', icon: <Sparkles className="text-purple-500" /> },
    { label: 'רמת אבטחה', value: '98%', icon: <ShieldCheck className="text-indigo-500" /> },
  ];

  return (
    <div className="pt-24 max-w-7xl mx-auto px-4 pb-20">
      <header className="mb-10 flex flex-col md:flex-row md:items-center justify-between gap-4">
        <div>
          <h1 className="text-3xl font-bold text-slate-900">שלום, {user.name}</h1>
          <p className="text-slate-500">סוג חשבון: {user.role === 'admin' ? 'מנהל על' : 'לקוח מועדף'}</p>
        </div>
      </header>

      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-10">
        {stats.map((stat, i) => (
          <div key={i} className="bg-white p-6 rounded-2xl border border-slate-100 shadow-sm">
            <div className="flex items-center justify-between mb-4">
              <div className="p-2 rounded-lg bg-slate-50">{stat.icon}</div>
              <span className="text-xs font-bold text-green-500 bg-green-50 px-2 py-1 rounded-full">+12%</span>
            </div>
            <p className="text-slate-500 text-sm mb-1">{stat.label}</p>
            <p className="text-2xl font-bold text-slate-900">{stat.value}</p>
          </div>
        ))}
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <div className="lg:col-span-2 bg-white rounded-2xl border border-slate-100 p-6 shadow-sm">
          <h3 className="text-lg font-bold mb-6">פעולות אחרונות בחשבון</h3>
          <div className="space-y-6">
            {[1,2,3].map(i => (
              <div key={i} className="flex items-center justify-between p-4 bg-slate-50 rounded-xl">
                <div className="flex items-center gap-4">
                  <div className="w-10 h-10 bg-indigo-100 rounded-full flex items-center justify-center text-indigo-600">
                    <Zap className="w-5 h-5" />
                  </div>
                  <div>
                    <p className="font-semibold text-slate-900">שימוש במנוע ה-AI</p>
                    <p className="text-xs text-slate-500">לפני {i * 2} שעות</p>
                  </div>
                </div>
                <span className="text-sm font-medium text-slate-400">הושלם</span>
              </div>
            ))}
          </div>
        </div>
        <div className="bg-gradient-to-br from-indigo-600 to-purple-700 rounded-3xl p-8 text-white relative overflow-hidden">
          <div className="relative z-10">
            <h3 className="text-2xl font-bold mb-4">Nexus Pro</h3>
            <p className="text-indigo-100 mb-8">שדרג עכשיו וקבל גישה למודלים המתקדמים ביותר.</p>
            <button className="w-full py-4 bg-white text-indigo-600 rounded-xl font-bold hover:bg-indigo-50 transition-all">
              שדרוג חשבון
            </button>
          </div>
          <Sparkles className="absolute bottom-[-10%] left-[-10%] w-32 h-32 opacity-20" />
        </div>
      </div>
    </div>
  );
};

// --- Main App Component ---

export default function App() {
  const [view, setView] = useState('landing');
  const [user, setUser] = useState(null);

  // Persistence check on mount
  useEffect(() => {
    const savedUser = localStorage.getItem('biz_current_session');
    if (savedUser) {
        setUser(JSON.parse(savedUser));
    }
  }, []);

  const handleLogin = (userData) => {
    setUser(userData);
    localStorage.setItem('biz_current_session', JSON.stringify(userData));
    setView('dashboard');
  };

  const handleLogout = () => {
    setUser(null);
    localStorage.removeItem('biz_current_session');
    setView('landing');
  };

  const renderContent = () => {
    switch (view) {
      case 'auth':
        return <AuthForm onLogin={handleLogin} />;
      case 'dashboard':
        return user ? <Dashboard user={user} /> : <AuthForm onLogin={handleLogin} />;
      case 'ai-tools':
        return user ? <AITools /> : <AuthForm onLogin={handleLogin} />;
      default:
        return (
          <>
            <Hero onStart={() => setView(user ? 'dashboard' : 'auth')} />
            <Features />
            <section className="py-20 text-center bg-white px-4">
              <h2 className="text-3xl font-bold mb-12">השותפים שלנו להצלחה</h2>
              <div className="flex flex-wrap justify-center gap-12 opacity-40 grayscale items-center">
                <div className="flex items-center gap-2 font-bold text-2xl uppercase tracking-widest"><Globe className="w-8 h-8"/> GlobalX</div>
                <div className="flex items-center gap-2 font-bold text-2xl uppercase tracking-widest"><Terminal className="w-8 h-8"/> CodeBase</div>
                <div className="flex items-center gap-2 font-bold text-2xl uppercase tracking-widest"><Cpu className="w-8 h-8"/> Intellect</div>
              </div>
            </section>
          </>
        );
    }
  };

  return (
    <div className="min-h-screen bg-white text-slate-900 font-sans selection:bg-indigo-100 selection:text-indigo-600" dir="rtl">
      <Navbar user={user} onLogout={handleLogout} setView={setView} currentView={view} />
      
      <main>
        {renderContent()}
      </main>

      <footer className="bg-slate-900 text-white py-20 px-4 mt-20">
        <div className="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-4 gap-12 text-right">
          <div className="col-span-1 md:col-span-2">
            <div className="flex items-center gap-2 mb-6">
              <Cpu className="text-indigo-400 w-8 h-8" />
              <span className="text-2xl font-bold">Nexus AI</span>
            </div>
            <p className="text-slate-400 max-w-sm">
              אנחנו כאן כדי להפוך את החזון העסקי שלך למציאות בעזרת הטכנולוגיה המתקדמת ביותר בעולם.
            </p>
          </div>
          <div>
            <h4 className="font-bold mb-6">ניווט מהיר</h4>
            <ul className="space-y-4 text-slate-400">
              <li onClick={() => setView('landing')} className="hover:text-white cursor-pointer transition-colors">דף הבית</li>
              <li onClick={() => setView('ai-tools')} className="hover:text-white cursor-pointer transition-colors">כלי בינה מלאכותית</li>
              <li className="hover:text-white cursor-pointer transition-colors">תמיכה טכנית</li>
            </ul>
          </div>
          <div>
            <h4 className="font-bold mb-6">משפטי</h4>
            <ul className="space-y-4 text-slate-400">
              <li className="hover:text-white cursor-pointer transition-colors">תנאי שימוש</li>
              <li className="hover:text-white cursor-pointer transition-colors">מדיניות פרטיות</li>
            </ul>
          </div>
        </div>
        <div className="max-w-7xl mx-auto mt-20 pt-8 border-t border-slate-800 text-center text-slate-500 text-sm">
          © {new Date().getFullYear()} Nexus AI Business Solutions. כל הזכויות שמורות.
        </div>
      </footer>
    </div>
  );
}
