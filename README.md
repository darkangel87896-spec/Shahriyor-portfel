# Shahriyor-portfel
My personal portfolio 
<img width="1039" height="1026" alt="image" src="https://github.com/user-attachments/assets/77ce08e4-854e-4e0d-9905-98130acefd75" />
<img width="2489" height="814" alt="image" src="https://github.com/user-attachments/assets/ac0feb4e-4d8f-4e90-8655-653fb2d338c4" />
<img width="2478" height="1242" alt="image" src="https://github.com/user-attachments/assets/4b6bf5d0-e44d-4773-b418-3c3aa418adf4" />
<img width="2455" height="961" alt="image" src="https://github.com/user-attachments/assets/82a1aeb7-6187-45ab-9b7c-6d9339f758c7" />
#Bulutli saqlash — bu ma’lumotlarni internet orqali serverlarda saqlash texnologiyasi.
Google Drive
Dropbox
OneDrive
Afzalliklari:
Istalgan joydan kirish
Xotira tejaydi (kompyuterda joy band qilmaydi)
Avtomatik backup
🔐 2. Bulutli saqlash xavfsizligi
6

Bulutdagi ma’lumotlar himoyasi uchun ishlatiladigan asosiy usullar:

1. Shifrlash (Encryption)
Ma’lumotlar kodlanadi
Faqat kalit orqali ochiladi
Misol: AES encryption
2. Autentifikatsiya
Foydalanuvchini tekshirish
Masalan: login + parol
2 bosqichli himoya: Two-factor authentication
3. Ruxsat nazorati (Access Control)
Kim qanday faylni ko‘ra olishini boshqaradi
Admin, user, guest kabi rollar
🛡️ 3. Ma’lumotlar daxlsizligi (Data Integrity)
6

Ma’lumotlar daxlsizligi — ma’lumotlar o‘zgarmagan va to‘g‘ri saqlanganini kafolatlash.

Asosiy texnologiyalar:
1. Hash funksiyalar
Faylga maxsus kod beriladi
O‘zgarsa — kod ham o‘zgaradi
Misol: MD5
2. Checksum
Ma’lumot tekshirish usuli
Yuklab olingan fayl buzilmaganini aniqlaydi
3. Blockchain texnologiyasi
Ma’lumotni o‘zgartirib bo‘lmaydi
Har bir blok bog‘langan
⚙️ 4. Bulutli xavfsizlik muammolari
Ma’lumotlar o‘g‘irlanishi (hacking)
Parol buzilishi
Server hujumi (DDoS)
Ichki xodimlar xatolari
✅ 5. Himoya qilish usullari
Kuchli parol qo‘llash
2FA yoqish
Ma’lumotlarni shifrlash
VPN ishlatish
Doimiy backup qilish
#📌 6. Xulosa (Loyiha uchun tayyor matn)

#Bulutli saqlash zamonaviy IT tizimlarning asosiy qismi hisoblanadi. U ma’lumotlarni saqlash, ularga tez kirish va xavfsiz boshqarish imkonini beradi. Biroq, xavfsizlik muammolari sababli shifrlash, autentifikatsiya va ma’lumotlar daxlsizligini ta’minlovchi texnologiyalar muhim rol o‘ynaydi. Zamonaviy tizimlarda hash funksiyalar, blockchain va ko‘p bosqichli autentifikatsiya keng qo‘llaniladi.

import React, { useState, useEffect, useMemo, useRef } from 'react';
import { 
  Shield, Lock, Unlock, Key, FileText, Upload, Trash2, 
  AlertTriangle, CheckCircle, Activity, UserCheck, Eye, 
  EyeOff, Sparkles, RefreshCw, LayoutDashboard, Database, 
  Settings, Bell, Search, ChevronRight, Zap, Menu, X, Info,
  Fingerprint, ShieldCheck, FileSearch, Clock, Table, AlignLeft,
  FileDown, Printer, UserPlus, LogIn, Volume2, VolumeX, Plus, Minus,
  LogOut, Mic, MicOff, Waves, ShieldAlert, ShieldX, UserSquare2, Save
} from 'lucide-react';

const App = () => {
  const apiKey = ""; 
  const GEMINI_MODEL = "gemini-2.5-flash-preview-09-2025";
  const TTS_MODEL = "gemini-2.5-flash-preview-tts";
  const fileInputRef = useRef(null);

  const [isAuthenticated, setIsAuthenticated] = useState(false);
  const [isRegisterMode, setIsRegisterMode] = useState(false);
  const [loginValue, setLoginValue] = useState("");
  const [passwordValue, setPasswordValue] = useState("");
  const [authError, setAuthError] = useState("");
  
  const [users, setUsers] = useState([
    { login: "511-24guruh", password: "shahriyor" }
  ]);

  const [activeTab, setActiveTab] = useState('files'); 
  const [mfaEnabled, setMfaEnabled] = useState(true);
  const [encryptionActive, setEncryptionActive] = useState(true);
  const [scale, setScale] = useState(1);
  
  const [files, setFiles] = useState([
    { 
      id: 1, 
      name: 'shaxsiy_pasport.pdf', 
      size: '2.4 MB', 
      encrypted: true, 
      isVaultLocked: true, 
      date: '2026-03-15', 
      riskLevel: 'low',
      summary: 'O\'zbekiston fuqarolik pasporti skaneri. O\'ta maxfiy hujjat.',
      passportData: { fullName: "FAYZULLOEV AZIZBEK SHAHRIYOR O'G'LI", serial: "AA 1234567", group: "511-24GURUH" }
    },
    { 
      id: 2, 
      name: 'loyixa_reja.docx', 
      size: '850 KB', 
      encrypted: true, 
      isVaultLocked: false, 
      date: '2026-03-20', 
      riskLevel: 'medium',
      summary: 'Loyiha strategiyasi va 2026-yilgi ish rejasi.' 
    },
    { 
      id: 3, 
      name: 'moliyaviy_xisobot.xlsx', 
      size: '4.2 MB', 
      encrypted: false, 
      isVaultLocked: false, 
      date: '2026-03-25', 
      riskLevel: 'high',
      summary: '' 
    }
  ]);

  const [logs, setLogs] = useState([
    { id: 1, action: 'Tizim ishga tushirildi', time: '09:00', status: 'success' },
    { id: 2, action: 'MFA protokoli faol', time: '09:05', status: 'success' },
  ]);

  const [aiInsights, setAiInsights] = useState(null);
  const [isAnalyzing, setIsAnalyzing] = useState(false);
  const [activeSummaryId, setActiveSummaryId] = useState(null);
  const [searchQuery, setSearchQuery] = useState("");
  const [isSpeaking, setIsSpeaking] = useState(false);
  const [isListening, setIsListening] = useState(false);
  const [voiceQuery, setVoiceQuery] = useState("");

  const [authModal, setAuthModal] = useState({ show: false, fileId: null, callback: null });
  const [passwordInput, setPasswordInput] = useState("");
  const [viewingFile, setViewingFile] = useState(null);
  
  const [isPassModalOpen, setIsPassModalOpen] = useState(false);
  const [passForm, setPassForm] = useState({ fullName: '', serial: '', group: '' });

  const pcmToWav = (pcmBase64, sampleRate) => {
    try {
      const binaryString = window.atob(pcmBase64);
      const len = binaryString.length;
      const bytes = new Uint8Array(len);
      for (let i = 0; i < len; i++) bytes[i] = binaryString.charCodeAt(i);
      const buffer = bytes.buffer;
      const wavHeader = new ArrayBuffer(44);
      const view = new DataView(wavHeader);
      const writeString = (offset, string) => {
        for (let i = 0; i < string.length; i++) view.setUint8(offset + i, string.charCodeAt(i));
      };
      writeString(0, 'RIFF');
      view.setUint32(4, 36 + buffer.byteLength, true);
      writeString(8, 'WAVE');
      writeString(12, 'fmt ');
      view.setUint32(16, 16, true);
      view.setUint16(20, 1, true);
      view.setUint16(22, 1, true);
      view.setUint32(24, sampleRate, true);
      view.setUint32(28, sampleRate * 2, true);
      view.setUint16(32, 2, true);
      view.setUint16(34, 16, true);
      writeString(36, 'data');
      view.setUint32(40, buffer.byteLength, true);
      return URL.createObjectURL(new Blob([wavHeader, buffer], { type: 'audio/wav' }));
    } catch (e) { return null; }
  };

  const speakText = async (text) => {
    if (!text || isSpeaking) return;
    setIsSpeaking(true);
    try {
      const url = `https://generativelanguage.googleapis.com/v1beta/models/${TTS_MODEL}:generateContent?key=${apiKey}`;
      const payload = {
        contents: [{ parts: [{ text: `Professional o'zbek tilida, kiberxavfsizlik eksperti kabi gapiring: ${text}` }] }],
        generationConfig: { responseModalities: ["AUDIO"], speechConfig: { voiceConfig: { prebuiltVoiceConfig: { voiceName: "Kore" } } } }
      };
      const response = await fetch(url, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
      const result = await response.json();
      const audioPart = result.candidates?.[0]?.content?.parts?.find(p => p.inlineData);
      if (audioPart) {
        const audioData = audioPart.inlineData;
        const sampleRate = parseInt(audioData.mimeType.split('rate=')[1]) || 24000;
        const audioUrl = pcmToWav(audioData.data, sampleRate);
        const audio = new Audio(audioUrl);
        audio.onended = () => setIsSpeaking(false);
        audio.play();
      } else { setIsSpeaking(false); }
    } catch (error) { setIsSpeaking(false); }
  };

  const callGemini = async (prompt, systemInstruction = "") => {
    const url = `https://generativelanguage.googleapis.com/v1beta/models/${GEMINI_MODEL}:generateContent?key=${apiKey}`;
    const payload = { contents: [{ parts: [{ text: prompt }] }], systemInstruction: systemInstruction ? { parts: [{ text: systemInstruction }] } : undefined };
    const response = await fetch(url, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
    const data = await response.json();
    return data.candidates?.[0]?.content?.parts?.[0]?.text;
  };

  const startLiveConversation = () => {
    const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    if (!SpeechRecognition) {
      return;
    }
    const recognition = new SpeechRecognition();
    recognition.lang = 'uz-UZ';
    recognition.interimResults = false;
    recognition.onstart = () => { setIsListening(true); setVoiceQuery(""); };
    recognition.onresult = async (event) => {
      const transcript = event.results[0][0].transcript;
      setVoiceQuery(transcript);
      setIsListening(false);
      setIsAnalyzing(true);
      const systemMsg = "Siz CloudSafe kiberxavfsizlik yordamchisisiz. O'zbek tilida qisqa va professional javob bering. Xavf darajalarini ham tushuntiring.";
      try {
        const response = await callGemini(transcript, systemMsg);
        setAiInsights(response);
        addLog(`Ovozli savol berildi`, "success");
        speakText(response);
      } catch (e) { setAiInsights("AI bilan bog'lanishda xato."); }
      finally { setIsAnalyzing(false); }
    };
    recognition.onerror = () => setIsListening(false);
    recognition.onend = () => setIsListening(false);
    recognition.start();
  };

  const handleLogin = () => {
    const user = users.find(u => u.login === loginValue && u.password === passwordValue);
    if (user) { setIsAuthenticated(true); setAuthError(""); addLog(`Tizimga kirildi`, "success"); }
    else { setAuthError("Login yoki parol noto'g'ri!"); }
  };

  const handleFileUpload = (event) => {
    const file = event.target.files[0];
    if (!file) return;
    const newFile = { 
      id: Date.now(), 
      name: file.name, 
      size: `${(file.size / (1024 * 1024)).toFixed(2)} MB`, 
      encrypted: encryptionActive, 
      isVaultLocked: false, 
      date: new Date().toISOString().split('T')[0], 
      riskLevel: encryptionActive ? 'low' : 'high', 
      summary: '' 
    };
    setFiles([newFile, ...files]);
    addLog(`Fayl qo'shildi: ${file.name}`, "success");
  };

  const handleAddPassport = () => {
    if (!passForm.fullName || !passForm.serial) {
      return;
    }
    const newPassportFile = {
      id: Date.now(),
      name: `secure_data_${passForm.serial}.pasport`,
      size: '0.01 MB',
      encrypted: true,
      isVaultLocked: true, 
      date: new Date().toISOString().split('T')[0],
      riskLevel: 'low',
      summary: 'Kiritilgan shaxsiy pasport ma\'lumotlari. Shifrlangan.',
      passportData: { ...passForm }
    };
    setFiles([newPassportFile, ...files]);
    setPassForm({ fullName: '', serial: '', group: '' });
    setIsPassModalOpen(false);
    addLog(`Pasport ma'lumoti shifrlab qo'shildi`, "success");
  };

  const summarizeFile = async (file) => {
    setActiveSummaryId(file.id);
    const prompt = `Fayl: ${file.name}. Nimaligini va xavf darajasi (${file.riskLevel}) sababini 1 jumlada ayting.`;
    try {
      const res = await callGemini(prompt, "Siz fayl ekspertisiz.");
      setFiles(files.map(f => f.id === file.id ? { ...f, summary: res } : f));
      addLog(`AI tahlili yakunlandi`, "success");
    } catch (e) { addLog("Fayl tahlilida xato", "danger"); }
    finally { setActiveSummaryId(null); }
  };

  const tryOpenFile = (file) => {
    if (file.isVaultLocked) {
      setAuthModal({ show: true, fileId: file.id, callback: () => setViewingFile(file) });
    } else {
      setViewingFile(file);
    }
  };

  const handleReAuth = () => {
    if (passwordInput === "shahriyor") {
      authModal.callback();
      setAuthModal({ show: false, fileId: null, callback: null });
      setPasswordInput("");
    } else { }
  };

  const toggleVaultStatus = (id) => {
    setFiles(files.map(f => {
      if (f.id === id) {
        const isLocked = !f.isVaultLocked;
        return { ...f, isVaultLocked: isLocked, riskLevel: isLocked ? 'low' : (f.encrypted ? 'medium' : 'high') };
      }
      return f;
    }));
    addLog(`Qulflash holati o'zgardi`, "success");
  };

  const deleteFile = (id) => {
    setFiles(files.filter(f => f.id !== id));
    addLog("Fayl o'chirildi", "danger");
  };

  const addLog = (action, status) => {
    const newLog = { id: Date.now(), action, time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}), status };
    setLogs(prev => [newLog, ...prev]);
  };

  const filteredFiles = useMemo(() => files.filter(f => f.name.toLowerCase().includes(searchQuery.toLowerCase())), [files, searchQuery]);
  
  const securityScoreValue = useMemo(() => {
    let score = 20;
    if (mfaEnabled) score += 30;
    if (encryptionActive) score += 20;
    const vaultRatio = files.length ? (files.filter(f => f.isVaultLocked).length / files.length) * 30 : 30;
    return Math.round(score + vaultRatio);
  }, [mfaEnabled, encryptionActive, files]);

  const getRiskBadge = (level) => {
    switch(level) {
      case 'high': return <span className="bg-red-500/10 text-red-500 border border-red-500/20 px-3 py-1 rounded-full text-[10px] font-black uppercase flex items-center gap-1.5"><ShieldAlert size={12}/> Yuqori Xavf</span>;
      case 'medium': return <span className="bg-yellow-500/10 text-yellow-500 border border-yellow-500/20 px-3 py-1 rounded-full text-[10px] font-black uppercase flex items-center gap-1.5"><Shield size={12}/> O'rta Xavf</span>;
      default: return <span className="bg-emerald-500/10 text-emerald-500 border border-emerald-500/20 px-3 py-1 rounded-full text-[10px] font-black uppercase flex items-center gap-1.5"><ShieldCheck size={12}/> Xavfsiz</span>;
    }
  };

  if (!isAuthenticated) {
    return (
      <div className="min-h-screen bg-[#0a1128] flex items-center justify-center p-6 relative overflow-hidden text-white text-center">
        <div className="absolute inset-0 opacity-10 pointer-events-none" style={{ backgroundImage: 'radial-gradient(#d4af37 1px, transparent 1px)', backgroundSize: '40px 40px' }}></div>
        <div className="max-w-md w-full bg-slate-900/90 backdrop-blur-2xl border border-[#d4af37]/30 p-10 rounded-[40px] shadow-2xl relative z-10 animate-in zoom-in-95">
          <div className="flex flex-col items-center mb-10">
            <div className="w-24 h-24 bg-gradient-to-tr from-blue-700 to-blue-500 rounded-[32px] flex items-center justify-center shadow-xl mb-6 border border-white/20 animate-bounce-slow">
              <Shield size={48} className="text-white drop-shadow-lg" />
            </div>
            <h2 className="text-4xl font-black uppercase tracking-tighter">CloudSafe</h2>
            <p className="text-[#d4af37] text-[10px] font-black uppercase tracking-[0.4em] mt-2">Daxlsiz Milliy Bulut</p>
          </div>
          <div className="space-y-6">
            <div className="text-left space-y-2"><label className="text-[10px] font-black text-[#d4af37] uppercase ml-2 tracking-widest">Login</label>
              <input type="text" placeholder="" className="w-full bg-[#0a1128]/80 border border-white/10 rounded-2xl px-6 py-4 outline-none focus:border-[#d4af37] focus:ring-4 ring-[#d4af37]/10 text-white transition-all placeholder:text-slate-600" value={loginValue} onChange={e => setLoginValue(e.target.value)} />
            </div>
            <div className="text-left space-y-2"><label className="text-[10px] font-black text-[#d4af37] uppercase ml-2 tracking-widest">Parol</label>
              <input type="password" placeholder="" className="w-full bg-[#0a1128]/80 border border-white/10 rounded-2xl px-6 py-4 outline-none focus:border-[#d4af37] focus:ring-4 ring-[#d4af37]/10 text-white transition-all placeholder:text-slate-600" value={passwordValue} onChange={e => setPasswordValue(e.target.value)} />
            </div>
            {authError && <div className="bg-red-500/10 p-4 rounded-2xl text-red-400 text-xs font-bold animate-pulse text-left flex items-center gap-2"><AlertTriangle size={14} /> {authError}</div>}
            <button onClick={handleLogin} className="w-full py-5 bg-blue-600 rounded-[24px] font-black uppercase text-xs shadow-xl active:scale-95 transition-all text-white tracking-widest">Tizimga Kirish</button>
          </div>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-[#0a1128] text-slate-200 flex font-sans selection:bg-[#d4af37]/30 text-left">
      <input type="file" ref={fileInputRef} className="hidden" onChange={handleFileUpload} />

      {isPassModalOpen && (
        <div className="fixed inset-0 z-[200] flex items-center justify-center bg-black/90 backdrop-blur-xl p-6">
          <div className="max-w-xl w-full bg-[#1a1c24] border border-[#d4af37]/30 p-10 rounded-[48px] shadow-2xl animate-in zoom-in-95">
             <div className="flex items-center gap-4 mb-10">
                <div className="p-4 bg-[#d4af37]/20 rounded-2xl text-[#d4af37]"><UserSquare2 size={32} /></div>
                <div><h3 className="text-2xl font-black text-white uppercase tracking-tight">Pasport Ma'lumotlari</h3><p className="text-[10px] text-slate-500 font-black uppercase tracking-widest">Xavfsiz shifrlash tizimi</p></div>
             </div>
             <div className="space-y-6">
                <div><label className="text-[10px] font-black text-slate-500 uppercase ml-2 mb-2 block">Ism-Sharif (To'liq)</label>
                   <input type="text" className="w-full bg-[#0a1128] border border-white/5 rounded-2xl px-6 py-4 text-white outline-none focus:ring-2 ring-[#d4af37]" value={passForm.fullName} onChange={e => setPassForm({...passForm, fullName: e.target.value})} placeholder="" />
                </div>
                <div className="grid grid-cols-2 gap-6">
                   <div><label className="text-[10px] font-black text-slate-500 uppercase ml-2 mb-2 block">Seriya va Raqam</label>
                      <input type="text" className="w-full bg-[#0a1128] border border-white/5 rounded-2xl px-6 py-4 text-white outline-none focus:ring-2 ring-[#d4af37]" value={passForm.serial} onChange={e => setPassForm({...passForm, serial: e.target.value})} placeholder="" />
                   </div>
                   <div><label className="text-[10px] font-black text-slate-500 uppercase ml-2 mb-2 block">Guruh / Bo'lim</label>
                      <input type="text" className="w-full bg-[#0a1128] border border-white/5 rounded-2xl px-6 py-4 text-white outline-none focus:ring-2 ring-[#d4af37]" value={passForm.group} onChange={e => setPassForm({...passForm, group: e.target.value})} placeholder="" />
                   </div>
                </div>
                <div className="flex gap-4 pt-6">
                   <button onClick={() => setIsPassModalOpen(false)} className="flex-1 py-5 bg-slate-800 rounded-3xl font-black uppercase text-[11px] text-slate-400">Yopish</button>
                   <button onClick={handleAddPassport} className="flex-1 py-5 bg-[#d4af37] rounded-3xl font-black uppercase text-[11px] text-black flex items-center justify-center gap-2"><Save size={18} /> Shifrlab saqlash</button>
                </div>
             </div>
          </div>
        </div>
      )}

      {authModal.show && (
        <div className="fixed inset-0 z-[200] flex items-center justify-center bg-black/90 backdrop-blur-xl p-6">
          <div className="max-w-md w-full bg-[#1a1c24] border border-[#d4af37]/30 p-10 rounded-[40px] text-center shadow-2xl animate-in zoom-in-95">
            <Fingerprint size={80} className="text-[#d4af37] mx-auto mb-8 animate-pulse" />
            <h3 className="text-2xl font-black text-white mb-2 uppercase tracking-widest text-center">Maxfiy Ruxsat</h3>
            <p className="text-slate-500 text-sm mb-8 text-center">Ushbu ma'lumot qulflangan. Parolni kiriting.</p>
            <input type="password" placeholder="" className="w-full bg-[#0a1128] border border-white/5 rounded-2xl px-6 py-4 text-white mb-6 text-center outline-none focus:ring-2 ring-[#d4af37]" value={passwordInput} onChange={e => setPasswordInput(e.target.value)} autoFocus onKeyDown={e => e.key === 'Enter' && handleReAuth()} />
            <div className="flex gap-4"><button onClick={() => setAuthModal({show:false})} className="flex-1 py-4 bg-slate-800 rounded-2xl font-bold uppercase text-[10px] text-slate-400">Yopish</button><button onClick={handleReAuth} className="flex-1 py-4 bg-[#d4af37] rounded-2xl font-bold uppercase text-[10px] text-black">Kirish</button></div>
          </div>
        </div>
      )}

      {viewingFile && (
        <div className="fixed inset-0 z-[150] flex items-center justify-center bg-black/95 backdrop-blur-2xl p-4 md:p-10">
          <div className="w-full h-full max-w-6xl bg-slate-900 rounded-[48px] flex flex-col border border-white/5 shadow-2xl overflow-hidden animate-in zoom-in-95">
            <div className="p-8 border-b border-white/5 flex justify-between items-center bg-slate-950/50">
              <div className="flex items-center gap-5 text-left">
                <div className="p-3 bg-blue-600 rounded-2xl shadow-lg"><FileText className="text-white" /></div>
                <div className="text-left">
                  <h3 className="text-white font-black text-xl tracking-tight text-left">{viewingFile.name}</h3>
                  <p className="text-[10px] text-slate-500 uppercase font-black text-left">{viewingFile.size}</p>
                </div>
              </div>
              <button onClick={() => setViewingFile(null)} className="p-4 bg-slate-800 hover:bg-red-500 text-white rounded-[24px] transition-all"><X size={24} /></button>
            </div>
            <div className="flex-1 overflow-y-auto p-12 text-left bg-slate-950/30 custom-scrollbar text-left">
               {viewingFile.name.includes('pasport') ? (
                 <div className="max-w-xl mx-auto space-y-12 animate-in slide-in-from-bottom-10 text-center">
                    <div className="w-56 h-72 bg-slate-800 rounded-[40px] border-4 border-[#d4af37]/30 mx-auto flex items-center justify-center relative overflow-hidden shadow-2xl">
                      <UserCheck size={100} className="text-blue-500/10 mx-auto" />
                      <div className="absolute inset-x-0 bottom-0 p-5 bg-[#d4af37] text-black text-[10px] font-black uppercase text-center tracking-widest">RASMIY KO'RINISH</div>
                    </div>
                    <div className="bg-[#1a1c24] border border-white/5 p-10 rounded-[48px] space-y-6 text-left shadow-2xl">
                       <div className="border-b border-white/5 pb-4 text-left">
                          <p className="text-[10px] text-slate-500 uppercase font-black mb-1 text-left">ISM-SHARIF</p>
                          <p className="text-white font-black text-2xl uppercase text-left">{viewingFile.passportData?.fullName || "FAYZULLOEV AZIZBEK SHAHRIYOR O'G'LI"}</p>
                       </div>
                       <div className="grid grid-cols-2 gap-8 text-left">
                          <div className="text-left"><p className="text-[10px] text-slate-500 uppercase font-black mb-1 text-left">Seriya</p><p className="text-white font-bold text-lg text-left">{viewingFile.passportData?.serial || "AA 1234567"}</p></div>
                          <div className="text-left"><p className="text-[10px] text-slate-500 uppercase font-black mb-1 text-left">Guruh</p><p className="text-[#d4af37] font-black text-lg uppercase tracking-tighter text-left">{viewingFile.passportData?.group || "511-24GURUH"}</p></div>
                       </div>
                    </div>
                 </div>
               ) : (
                 <div className="max-w-4xl mx-auto bg-white p-16 md:p-24 rounded-3xl shadow-2xl text-slate-800 text-left animate-in fade-in">
                    <h4 className="text-3xl font-black text-slate-900 mb-8 border-b-2 pb-6 uppercase text-left">{viewingFile.name}</h4>
                    <div className="space-y-8 text-lg text-slate-600 leading-relaxed text-left">
                       <p className="font-bold text-blue-600 uppercase text-left">Loyiha tahlili</p>
                       <p className="text-left">Ushbu fayl CloudSafe milliy bulut ekotizimida xavfsiz holatda saqlanmoqda. Gemini AI buni nazorat qiladi.</p>
                       <p className="text-left">Xavfsizlik darajasi: Yuqori (AES-256 shifrlash faol).</p>
                    </div>
                 </div>
               )}
            </div>
          </div>
        </div>
      )}

      <aside className="w-72 bg-[#1a1c24] border-r border-white/5 flex flex-col p-6 h-screen sticky top-0 text-left z-40">
        <div className="flex items-center gap-4 mb-12 text-left">
          <div className="bg-[#d4af37] p-2.5 rounded-2xl shadow-xl shadow-[#d4af37]/10"><Zap className="text-black" size={24} /></div>
          <span className="text-2xl font-black text-white tracking-tighter uppercase text-left">CLOUDSAFE</span>
        </div>
        <nav className="space-y-2 flex-1 text-left">
          {[
            { id: 'dashboard', icon: LayoutDashboard, label: 'Bosh sahifa' },
            { id: 'files', icon: Database, label: 'Fayllar ombori' },
            { id: 'security', icon: Shield, label: 'Xavfsizlik markazi' },
          ].map(item => (
            <button key={item.id} onClick={() => setActiveTab(item.id)} className={`w-full flex items-center gap-4 px-6 py-4 rounded-2xl transition-all ${activeTab === item.id ? 'bg-[#d4af37] text-black font-black shadow-lg shadow-[#d4af37]/20' : 'text-slate-500 hover:bg-[#252836] font-bold uppercase text-[11px] tracking-widest'}`}>
              <item.icon size={20} />
              <span className="text-left">{item.label}</span>
            </button>
          ))}
        </nav>
        <button onClick={() => setIsAuthenticated(false)} className="mt-auto flex items-center gap-4 px-6 py-4 rounded-2xl text-slate-500 hover:text-red-400 font-black uppercase text-[10px] tracking-widest transition-all"><LogOut size={18} /> Chiqish</button>
      </aside>

      <main className="flex-1 flex flex-col h-screen overflow-hidden text-left relative bg-[radial-gradient(circle_at_top_right,_rgba(212,175,55,0.03),_transparent)]">
        <header className="h-24 border-b border-white/5 flex items-center justify-between px-10 bg-[#0f1115]/50 backdrop-blur-md sticky top-0 z-30">
          <div className="relative text-left flex-1 max-w-xl">
            <Search className="absolute left-4 top-1/2 -translate-y-1/2 w-4 h-4 text-slate-500" />
            <input type="text" placeholder="" className="bg-[#1a1c24] border border-white/5 rounded-2xl pl-12 pr-6 py-3 text-sm w-full outline-none focus:ring-2 ring-[#d4af37] transition-all text-white placeholder:text-slate-600" value={searchQuery} onChange={e => setSearchQuery(e.target.value)} />
          </div>
          <div className="flex items-center gap-6 text-right">
            <div className="flex flex-col text-right"><span className="text-sm font-black text-white uppercase tracking-tight">{loginValue || "Admin"}</span><span className="text-[10px] text-[#d4af37] font-black uppercase tracking-[0.2em]">ULTRA SECURE</span></div>
            <div className="w-12 h-12 rounded-2xl bg-gradient-to-br from-[#d4af37] to-yellow-600 flex items-center justify-center shadow-xl shadow-yellow-600/10 border border-white/10"><UserCheck className="text-black" size={24} /></div>
          </div>
        </header>

        <div className="flex-1 overflow-y-auto p-10 custom-scrollbar text-left">
          
          {activeTab === 'dashboard' && (
            <div className="animate-in fade-in slide-in-from-bottom-6 space-y-10 text-left">
              <div className="grid grid-cols-1 md:grid-cols-2 gap-8 text-left">
                <div className="bg-[#1a1c24] border border-white/5 p-8 rounded-[40px] shadow-2xl relative overflow-hidden group text-left">
                   <ShieldCheck className="text-emerald-500 mb-6 group-hover:scale-110 transition-transform" size={48} />
                   <h3 className="text-4xl font-black text-white text-left">{securityScoreValue}%</h3>
                   <p className="text-xs text-slate-500 font-black uppercase tracking-widest mt-2 text-left">Xavfsizlik Indeksi</p>
                   <div className="mt-6 h-2 w-full bg-[#0f1115] rounded-full overflow-hidden text-left"><div className="h-full bg-emerald-500 transition-all duration-1000 shadow-[0_0_15px_rgba(16,185,129,0.5)] text-left" style={{width: `${securityScoreValue}%`}}></div></div>
                </div>

                <div className="bg-gradient-to-br from-blue-900/40 via-[#1a1c24] to-[#1a1c24] border border-[#d4af37]/20 p-12 rounded-[56px] shadow-2xl relative overflow-hidden group text-left">
                   <div className="flex items-center justify-between mb-8 text-left">
                      <div className="flex items-center gap-5 text-left">
                        <div className={`p-4 rounded-3xl transition-all duration-500 ${isListening ? 'bg-red-600 shadow-[0_0_30px_rgba(220,38,38,0.5)] scale-110' : 'bg-[#d4af37]/20'}`}>
                          <Mic size={32} className={`${isListening ? 'text-white animate-pulse' : 'text-[#d4af37]'}`} />
                        </div>
                        <h3 className="text-3xl font-black text-white uppercase tracking-tighter text-left">JONLI MULOQOT ✨</h3>
                      </div>
                      
                      <div className="flex gap-4">
                        {aiInsights && (
                          <button onClick={() => speakText(aiInsights)} disabled={isSpeaking} className={`p-4 rounded-2xl transition-all ${isSpeaking ? 'bg-[#d4af37] text-black shadow-xl animate-pulse' : 'bg-white/5 hover:bg-white/10'}`}>
                            {isSpeaking ? <Volume2 size={24} /> : <VolumeX size={24} />}
                          </button>
                        )}
                        <button 
                          onClick={startLiveConversation} 
                          disabled={isListening || isAnalyzing}
                          className={`flex items-center gap-3 px-8 py-4 rounded-2xl font-black uppercase text-[11px] tracking-widest transition-all ${isListening ? 'bg-red-600 text-white' : 'bg-[#d4af37] text-black hover:scale-105 active:scale-95'}`}
                        >
                          {isListening ? <Waves className="animate-bounce" size={18} /> : <Mic size={18} />}
                          {isListening ? 'Sizni eshitmoqdaman...' : 'Savol berish ✨'}
                        </button>
                      </div>
                   </div>

                   <div className="min-h-[120px] text-left">
                      {isAnalyzing ? (
                        <div className="flex items-center gap-4 py-8">
                          <RefreshCw className="animate-spin text-[#d4af37]" />
                          <p className="text-slate-400 font-bold uppercase text-xs tracking-widest">Gemini o'ylamoqda...</p>
                        </div>
                      ) : (
                        <div className="space-y-4 text-left">
                          {voiceQuery && <div className="text-xs text-[#d4af37] font-black uppercase tracking-widest opacity-60">Savolingiz: "{voiceQuery}"</div>}
                          {aiInsights ? (
                            <div className="text-slate-300 leading-relaxed font-medium text-left border-l-4 border-[#d4af37] pl-6 py-2 bg-black/20 rounded-r-2xl">
                              {aiInsights}
                            </div>
                          ) : (
                            <div className="py-6 border border-white/5 border-dashed rounded-3xl text-center">
                              <p className="text-slate-500 text-sm italic">"Savol berish" tugmasini bosing va o'zbek tilida kiberxavfsizlik haqida savol bering.</p>
                            </div>
                          )}
                        </div>
                      )}
                   </div>
                </div>
              </div>
            </div>
          )}

          {activeTab === 'files' && (
            <div className="animate-in fade-in slide-in-from-right-6 space-y-10 text-left max-w-7xl mx-auto">
               <div className="flex justify-between items-center text-left mb-4">
                  <div className="text-left">
                    <h2 className="text-4xl font-black text-white uppercase tracking-tighter text-left">Fayllar ombori</h2>
                    <p className="text-slate-500 text-sm italic font-medium mt-2 text-left">Ma'lumotlar boshqaruvi va Xavf tahlili ✨</p>
                  </div>
                  
                  <div className="flex items-center gap-4">
                    <button 
                      onClick={() => setIsPassModalOpen(true)} 
                      className="flex items-center gap-3 px-8 py-5 bg-emerald-600 text-white rounded-[28px] font-black uppercase text-[11px] tracking-widest transition-all shadow-xl hover:bg-emerald-700 active:scale-95"
                    >
                      <UserSquare2 size={20} /> Pasport Qo'shish
                    </button>
                    
                    <button 
                      onClick={() => fileInputRef.current.click()} 
                      className="flex items-center gap-3 px-8 py-5 bg-[#d4af37] text-black rounded-[28px] font-black uppercase text-[11px] tracking-[0.2em] transition-all shadow-[0_20px_40px_rgba(212,175,55,0.2)] hover:scale-105 active:scale-95"
                    >
                      <Plus size={20} /> Fayl Qo'shish
                    </button>

                    <div className="flex items-center gap-4 bg-[#1a1c24] p-3 rounded-2xl border border-white/5 shadow-xl">
                      <button onClick={() => setScale(Math.max(0.7, scale - 0.1))} className="p-2 bg-slate-800 hover:bg-slate-700 rounded-xl text-[#d4af37] active:scale-90 transition-all"><Minus size={18} /></button>
                      <span className="text-xs font-black text-white w-14 text-center">{Math.round(scale * 100)}%</span>
                      <button onClick={() => setScale(Math.min(1.3, scale + 0.1))} className="p-2 bg-slate-800 hover:bg-slate-700 rounded-xl text-[#d4af37] active:scale-90 transition-all"><Plus size={18} /></button>
                    </div>
                  </div>
               </div>

               <div className="grid grid-cols-1 gap-10 pb-32">
                  {filteredFiles.map(file => (
                    <div 
                      key={file.id} 
                      style={{ transform: `scale(${scale})`, transformOrigin: 'center center' }}
                      className={`bg-[#1a1c24] border ${file.riskLevel === 'high' ? 'border-red-500/40 shadow-red-500/5' : file.isVaultLocked ? 'border-[#d4af37]/40 shadow-[#d4af37]/5' : 'border-white/5'} p-10 rounded-[48px] flex flex-col items-center group hover:border-[#d4af37]/60 transition-all duration-300 shadow-2xl relative overflow-hidden`}
                    >
                      <div className="absolute inset-0 opacity-0 group-hover:opacity-5 pointer-events-none transition-opacity" style={{ backgroundImage: 'radial-gradient(#d4af37 1px, transparent 1px)', backgroundSize: '20px 20px' }}></div>

                      <div className="absolute top-8 right-8">
                         {getRiskBadge(file.riskLevel)}
                      </div>

                      <div className="w-full flex flex-col items-center text-center z-10 mb-10">
                        <div className={`p-8 rounded-[40px] transition-all duration-500 mb-8 ${file.isVaultLocked ? 'bg-[#d4af37]/10 text-[#d4af37]' : file.riskLevel === 'high' ? 'bg-red-500/10 text-red-500' : 'bg-[#252836] text-blue-400'} group-hover:scale-110`}>
                          {file.isVaultLocked ? <Lock size={60} /> : <FileText size={60} />}
                        </div>
                        <h2 className="text-3xl font-black text-white group-hover:text-[#d4af37] transition-colors tracking-tight uppercase mb-4 text-center">{file.name}</h2>
                        <p className="text-[12px] text-slate-500 uppercase font-black tracking-[0.3em] flex items-center gap-3">
                           <Clock size={14} /> {file.date} <span className="opacity-20">•</span> <Database size={14} /> {file.size}
                        </p>
                        
                        {file.summary && (
                          <div className="mt-8 flex items-start gap-4 bg-[#d4af37]/5 p-6 rounded-3xl border border-[#d4af37]/10 animate-in fade-in max-w-2xl text-left">
                             <p className="text-sm text-[#d4af37]/90 italic flex-1 leading-relaxed text-left font-medium">"{file.summary}"</p>
                             <button onClick={() => speakText(file.summary)} className="p-3 bg-[#d4af37]/10 rounded-xl text-[#d4af37] hover:bg-[#d4af37] hover:text-black transition-all"><Volume2 size={20} /></button>
                          </div>
                        )}
                      </div>

                      <div className="flex items-center gap-6 z-10">
                         <button onClick={() => tryOpenFile(file)} className="flex items-center gap-4 px-12 py-5 bg-[#d4af37] text-black rounded-[28px] font-black uppercase text-[13px] tracking-widest transition-all shadow-[0_15px_30px_rgba(212,175,55,0.3)] hover:scale-105 active:scale-95">
                           <Eye size={22} /> KO'RISH
                         </button>

                         <button onClick={() => toggleVaultStatus(file.id)} className={`p-5 rounded-[24px] transition-all shadow-xl border-2 ${file.isVaultLocked ? 'bg-red-600 text-white border-red-500' : 'bg-[#252836] text-slate-400 border-white/5 hover:border-[#d4af37] hover:text-[#d4af37]'}`} title={file.isVaultLocked ? "Qulfni ochish" : "Faylni qulflash"}>
                           {file.isVaultLocked ? <Lock size={28} /> : <Unlock size={28} />}
                         </button>

                         <button onClick={() => summarizeFile(file)} disabled={activeSummaryId === file.id} className="p-5 bg-purple-600/10 text-purple-400 rounded-[24px] border-2 border-purple-500/20 hover:bg-purple-600 hover:text-white transition-all disabled:opacity-30 shadow-xl">
                           {activeSummaryId === file.id ? <RefreshCw size={28} className="animate-spin" /> : <Sparkles size={28} />}
                         </button>

                         <button onClick={() => deleteFile(file.id)} className="p-5 bg-red-600/10 text-red-500 rounded-[24px] hover:bg-red-600 hover:text-white transition-all shadow-xl">
                            <Trash2 size={28} />
                         </button>
                      </div>
                    </div>
                  ))}
               </div>
            </div>
          )}

          {activeTab === 'security' && (
            <div className="animate-in fade-in slide-in-from-top-10 space-y-12 text-left">
               <h2 className="text-4xl font-black text-white uppercase tracking-tighter text-left">Xavfsizlik Markazi</h2>
               <div className="grid grid-cols-1 md:grid-cols-2 gap-12 text-left">
                  <div className="bg-[#1a1c24] border border-white/5 p-12 rounded-[56px] group hover:border-blue-500/30 transition-all shadow-2xl text-left">
                     <div className="flex justify-between items-center mb-10 text-left"><Key size={40} className="text-blue-500" /><div className={`w-14 h-7 rounded-full relative cursor-pointer transition-all duration-500 ${mfaEnabled ? 'bg-blue-600 shadow-[0_0_20px_rgba(59,130,246,0.5)]' : 'bg-slate-800'}`} onClick={() => setMfaEnabled(!mfaEnabled)}><div className={`absolute top-1.5 w-5 h-5 bg-white rounded-full transition-all ${mfaEnabled ? 'right-1.5' : 'left-1.5'}`}></div></div></div>
                     <h3 className="text-2xl font-black text-white mb-4 uppercase text-left">MFA Autentifikatsiya</h3><p className="text-slate-500 leading-relaxed text-base font-medium opacity-80 text-left">Ikki bosqichli tekshiruv ruxsatsiz kirishni 99.9% ga kamaytiradi.</p>
                  </div>
                  <div className="bg-[#1a1c24] border border-white/5 p-12 rounded-[56px] group hover:border-purple-500/30 transition-all shadow-2xl text-left">
                     <div className="flex justify-between items-center mb-10 text-left"><Lock size={40} className="text-purple-500" /><div className={`w-16 h-8 rounded-full relative cursor-pointer transition-all duration-500 ${encryptionActive ? 'bg-purple-600 shadow-[0_0_168,85,247,0.5)]' : 'bg-slate-800'}`} onClick={() => setEncryptionActive(!encryptionActive)}><div className={`absolute top-1.5 w-5 h-5 bg-white rounded-full transition-all ${encryptionActive ? 'right-1.5' : 'left-1.5'}`}></div></div></div>
                     <h3 className="text-2xl font-black text-white mb-4 uppercase text-left tracking-tight">AES-256 Shifrlash</h3><p className="text-slate-500 leading-relaxed text-base font-medium opacity-80 text-left">Yangi yuklanadigan barcha fayllar avtomatik ravishda harbiy darajadagi shifrlash algoritmlari bilan himoyalanadi.</p>
                  </div>
               </div>
            </div>
          )}
        </div>
      </main>

      <style dangerouslySetInnerHTML={{ __html: `
        .custom-scrollbar::-webkit-scrollbar { width: 6px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: transparent; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #1e293b; border-radius: 10px; border: 2px solid transparent; background-clip: content-box; }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #d4af37; }
        @keyframes bounce-slow { 0%, 100% { transform: translateY(-5%); } 50% { transform: translateY(0); } }
        .animate-bounce-slow { animation: bounce-slow 4s infinite ease-in-out; }
      `}} />
    </div>
  );
};

export default App;
