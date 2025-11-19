<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Гімназійна Рада | Платформа</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- React & ReactDOM -->
    <script type="importmap">
        {
            "imports": {
                "react": "https://esm.sh/react@18.2.0",
                "react-dom/client": "https://esm.sh/react-dom@18.2.0/client"
            }
        }
    </script>
    
    <!-- Babel for JSX compilation in browser -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <style>
        :root {
            --primary: #1e3a5f;
            --primary-light: #2c5282;
            --accent: #10b981;
            --accent-light: #34d399;
        }
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; }
        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; height: 8px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel" data-type="module">
        import React, { useState, useEffect, useRef } from 'react';
        import { createRoot } from 'react-dom/client';
        
        // Firebase Imports (ESM)
        import { initializeApp } from 'https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js';
        import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-analytics.js";
        import { 
            getAuth, 
            createUserWithEmailAndPassword,
            signInWithEmailAndPassword,
            signInWithPopup,
            GoogleAuthProvider,
            onAuthStateChanged, 
            updateProfile,
            signOut,
            signInAnonymously,
            signInWithCustomToken
        } from 'https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js';
        import { 
            getFirestore, 
            collection, 
            addDoc, 
            updateDoc, 
            deleteDoc, 
            doc, 
            query, 
            where, 
            orderBy, 
            onSnapshot, 
            setDoc,
            getDoc,
            getDocs,
            limit,
            serverTimestamp
        } from 'https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js';

        // Icons & Utilities
        import { 
            Home, MessageSquare, CheckSquare, Vote, Megaphone, FolderOpen, 
            Settings, Menu, X, LogOut, User as UserIcon, Calendar as CalendarIcon,
            Plus, Search, Trash2, Edit, ArrowLeft, Send, Hash, Lock, Users,
            Clock, AlertCircle, ArrowRight, TrendingUp, Filter, Download,
            FileText, File, MoreVertical, Move, Power, Shield, Activity,
            Briefcase, Building, Camera, Save, CheckCircle2, Bell, ChevronLeft, ChevronRight, Folder, FolderPlus, Upload, LayoutTemplate, Eye, CornerDownLeft, UserPlus, Pencil, FileIcon, MoreHorizontal, FileSpreadsheet, RefreshCw, XCircle
        } from 'https://esm.sh/lucide-react@0.294.0?external=react';
        
        import { format, startOfMonth, endOfMonth, eachDayOfInterval, isSameDay, addMonths, subMonths, parseISO } from 'https://esm.sh/date-fns@2.30.0';
        import { uk } from 'https://esm.sh/date-fns@2.30.0/locale';

        // --- FIREBASE SETUP ---
        // ВАШІ КЛЮЧІ (vhr2-0)
        const firebaseConfig = {
            apiKey: "AIzaSyBOCGP-PAdxhohSUjIbhlb2W_PvMAi9__4",
            authDomain: "vhr2-0.firebaseapp.com",
            projectId: "vhr2-0",
            storageBucket: "vhr2-0.firebasestorage.app",
            messagingSenderId: "637700407984",
            appId: "1:637700407984:web:6da5b14cbf2a7e089c7175",
            measurementId: "G-L11R2GYC9X"
        };

        // Ініціалізація з вашими ключами напряму
        const app = initializeApp(firebaseConfig);
        const analytics = getAnalytics(app);
        const auth = getAuth(app);
        const db = getFirestore(app);
        const googleProvider = new GoogleAuthProvider();
        
        // Використовуємо ваш App ID як ідентифікатор колекції
        const appId = "vhr2-0-production"; 

        // Paths helper
        const getCollectionRef = (colName) => collection(db, 'artifacts', appId, 'public', 'data', colName);

        // Logger helper
        const logAction = async (user, action, entity, details) => {
            if (!user) return;
            try {
                await addDoc(getCollectionRef('audit_logs'), {
                    action,
                    entity,
                    details,
                    performed_by: user.full_name || user.email,
                    user_id: user.id,
                    created_date: new Date().toISOString()
                });
            } catch (e) {
                console.error("Failed to log action", e);
            }
        };

        // --- UI COMPONENTS ---

        const Button = ({ className, variant = "default", size = "default", ...props }) => {
            const variants = {
                default: "bg-[var(--primary)] text-white hover:bg-[var(--primary-light)] shadow-sm",
                destructive: "bg-red-500 text-white hover:bg-red-600 shadow-sm",
                outline: "border border-gray-200 bg-white hover:bg-gray-50 text-gray-900",
                ghost: "hover:bg-gray-100 hover:text-gray-900",
                link: "text-[var(--primary)] underline-offset-4 hover:underline",
                success: "bg-emerald-400 hover:bg-emerald-500 text-white shadow-sm font-semibold"
            };
            const sizes = {
                default: "h-10 px-4 py-2",
                sm: "h-9 rounded-md px-3 text-xs",
                lg: "h-11 rounded-md px-8",
                icon: "h-10 w-10",
            };
            const classes = `inline-flex items-center justify-center rounded-lg text-sm font-medium transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[var(--primary)] disabled:pointer-events-none disabled:opacity-50 ${variants[variant]} ${sizes[size]} ${className || ''}`;
            return <button className={classes} {...props} />;
        };

        const Input = ({ className, ...props }) => {
            const classes = `flex h-10 w-full rounded-lg border border-gray-300 bg-white px-3 py-2 text-sm file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-gray-500 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[var(--primary)] disabled:cursor-not-allowed disabled:opacity-50 ${className || ''}`;
            return <input className={classes} {...props} />;
        };

        const Textarea = ({ className, ...props }) => {
            const classes = `flex min-h-[80px] w-full rounded-lg border border-gray-300 bg-white px-3 py-2 text-sm placeholder:text-gray-500 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[var(--primary)] disabled:cursor-not-allowed disabled:opacity-50 ${className || ''}`;
            return <textarea className={classes} {...props} />;
        };

        const Card = ({ className, ...props }) => {
            const classes = `rounded-xl border bg-white text-gray-950 shadow-sm ${className || ''}`;
            return <div className={classes} {...props} />;
        };

        const CardHeader = ({ className, ...props }) => <div className={`flex flex-col space-y-1.5 p-6 ${className || ''}`} {...props} />;
        const CardTitle = ({ className, ...props }) => <h3 className={`text-2xl font-semibold leading-none tracking-tight ${className || ''}`} {...props} />;
        const CardContent = ({ className, ...props }) => <div className={`p-6 pt-0 ${className || ''}`} {...props} />;

        const Badge = ({ className, variant = "default", ...props }) => {
            const classes = `inline-flex items-center rounded-full border px-2.5 py-0.5 text-xs font-semibold transition-colors focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2 ${className || ''}`;
            return <div className={classes} {...props} />;
        };

        const Dialog = ({ open, onOpenChange, children }) => {
            if (!open) return null;
            return (
                <div className="fixed inset-0 z-[100] flex items-center justify-center p-4 sm:p-0">
                    <div className="fixed inset-0 bg-black/50 backdrop-blur-sm transition-opacity" onClick={() => onOpenChange(false)} />
                    <div className="fixed z-[100] grid w-full max-w-lg gap-4 bg-white p-6 shadow-lg duration-200 sm:rounded-xl md:w-full max-h-[90vh] overflow-y-auto animate-in fade-in zoom-in-95">
                        {children}
                        <button className="absolute right-4 top-4 rounded-sm opacity-70 ring-offset-white transition-opacity hover:opacity-100 focus:outline-none" onClick={() => onOpenChange(false)}>
                            <X className="h-4 w-4" />
                            <span className="sr-only">Close</span>
                        </button>
                    </div>
                </div>
            );
        };
        const DialogContent = ({ children, className }) => <div className={className || ''}>{children}</div>;
        const DialogHeader = ({ className, ...props }) => <div className={`flex flex-col space-y-1.5 text-center sm:text-left mb-4 ${className || ''}`} {...props} />;
        const DialogTitle = ({ className, ...props }) => <h2 className={`text-lg font-semibold leading-none tracking-tight ${className || ''}`} {...props} />;

        const Tabs = ({ defaultValue, className, children }) => {
            const [activeTab, setActiveTab] = useState(defaultValue);
            return (
                <div className={className || ''}>
                    {React.Children.map(children, child => {
                        if (React.isValidElement(child)) {
                            return React.cloneElement(child, { activeTab, setActiveTab });
                        }
                        return child;
                    })}
                </div>
            );
        };
        const TabsList = ({ className, children, activeTab, setActiveTab }) => (
            <div className={`inline-flex h-10 items-center justify-center rounded-lg bg-gray-100 p-1 text-gray-500 ${className || ''}`}>
                {React.Children.map(children, child => React.cloneElement(child, { activeTab, setActiveTab }))}
            </div>
        );
        const TabsTrigger = ({ value, children, activeTab, setActiveTab, className }) => {
            const isActive = activeTab === value;
            const classes = `inline-flex items-center justify-center whitespace-nowrap rounded-md px-3 py-1.5 text-sm font-medium ring-offset-white transition-all focus-visible:outline-none disabled:pointer-events-none disabled:opacity-50 ${isActive ? "bg-white text-gray-950 shadow-sm" : "hover:bg-gray-200 hover:text-gray-900"} ${className || ''}`;
            return (
                <button onClick={() => setActiveTab(value)} className={classes}>
                    {children}
                </button>
            );
        };
        const TabsContent = ({ value, activeTab, children, className }) => {
            if (value !== activeTab) return null;
            return <div className={`mt-2 ring-offset-white focus-visible:outline-none ${className || ''}`}>{children}</div>;
        };

        // --- COMPONENTS ---

        function NotificationBell({ user, setPage }) {
            const [notifications, setNotifications] = useState([]);
            const [isOpen, setIsOpen] = useState(false);
            const dropdownRef = useRef(null);

            useEffect(() => {
                const mock = [
                    { id: 1, title: 'Ласкаво просимо', content: 'Вітаємо на платформі!', read: false, date: new Date() },
                ];
                setNotifications(mock);
            }, []);
            
            useEffect(() => {
                function handleClickOutside(event) {
                    if (dropdownRef.current && !dropdownRef.current.contains(event.target)) {
                        setIsOpen(false);
                    }
                }
                document.addEventListener("mousedown", handleClickOutside);
                return () => document.removeEventListener("mousedown", handleClickOutside);
            }, [dropdownRef]);

            const unread = notifications.filter(n => !n.read).length;

            return (
                <div className="relative" ref={dropdownRef}>
                    <button onClick={() => setIsOpen(!isOpen)} className="p-2 rounded-full hover:bg-gray-100 relative">
                        <Bell className="w-6 h-6 text-gray-600"/>
                        {unread > 0 && <span className="absolute top-1 right-1 w-4 h-4 bg-red-500 rounded-full text-[10px] text-white flex items-center justify-center">{unread}</span>}
                    </button>
                    
                    {isOpen && (
                        <div className="absolute right-0 mt-2 w-80 bg-white rounded-xl shadow-xl border border-gray-100 z-50 overflow-hidden animate-in fade-in zoom-in-95">
                            <div className="p-3 border-b bg-gray-50 font-semibold text-sm">Сповіщення</div>
                            <div className="max-h-80 overflow-y-auto">
                                {notifications.map(n => (
                                    <div key={n.id} className={`p-3 border-b hover:bg-blue-50 cursor-pointer ${!n.read ? 'bg-blue-50/50' : ''}`} onClick={() => setIsOpen(false)}>
                                        <p className="text-sm font-medium text-gray-900">{n.title}</p>
                                        <p className="text-xs text-gray-500 mt-1">{n.content}</p>
                                    </div>
                                ))}
                            </div>
                        </div>
                    )}
                </div>
            );
        }

        function Layout({ children, user, currentPage, setPage }) {
            const [sidebarOpen, setSidebarOpen] = useState(false);

            const navigation = [
                { name: 'Головна', page: 'Dashboard', icon: Home },
                { name: 'Чат', page: 'Chat', icon: MessageSquare },
                { name: 'Завдання', page: 'Tasks', icon: CheckSquare },
                { name: 'Голосування', page: 'Voting', icon: Vote },
                { name: 'Оголошення', page: 'Announcements', icon: Megaphone },
                { name: 'Документи', page: 'Documents', icon: FolderOpen },
                { name: 'Календар', page: 'Calendar', icon: CalendarIcon },
            ];

            if (user?.role === 'admin') {
                navigation.push({ name: 'Адмін-панель', page: 'AdminPanel', icon: Settings });
            }

            return (
                <div className="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50 to-slate-100">
                    {/* Mobile Header */}
                    <div className="lg:hidden fixed top-0 left-0 right-0 z-50 bg-white border-b border-gray-200 shadow-sm">
                        <div className="flex items-center justify-between px-4 py-3">
                            <div className="flex items-center gap-3">
                                <button onClick={() => setSidebarOpen(!sidebarOpen)} className="p-2 rounded-lg hover:bg-gray-100 transition-colors">
                                    {sidebarOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
                                </button>
                                <h1 className="text-xl font-bold text-[var(--primary)]">Платформа ГГР</h1>
                            </div>
                            <div className="flex items-center gap-2">
                                <NotificationBell user={user} setPage={setPage} />
                            </div>
                        </div>
                    </div>

                    {/* Sidebar */}
                    <aside className={`fixed left-0 top-0 bottom-0 w-72 bg-[var(--primary)] text-white z-40 transition-transform duration-300 ${sidebarOpen ? 'translate-x-0' : '-translate-x-full lg:translate-x-0'}`}>
                        <div className="flex flex-col h-full">
                            <div className="p-6 border-b border-white/10">
                                <h1 className="text-2xl font-bold tracking-tight">Велика Гімназійна</h1>
                                <p className="text-sm text-blue-200 mt-1">Рада - Платформа</p>
                            </div>

                            <nav className="flex-1 overflow-y-auto py-6 px-4 space-y-2">
                                {navigation.map((item) => {
                                    const Icon = item.icon;
                                    const isActive = currentPage === item.page;
                                    return (
                                        <button
                                            key={item.page}
                                            onClick={() => { setPage(item.page); setSidebarOpen(false); }}
                                            className={`w-full flex items-center gap-3 px-4 py-3 rounded-lg transition-all duration-200 ${isActive ? 'bg-white/20 text-white shadow-lg' : 'text-blue-100 hover:bg-white/10 hover:text-white'}`}
                                        >
                                            <Icon className="w-5 h-5" />
                                            <span className="font-medium">{item.name}</span>
                                        </button>
                                    );
                                })}
                            </nav>

                            {user && (
                                <div className="p-4 border-t border-white/10">
                                    <div 
                                        className="flex items-center gap-3 px-4 py-3 rounded-lg hover:bg-white/10 transition-colors cursor-pointer"
                                        onClick={() => { setPage('Profile'); setSidebarOpen(false); }}
                                    >
                                        <div className="w-10 h-10 rounded-full bg-[var(--accent)] flex items-center justify-center text-white font-bold shrink-0 overflow-hidden">
                                            {user.avatar_url ? <img src={user.avatar_url} className="w-full h-full object-cover"/> : (user.full_name?.[0] || 'U')}
                                        </div>
                                        <div className="flex-1 text-left overflow-hidden">
                                            <p className="font-medium text-sm truncate">{user.full_name}</p>
                                            <p className="text-xs text-blue-200 truncate capitalize">{user.role}</p>
                                        </div>
                                    </div>
                                    <button onClick={() => signOut(auth)} className="mt-2 w-full flex items-center justify-center gap-2 text-xs text-red-300 hover:text-red-100 py-2">
                                        <LogOut className="w-3 h-3"/> Вийти
                                    </button>
                                </div>
                            )}
                        </div>
                    </aside>

                    {sidebarOpen && (
                        <div className="fixed inset-0 bg-black/50 z-30 lg:hidden" onClick={() => setSidebarOpen(false)} />
                    )}

                    <main className="lg:ml-72 pt-16 lg:pt-0 min-h-screen">
                        <div className="p-4 lg:p-8 max-w-[1600px] mx-auto">
                            {children}
                        </div>
                    </main>
                </div>
            );
        }

        function Auth({ setUser }) {
            const [isLogin, setIsLogin] = useState(true);
            const [email, setEmail] = useState('');
            const [password, setPassword] = useState('');
            const [name, setName] = useState('');
            const [error, setError] = useState('');
            const [loading, setLoading] = useState(false);

            const handleGoogleLogin = async () => {
                setError('');
                setLoading(true);
                try {
                    const result = await signInWithPopup(auth, googleProvider);
                    await checkAndCreateUser(result.user, result.user.displayName || 'Google User');
                } catch (err) {
                    console.error(err);
                    // Friendly error mapping
                    if (err.code === 'auth/operation-not-allowed') {
                        setError("Помилка налаштування: Вхід через Google вимкнено в Firebase Console. Будь ласка, увімкніть його.");
                    } else {
                        setError(err.message);
                    }
                } finally {
                    setLoading(false);
                }
            };

            const checkAndCreateUser = async (user, userName) => {
                const userRef = doc(getCollectionRef('users'), user.uid);
                const userSnap = await getDoc(userRef);
                
                if (!userSnap.exists()) {
                    const usersSnapshot = await getDocs(getCollectionRef('users'));
                    // First user becomes admin
                    const role = usersSnapshot.empty ? 'admin' : 'user';
                    
                    await setDoc(userRef, {
                        id: user.uid,
                        full_name: userName,
                        email: user.email,
                        role: role, 
                        is_active: true,
                        created_date: new Date().toISOString(),
                        avatar_url: user.photoURL,
                        last_seen: new Date().toISOString()
                    });
                    logAction({id: user.uid, full_name: userName}, 'register', 'User', `Новий користувач зареєструвався: ${userName}`);
                } else {
                    await updateDoc(userRef, { last_seen: new Date().toISOString() });
                }
            };

            const handleAuth = async (e) => {
                e.preventDefault();
                setError('');
                setLoading(true);
                try {
                    let userCredential;
                    if (isLogin) {
                        userCredential = await signInWithEmailAndPassword(auth, email, password);
                        await checkAndCreateUser(userCredential.user, userCredential.user.displayName || 'User');
                    } else {
                        userCredential = await createUserWithEmailAndPassword(auth, email, password);
                        await updateProfile(userCredential.user, { displayName: name });
                        await checkAndCreateUser(userCredential.user, name);
                    }
                } catch (err) {
                    console.error(err);
                    let msg = err.message;
                    if (err.code === 'auth/operation-not-allowed') {
                        msg = "ПОМИЛКА: Email/Password вхід не увімкнено в Firebase Console. Увімкніть його в Authentication > Sign-in method.";
                    } else if (err.code === 'auth/invalid-credential' || err.code === 'auth/invalid-login-credentials') {
                        msg = "Невірний email або пароль. Перевірте дані або зареєструйтесь.";
                    } else if (err.code === 'auth/user-not-found') {
                        msg = "Користувача не знайдено. Будь ласка, зареєструйтесь.";
                    } else if (err.code === 'auth/wrong-password') {
                        msg = "Невірний пароль.";
                    } else if (err.code === 'auth/email-already-in-use') {
                        msg = "Цей email вже використовується. Спробуйте увійти.";
                    } else if (err.code === 'auth/weak-password') {
                        msg = "Пароль занадто слабкий (мінімум 6 символів).";
                    }
                    setError(msg);
                } finally {
                    setLoading(false);
                }
            };

            return (
                <div className="min-h-screen flex items-center justify-center bg-gradient-to-br from-slate-900 to-slate-800 p-4">
                    <Card className="w-full max-w-md border-0 shadow-2xl animate-in fade-in zoom-in-95">
                        <CardHeader className="space-y-1">
                            <CardTitle className="text-2xl font-bold text-center">
                                {isLogin ? 'Вхід до системи' : 'Реєстрація'}
                            </CardTitle>
                            <p className="text-center text-gray-500">Гімназійна Рада</p>
                        </CardHeader>
                        <CardContent>
                            <form onSubmit={handleAuth} className="space-y-4">
                                {!isLogin && (
                                    <div className="space-y-2">
                                        <label className="text-sm font-medium">Прізвище та Ім'я</label>
                                        <Input placeholder="Іванов Іван" value={name} onChange={e => setName(e.target.value)} required />
                                    </div>
                                )}
                                <div className="space-y-2">
                                    <label className="text-sm font-medium">Email</label>
                                    <Input type="email" placeholder="user@example.com" value={email} onChange={e => setEmail(e.target.value)} required />
                                </div>
                                <div className="space-y-2">
                                    <label className="text-sm font-medium">Пароль</label>
                                    <Input type="password" value={password} onChange={e => setPassword(e.target.value)} required />
                                </div>
                                {error && (
                                    <div className="p-3 rounded bg-red-50 text-red-600 text-sm border border-red-200">
                                        <p className="font-bold flex items-center gap-2"><AlertCircle className="w-4 h-4"/> Помилка:</p>
                                        {error}
                                    </div>
                                )}
                                <Button type="submit" className="w-full" disabled={loading}>
                                    {loading ? 'Завантаження...' : (isLogin ? 'Увійти' : 'Зареєструватися')}
                                </Button>
                            </form>
                            
                            <div className="relative my-4">
                                <div className="absolute inset-0 flex items-center"><span className="w-full border-t" /></div>
                                <div className="relative flex justify-center text-xs uppercase"><span className="bg-white px-2 text-muted-foreground">Або</span></div>
                            </div>

                            <Button variant="outline" type="button" className="w-full" onClick={handleGoogleLogin} disabled={loading}>
                                <svg className="mr-2 h-4 w-4" viewBox="0 0 24 24"><path d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z" fill="#4285F4"/><path d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z" fill="#34A853"/><path d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z" fill="#FBBC05"/><path d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z" fill="#EA4335"/></svg>
                                Увійти через Google
                            </Button>

                            <div className="mt-4 text-center text-sm">
                                <span className="text-gray-500">
                                    {isLogin ? 'Немає акаунту? ' : 'Вже є акаунт? '}
                                </span>
                                <button 
                                    type="button" 
                                    onClick={() => setIsLogin(!isLogin)} 
                                    className="text-blue-600 hover:underline font-medium"
                                >
                                    {isLogin ? 'Зареєструватися' : 'Увійти'}
                                </button>
                            </div>
                        </CardContent>
                    </Card>
                </div>
            );
        }

        function Dashboard({ user, setPage }) {
            const [stats, setStats] = useState({ tasks: 0, polls: 0, anns: 0 });
            const [myTasks, setMyTasks] = useState([]);
            const [announcements, setAnnouncements] = useState([]);

            useEffect(() => {
                if (!user) return;
                const unsubTasks = onSnapshot(query(getCollectionRef('tasks'), orderBy('created_date', 'desc')), (snap) => {
                    const tasks = snap.docs.map(d => ({ id: d.id, ...d.data() }));
                    const my = tasks.filter(t => t.assigned_to?.includes(user.id) && t.status !== 'completed');
                    setMyTasks(my);
                    setStats(prev => ({ ...prev, tasks: my.length }));
                }, (err) => console.log(err));

                const unsubPolls = onSnapshot(query(getCollectionRef('polls'), orderBy('created_date', 'desc')), (snap) => {
                    const polls = snap.docs.map(d => ({ id: d.id, ...d.data() }));
                    const active = polls.filter(p => p.status === 'active');
                    setStats(prev => ({ ...prev, polls: active.length }));
                }, (err) => console.log(err));

                const unsubAnns = onSnapshot(query(getCollectionRef('announcements'), orderBy('created_date', 'desc')), (snap) => {
                    const anns = snap.docs.map(d => ({ id: d.id, ...d.data() }));
                    setAnnouncements(anns.slice(0, 3));
                    setStats(prev => ({ ...prev, anns: anns.filter(a => a.priority === 'High').length }));
                }, (err) => console.log(err));

                return () => { unsubTasks(); unsubPolls(); unsubAnns(); };
            }, [user]);

            const statCards = [
                { title: 'Мої активні завдання', value: stats.tasks, icon: CheckSquare, color: 'bg-blue-500', link: 'Tasks' },
                { title: 'Активні голосування', value: stats.polls, icon: Vote, color: 'bg-emerald-500', link: 'Voting' },
                { title: 'Нові оголошення', value: stats.anns, icon: Megaphone, color: 'bg-orange-500', link: 'Announcements' },
                { title: 'Непрочитані повідомлення', value: 0, icon: MessageSquare, color: 'bg-purple-500', link: 'Chat' },
            ];

            return (
                <div className="space-y-8 animate-in fade-in duration-500">
                    <div className="bg-gradient-to-r from-[var(--primary)] to-[var(--primary-light)] rounded-2xl p-8 text-white shadow-xl relative overflow-hidden">
                        <div className="relative z-10">
                            <h1 className="text-3xl md:text-4xl font-bold mb-2">Вітаємо, {user?.full_name?.split(' ')[0]}! 👋</h1>
                            <p className="text-blue-100 text-lg">{user?.position || 'Член Ради'} • Велика Гімназійна Рада</p>
                        </div>
                        <div className="absolute right-0 top-0 h-full w-1/3 bg-white/10 skew-x-12 transform translate-x-12" />
                    </div>

                    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                        {statCards.map((stat, index) => {
                            const Icon = stat.icon;
                            return (
                                <Card key={index} onClick={() => setPage(stat.link)} className="hover:shadow-lg transition-all duration-300 hover:-translate-y-1 cursor-pointer border-0 shadow-md bg-white/80 backdrop-blur">
                                    <CardContent className="p-6">
                                        <div className="flex items-start justify-between">
                                            <div>
                                                <p className="text-sm font-medium text-gray-600 mb-2">{stat.title}</p>
                                                <p className="text-4xl font-bold text-gray-900">{stat.value}</p>
                                            </div>
                                            <div className={`${stat.color} p-3 rounded-xl shadow-md`}>
                                                <Icon className="w-6 h-6 text-white" />
                                            </div>
                                        </div>
                                    </CardContent>
                                </Card>
                            );
                        })}
                    </div>

                    <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
                        <Card className="border-0 shadow-lg bg-white/80 backdrop-blur flex flex-col">
                            <CardHeader className="border-b border-gray-100">
                                <div className="flex items-center justify-between">
                                    <CardTitle className="text-xl font-bold flex items-center gap-2">
                                        <CheckSquare className="w-5 h-5 text-blue-600" /> Мої завдання
                                    </CardTitle>
                                    <Button variant="ghost" size="sm" onClick={() => setPage('Tasks')}>Всі <ArrowRight className="w-4 h-4 ml-1"/></Button>
                                </div>
                            </CardHeader>
                            <CardContent className="p-6 flex-1">
                                {myTasks.length === 0 ? (
                                    <div className="text-center py-12 text-gray-500 h-full flex flex-col justify-center items-center">
                                        <CheckSquare className="w-12 h-12 mb-3 opacity-20" />
                                        <p>Немає активних завдань</p>
                                    </div>
                                ) : (
                                    <div className="space-y-3">
                                        {myTasks.slice(0, 4).map((task) => (
                                            <div key={task.id} className="p-4 border border-gray-200 rounded-lg hover:shadow-md transition-all hover:bg-gray-50 cursor-pointer" onClick={() => setPage('Tasks')}>
                                                <div className="flex items-start justify-between mb-2">
                                                    <h4 className="font-semibold text-gray-900">{task.title}</h4>
                                                    <Badge className={task.priority === 'High' ? 'bg-red-100 text-red-800' : 'bg-blue-100 text-blue-800'}>{task.priority}</Badge>
                                                </div>
                                                {task.due_date && (
                                                    <div className="flex items-center gap-2 text-sm text-gray-600">
                                                        <Clock className="w-4 h-4" />
                                                        Виконати до: {task.due_date}
                                                    </div>
                                                )}
                                            </div>
                                        ))}
                                    </div>
                                )}
                            </CardContent>
                        </Card>

                        <Card className="border-0 shadow-lg bg-white/80 backdrop-blur flex flex-col">
                            <CardHeader className="border-b border-gray-100">
                                <div className="flex items-center justify-between">
                                    <CardTitle className="text-xl font-bold flex items-center gap-2">
                                        <Megaphone className="w-5 h-5 text-orange-600" /> Останні оголошення
                                    </CardTitle>
                                    <Button variant="ghost" size="sm" onClick={() => setPage('Announcements')}>Всі <ArrowRight className="w-4 h-4 ml-1"/></Button>
                                </div>
                            </CardHeader>
                            <CardContent className="p-6 flex-1">
                                {announcements.length === 0 ? (
                                    <div className="text-center py-12 text-gray-500 h-full flex flex-col justify-center items-center">
                                        <Megaphone className="w-12 h-12 mb-3 opacity-20" />
                                        <p>Поки немає оголошень</p>
                                    </div>
                                ) : (
                                    <div className="space-y-4">
                                        {announcements.map((ann) => (
                                            <div key={ann.id} className="p-4 border border-gray-200 rounded-lg hover:shadow-md transition-all bg-white">
                                                <div className="flex items-start gap-3">
                                                    {ann.priority === 'High' && <AlertCircle className="w-5 h-5 text-red-500 flex-shrink-0 mt-0.5" />}
                                                    <div className="flex-1">
                                                        <div className="flex items-center gap-2 mb-1">
                                                            <h4 className="font-semibold text-gray-900">{ann.title}</h4>
                                                            {ann.priority === 'High' && <Badge className="bg-red-100 text-red-800">Важливе</Badge>}
                                                        </div>
                                                        <p className="text-gray-600 text-sm line-clamp-2">{ann.content}</p>
                                                        <p className="text-xs text-gray-500 mt-2">
                                                            {ann.created_date ? format(new Date(ann.created_date), 'dd.MM.yyyy HH:mm') : ''}
                                                        </p>
                                                    </div>
                                                </div>
                                            </div>
                                        ))}
                                    </div>
                                )}
                            </CardContent>
                        </Card>
                    </div>
                </div>
            );
        }

        // --- [CHAT COMPONENT - Inserted Here] ---
        function Chat({ user }) {
            const [channels, setChannels] = useState([]);
            const [selectedChannel, setSelectedChannel] = useState(null);
            const [messages, setMessages] = useState([]);
            const [newMessage, setNewMessage] = useState('');
            const [showChannels, setShowChannels] = useState(true);
            const [isCreateOpen, setIsCreateOpen] = useState(false);
            const [newChannelName, setNewChannelName] = useState('');
            const [channelType, setChannelType] = useState('general'); 
            const [selectedMembers, setSelectedMembers] = useState([]);
            const [allUsers, setAllUsers] = useState([]);
            const [editingMessage, setEditingMessage] = useState(null);
            const [editText, setEditText] = useState('');

            useEffect(() => {
                if (!user) return;
                const unsub = onSnapshot(getCollectionRef('channels'), (snap) => {
                    if (snap.empty && user.role === 'admin') {
                        addDoc(getCollectionRef('channels'), { name: 'Загальний', type: 'general', created_by: 'system' });
                    }
                    const allChannels = snap.docs.map(d => ({ id: d.id, ...d.data() }));
                    const visibleChannels = allChannels.filter(ch => {
                        if (user.role === 'admin') return true;
                        if (ch.type === 'general') return true;
                        if (ch.type === 'admin' && user.role === 'admin') return true;
                        if (ch.type === 'private' && (ch.members?.includes(user.id) || ch.created_by === user.id)) return true;
                        return false;
                    });
                    setChannels(visibleChannels);
                }, (err) => console.log(err));
                
                const unsubUsers = onSnapshot(getCollectionRef('users'), (snap) => {
                    setAllUsers(snap.docs.map(d => ({ id: d.id, ...d.data() })));
                }, (err) => console.log(err));
                return () => { unsub(); unsubUsers(); };
            }, [user]);

            useEffect(() => {
                if(channels.length > 0 && !selectedChannel) setSelectedChannel(channels[0]);
            }, [channels]);

            useEffect(() => {
                if (!selectedChannel) return;
                const q = query(getCollectionRef('messages'), orderBy('created_date'));
                const unsub = onSnapshot(q, (snap) => {
                    const all = snap.docs.map(d => ({ id: d.id, ...d.data() }));
                    setMessages(all.filter(m => m.channel_id === selectedChannel.id));
                }, (err) => console.log(err));
                return () => unsub();
            }, [selectedChannel]);

            const createChannel = async () => {
                if (!newChannelName.trim()) return;
                const channelData = {
                    name: newChannelName,
                    type: channelType,
                    created_by: user.id,
                    members: channelType === 'private' ? [...selectedMembers, user.id] : []
                };
                await addDoc(getCollectionRef('channels'), channelData);
                logAction(user, 'create', 'Channel', `Channel created: ${newChannelName}`);
                setIsCreateOpen(false); setNewChannelName(''); setChannelType('general'); setSelectedMembers([]);
            };

            const deleteChannel = async (e, id) => {
                e.stopPropagation();
                if(confirm('Видалити цей чат?')) {
                    await deleteDoc(doc(getCollectionRef('channels'), id));
                    logAction(user, 'delete', 'Channel', `Channel deleted: ${id}`);
                }
            };

            const sendMessage = async () => {
                if (!newMessage.trim()) return;
                await addDoc(getCollectionRef('messages'), {
                    content: newMessage,
                    channel_id: selectedChannel.id,
                    sender_id: user.id,
                    sender_name: user.full_name,
                    created_date: new Date().toISOString()
                });
                setNewMessage('');
            };

            const handleEditMessage = async () => {
                if (!editingMessage || !editText.trim()) return;
                await updateDoc(doc(getCollectionRef('messages'), editingMessage.id), {
                    content: editText
                });
                setEditingMessage(null);
            };

            const deleteMessage = async (msgId) => {
                if (confirm('Видалити це повідомлення?')) {
                    await deleteDoc(doc(getCollectionRef('messages'), msgId));
                }
            };

            return (
                <div className="h-[calc(100vh-8rem)] flex gap-6 animate-in fade-in">
                <Card className={`w-full lg:w-80 flex flex-col border-0 shadow-lg bg-white/80 backdrop-blur ${showChannels ? 'flex' : 'hidden lg:flex'}`}>
                    <div className="p-4 border-b border-gray-200">
                        <div className="flex justify-between items-center mb-4">
                            <h2 className="text-xl font-bold text-gray-900">Канали</h2>
                            <Button size="sm" variant="ghost" onClick={() => setIsCreateOpen(true)}><Plus className="w-5 h-5"/></Button>
                        </div>
                        <div className="relative">
                            <Search className="absolute left-3 top-1/2 -translate-y-1/2 w-4 h-4 text-gray-400" />
                            <Input placeholder="Пошук..." className="pl-9" />
                        </div>
                    </div>
                    <div className="flex-1 overflow-y-auto p-2 space-y-1">
                        {channels.map(c => (
                            <button 
                                key={c.id} 
                                onClick={() => { setSelectedChannel(c); setShowChannels(false); }}
                                className={`w-full flex items-center gap-3 px-4 py-3 rounded-lg transition-all text-left group ${selectedChannel?.id === c.id ? 'bg-blue-50 text-blue-900 shadow-sm' : 'hover:bg-gray-100 text-gray-700'}`}
                            >
                                {c.type === 'private' ? <Lock className="w-4 h-4 flex-shrink-0 text-orange-500"/> : c.type === 'admin' ? <Shield className="w-4 h-4 text-red-500"/> : <Hash className="w-4 h-4 flex-shrink-0"/>}
                                <div className="flex-1 min-w-0"><p className="font-medium truncate">{c.name}</p></div>
                                {(user.role === 'admin' || c.created_by === user.id) && (
                                    <div onClick={(e) => deleteChannel(e, c.id)} className="opacity-0 group-hover:opacity-100 p-1 hover:bg-red-100 rounded text-red-500 transition-opacity">
                                        <Trash2 className="w-3 h-3"/>
                                    </div>
                                )}
                            </button>
                        ))}
                    </div>
                </Card>

                <Card className={`flex-1 flex flex-col border-0 shadow-lg bg-white/80 backdrop-blur ${showChannels ? 'hidden lg:flex' : 'flex'}`}>
                    {selectedChannel ? (
                        <>
                            <div className="p-4 border-b border-gray-200 bg-white flex items-center gap-3 rounded-t-xl">
                                <Button variant="ghost" size="icon" onClick={() => setShowChannels(true)} className="lg:hidden">
                                    <ArrowLeft className="w-5 h-5"/>
                                </Button>
                                <h3 className="font-bold text-lg text-gray-900">{selectedChannel.name}</h3>
                                {selectedChannel.type === 'private' && <span className="text-xs bg-orange-100 text-orange-800 px-2 py-0.5 rounded">Приватний</span>}
                            </div>
                            <div className="flex-1 overflow-y-auto p-6 space-y-4 bg-slate-50/50">
                                {messages.map(m => (
                                    <div key={m.id} className={`flex gap-3 group ${m.sender_id === user.id ? 'flex-row-reverse' : ''}`}>
                                        <div className="w-10 h-10 rounded-full bg-gradient-to-br from-blue-500 to-blue-600 flex items-center justify-center text-white font-semibold flex-shrink-0 shadow-md text-xs">
                                            {m.sender_name?.[0]}
                                        </div>
                                        <div className={`flex-1 max-w-[80%] ${m.sender_id === user.id ? 'items-end' : 'items-start'} flex flex-col relative`}>
                                            <div className="flex items-baseline gap-2 mb-1 px-1">
                                                <span className="font-semibold text-xs text-gray-900">{m.sender_name}</span>
                                                <span className="text-[10px] text-gray-500">{m.created_date ? format(new Date(m.created_date), 'HH:mm') : ''}</span>
                                            </div>
                                            <div className={`p-3 rounded-xl shadow-sm border relative group/msg ${m.sender_id === user.id ? 'bg-blue-600 text-white border-blue-600' : 'bg-white text-gray-700 border-gray-100'}`}>
                                                <p className="leading-relaxed whitespace-pre-wrap">{m.content}</p>
                                                
                                                {/* Message Actions */}
                                                {(m.sender_id === user.id || user.role === 'admin') && (
                                                    <div className={`absolute top-1 ${m.sender_id === user.id ? '-left-12' : '-right-12'} opacity-0 group-hover/msg:opacity-100 flex gap-1`}>
                                                        {m.sender_id === user.id && <button onClick={() => { setEditingMessage(m); setEditText(m.content); }} className="p-1 hover:bg-gray-200 rounded-full bg-white shadow text-blue-600"><Edit className="w-3 h-3"/></button>}
                                                        <button onClick={() => deleteMessage(m.id)} className="p-1 hover:bg-red-100 rounded-full bg-white shadow text-red-500"><Trash2 className="w-3 h-3"/></button>
                                                    </div>
                                                )}
                                            </div>
                                        </div>
                                    </div>
                                ))}
                            </div>
                            <div className="p-4 border-t border-gray-200 bg-white flex gap-3 rounded-b-xl">
                                <Input 
                                    placeholder={`Повідомлення #${selectedChannel.name}`} 
                                    value={newMessage}
                                    onChange={e => setNewMessage(e.target.value)}
                                    onKeyDown={e => e.key === 'Enter' && sendMessage()}
                                    className="flex-1"
                                />
                                <Button onClick={sendMessage} className="bg-[var(--primary)] shadow-md"><Send className="w-4 h-4"/></Button>
                            </div>
                        </>
                    ) : <div className="flex-1 flex items-center justify-center text-gray-500">Виберіть канал</div>}
                </Card>

                {/* Create Channel Dialog */}
                <Dialog open={isCreateOpen} onOpenChange={setIsCreateOpen}>
                    <DialogContent>
                        <DialogHeader><DialogTitle>Створити канал</DialogTitle></DialogHeader>
                        <div className="space-y-4 py-4">
                            <Input placeholder="Назва каналу" value={newChannelName} onChange={e => setNewChannelName(e.target.value)}/>
                            <div>
                                <label className="text-sm font-medium mb-1 block">Тип каналу</label>
                                <div className="flex gap-2">
                                    <Button size="sm" variant={channelType === 'general' ? 'default' : 'outline'} onClick={() => setChannelType('general')}>Публічний</Button>
                                    <Button size="sm" variant={channelType === 'private' ? 'default' : 'outline'} onClick={() => setChannelType('private')}>Приватний</Button>
                                    {user.role === 'admin' && <Button size="sm" variant={channelType === 'admin' ? 'default' : 'outline'} onClick={() => setChannelType('admin')}>Адмін</Button>}
                                </div>
                            </div>
                            {channelType === 'private' && (
                                <div>
                                    <label className="text-sm font-medium mb-1 block">Оберіть учасників</label>
                                    <div className="border rounded-lg p-2 max-h-48 overflow-y-auto bg-gray-50">
                                        {allUsers.filter(u => u.id !== user.id).map(u => (
                                            <label key={u.id} className="flex items-center gap-2 p-2 hover:bg-gray-200 rounded cursor-pointer">
                                                <input type="checkbox" checked={selectedMembers.includes(u.id)} onChange={e => {
                                                    if(e.target.checked) setSelectedMembers([...selectedMembers, u.id]);
                                                    else setSelectedMembers(selectedMembers.filter(id => id !== u.id));
                                                }} className="w-4 h-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"/>
                                                <span className="text-sm">{u.full_name}</span>
                                            </label>
                                        ))}
                                    </div>
                                </div>
                            )}
                            <Button onClick={createChannel} variant="success" className="w-full">Створити</Button>
                        </div>
                    </DialogContent>
                </Dialog>

                {/* Edit Message Dialog */}
                <Dialog open={!!editingMessage} onOpenChange={() => setEditingMessage(null)}>
                    <DialogContent>
                        <DialogHeader><DialogTitle>Редагувати повідомлення</DialogTitle></DialogHeader>
                        <Textarea value={editText} onChange={e => setEditText(e.target.value)}/>
                        <Button onClick={handleEditMessage} className="w-full mt-4">Зберегти</Button>
                    </DialogContent>
                </Dialog>
                </div>
            );
        }

        function Tasks({ user }) {
            const [tasks, setTasks] = useState([]);
            const [newTask, setNewTask] = useState({ title: '', description: '', priority: 'Medium', category: '', due_date: '' });
            const [isCreateOpen, setIsCreateOpen] = useState(false);
            const [users, setUsers] = useState([]);
            const [filter, setFilter] = useState('all');
            const [assignedTo, setAssignedTo] = useState([]);

            useEffect(() => {
                if (!user) return;
                const unsub = onSnapshot(query(getCollectionRef('tasks'), orderBy('created_date', 'desc')), (snap) => {
                    setTasks(snap.docs.map(d => ({ id: d.id, ...d.data() })));
                }, (err) => console.log(err));
                const unsubUsers = onSnapshot(getCollectionRef('users'), (snap) => {
                    setUsers(snap.docs.map(d => ({ id: d.id, ...d.data() })));
                }, (err) => console.log(err));
                return () => { unsub(); unsubUsers(); };
            }, [user]);

            const createTask = async () => {
                if (!newTask.title) return;
                await addDoc(getCollectionRef('tasks'), {
                    ...newTask,
                    assigned_to: assignedTo,
                    status: 'to_do',
                    created_date: new Date().toISOString(),
                    assigned_to_names: assignedTo.map(uid => users.find(u => u.id === uid)?.full_name || '')
                });
                logAction(user, 'create', 'Task', `Task created: ${newTask.title}`);
                setIsCreateOpen(false);
                setNewTask({ title: '', description: '', priority: 'Medium', category: '', due_date: '' });
                setAssignedTo([]);
            };

            const deleteTask = async (id) => {
                if(confirm('Видалити завдання?')) {
                    await deleteDoc(doc(getCollectionRef('tasks'), id));
                    logAction(user, 'delete', 'Task', `Task deleted: ${id}`);
                }
            };
            const updateStatus = async (id, status) => {
                await updateDoc(doc(getCollectionRef('tasks'), id), { status });
                logAction(user, 'update', 'Task', `Task status updated to: ${status}`);
            };

            const filteredTasks = tasks.filter(t => {
                if (filter === 'my_tasks') return t.assigned_to?.includes(user.id);
                if (filter === 'to_do') return t.status === 'to_do';
                if (filter === 'in_progress') return t.status === 'in_progress';
                if (filter === 'completed') return t.status === 'completed';
                return true;
            });

            const priorityColors = { Low: 'bg-gray-100 text-gray-800', Medium: 'bg-blue-100 text-blue-800', High: 'bg-orange-100 text-orange-800', Urgent: 'bg-red-100 text-red-800' };

            return (
                <div className="space-y-6 animate-in fade-in">
                    <div className="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4">
                        <div>
                            <h1 className="text-3xl font-bold text-gray-900">Управління завданнями</h1>
                            <p className="text-gray-600 mt-1">Призначайте та відстежуйте завдання</p>
                        </div>
                        {user.role === 'admin' && <Button onClick={() => setIsCreateOpen(true)} className="bg-emerald-500 hover:bg-emerald-600"><Plus className="w-4 h-4 mr-2"/> Створити</Button>}
                    </div>

                    <Dialog open={isCreateOpen} onOpenChange={setIsCreateOpen}>
                        <DialogContent className="max-w-2xl">
                            <DialogHeader><DialogTitle className="text-xl">Create New Task</DialogTitle></DialogHeader>
                            <div className="space-y-4 py-2">
                                <div>
                                    <label className="text-sm font-semibold mb-1 block">Title</label>
                                    <Input placeholder="Task title" value={newTask.title} onChange={e => setNewTask({...newTask, title: e.target.value})}/>
                                </div>
                                <div>
                                    <label className="text-sm font-semibold mb-1 block">Description</label>
                                    <Textarea placeholder="Task description" value={newTask.description} onChange={e => setNewTask({...newTask, description: e.target.value})} className="min-h-[120px]"/>
                                </div>
                                <div className="grid grid-cols-2 gap-4">
                                    <div>
                                        <label className="text-sm font-semibold mb-1 block">Priority</label>
                                        <select className="w-full border rounded-lg h-10 px-3 text-sm" value={newTask.priority} onChange={e => setNewTask({...newTask, priority: e.target.value})}>
                                            <option value="Low">Low</option>
                                            <option value="Medium">Medium</option>
                                            <option value="High">High</option>
                                            <option value="Urgent">Urgent</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label className="text-sm font-semibold mb-1 block">Due Date</label>
                                        <Input type="date" value={newTask.due_date} onChange={e => setNewTask({...newTask, due_date: e.target.value})}/>
                                    </div>
                                </div>
                                <div>
                                    <label className="text-sm font-semibold mb-1 block">Category</label>
                                    <Input placeholder="e.g., Finance, Event Planning" value={newTask.category} onChange={e => setNewTask({...newTask, category: e.target.value})}/>
                                </div>
                                <div className="mt-2">
                                    <label className="text-sm font-semibold mb-1 block text-gray-500">Assign To (Optional)</label>
                                    <div className="flex flex-wrap gap-2">
                                        {users.map(u => (
                                            <button 
                                                key={u.id} 
                                                onClick={() => {
                                                    if(assignedTo.includes(u.id)) setAssignedTo(assignedTo.filter(id => id !== u.id));
                                                    else setAssignedTo([...assignedTo, u.id]);
                                                }}
                                                className={`text-xs border px-2 py-1 rounded-full ${assignedTo.includes(u.id) ? 'bg-blue-100 border-blue-300' : 'bg-gray-50'}`}
                                            >
                                                {u.full_name}
                                            </button>
                                        ))}
                                    </div>
                                </div>
                                <Button onClick={createTask} variant="success" className="w-full mt-4">Create Task</Button>
                            </div>
                        </DialogContent>
                    </Dialog>

                    <Card className="border-0 shadow-md bg-white/80 backdrop-blur">
                        <CardContent className="p-4 flex flex-wrap gap-2">
                            <Filter className="w-4 h-4 text-gray-500 self-center mr-2"/>
                            {['all', 'my_tasks', 'to_do', 'in_progress', 'completed'].map(f => (
                                <Button key={f} variant={filter === f ? 'default' : 'outline'} size="sm" onClick={() => setFilter(f)}>{f.replace('_', ' ')}</Button>
                            ))}
                        </CardContent>
                    </Card>

                    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                        {filteredTasks.map(task => (
                            <Card key={task.id} className="border-0 shadow-md hover:shadow-lg transition-all bg-white/80 backdrop-blur">
                                <CardHeader>
                                    <div className="flex justify-between items-start">
                                        <CardTitle className="text-lg font-bold">{task.title}</CardTitle>
                                        <div className="flex gap-1 items-center">
                                            <Badge className={priorityColors[task.priority]}>{task.priority}</Badge>
                                            {user.role === 'admin' && <button onClick={() => deleteTask(task.id)} className="text-red-500 hover:bg-red-50 p-1 rounded transition-colors"><Trash2 className="w-4 h-4"/></button>}
                                        </div>
                                    </div>
                                </CardHeader>
                                <CardContent className="space-y-4">
                                    <p className="text-gray-600 text-sm line-clamp-2">{task.description}</p>
                                    {task.due_date && <p className="text-xs text-gray-500 flex items-center gap-1"><CalendarIcon className="w-3 h-3"/> Due: {task.due_date}</p>}
                                    <div>
                                        <label className="text-xs text-gray-500">Статус</label>
                                        <select value={task.status} onChange={e => updateStatus(task.id, e.target.value)} className="w-full border rounded p-1 text-sm mt-1 bg-gray-50">
                                            <option value="to_do">До виконання</option>
                                            <option value="in_progress">В процесі</option>
                                            <option value="completed">Виконано</option>
                                        </select>
                                    </div>
                                    {task.assigned_to_names?.length > 0 && (
                                        <div className="flex items-center gap-2 text-sm text-gray-600 pt-2 border-t">
                                            <UserIcon className="w-4 h-4"/> <span>{task.assigned_to_names.join(', ')}</span>
                                        </div>
                                    )}
                                </CardContent>
                            </Card>
                        ))}
                    </div>
                </div>
            );
        }

        function Voting({ user }) {
            const [polls, setPolls] = useState([]);
            const [newPoll, setNewPoll] = useState({ title: '', description: '', options: ['', ''], category: 'Other', closing_date: '', min_quorum: 0, anonymous: false });
            const [isCreateOpen, setIsCreateOpen] = useState(false);

            useEffect(() => {
                if (!user) return;
                return onSnapshot(query(getCollectionRef('polls'), orderBy('created_date', 'desc')), snap => {
                    setPolls(snap.docs.map(d => ({ id: d.id, ...d.data() })));
                }, (err) => console.log(err));
            }, [user]);

            const createPoll = async () => {
                const validOpts = newPoll.options.filter(o => o);
                if (!newPoll.title || validOpts.length < 2) return;
                
                const results = {};
                validOpts.forEach((o, i) => results[i] = 0);
                
                await addDoc(getCollectionRef('polls'), {
                    ...newPoll,
                    options: validOpts,
                    results,
                    voters: [],
                    status: 'active',
                    created_date: new Date().toISOString(),
                    total_votes: 0
                });
                logAction(user, 'create', 'Poll', `Poll created: ${newPoll.title}`);
                setIsCreateOpen(false);
                setNewPoll({ title: '', description: '', options: ['', ''], category: 'Other', closing_date: '', min_quorum: 0, anonymous: false });
            };

            const vote = async (poll, optIndex) => {
                if (poll.voters?.includes(user.id)) return;
                const newResults = { ...poll.results };
                newResults[optIndex] = (newResults[optIndex] || 0) + 1;
                await updateDoc(doc(getCollectionRef('polls'), poll.id), {
                    results: newResults,
                    total_votes: (poll.total_votes || 0) + 1,
                    voters: [...(poll.voters || []), user.id]
                });
            };
            
            const deletePoll = async (id) => {
                if(confirm('Видалити опитування?')) {
                    await deleteDoc(doc(getCollectionRef('polls'), id));
                    logAction(user, 'delete', 'Poll', `Poll deleted: ${id}`);
                }
            };

            return (
                <div className="space-y-6 animate-in fade-in">
                    <div className="flex justify-between items-center">
                        <div><h1 className="text-3xl font-bold">Голосування</h1><p className="text-gray-600">Приймайте рішення разом</p></div>
                        {user.role === 'admin' && <Button onClick={() => setIsCreateOpen(true)} className="bg-[var(--accent)] hover:bg-[var(--accent-light)]"><Plus className="w-4 h-4 mr-2"/> Нове</Button>}
                    </div>

                    <Dialog open={isCreateOpen} onOpenChange={setIsCreateOpen}>
                        <DialogContent className="max-w-2xl">
                            <DialogHeader><DialogTitle className="text-xl">Create New Poll</DialogTitle></DialogHeader>
                            <div className="space-y-4 py-2">
                                <div><label className="text-sm font-semibold mb-1 block">Title</label><Input placeholder="Poll title" value={newPoll.title} onChange={e => setNewPoll({...newPoll, title: e.target.value})}/></div>
                                <div><label className="text-sm font-semibold mb-1 block">Description</label><Textarea placeholder="Poll description" value={newPoll.description} onChange={e => setNewPoll({...newPoll, description: e.target.value})}/></div>
                                
                                <div>
                                    <label className="text-sm font-semibold mb-1 block">Options</label>
                                    {newPoll.options.map((opt, i) => (
                                        <div key={i} className="mb-2"><Input placeholder={`Option ${i+1}`} value={opt} onChange={e => {
                                            const opts = [...newPoll.options]; opts[i] = e.target.value; setNewPoll({...newPoll, options: opts});
                                        }}/></div>
                                    ))}
                                    <Button variant="outline" size="sm" onClick={() => setNewPoll(p => ({...p, options: [...p.options, '']}))}><Plus className="w-3 h-3 mr-1"/> Add Option</Button>
                                </div>

                                <div className="grid grid-cols-2 gap-4">
                                    <div>
                                        <label className="text-sm font-semibold mb-1 block">Category</label>
                                        <select className="w-full border rounded-lg h-10 px-3" value={newPoll.category} onChange={e => setNewPoll({...newPoll, category: e.target.value})}>
                                            <option>Other</option><option>Budget</option><option>Event</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label className="text-sm font-semibold mb-1 block">Closing Date</label>
                                        <Input type="date" value={newPoll.closing_date} onChange={e => setNewPoll({...newPoll, closing_date: e.target.value})}/>
                                    </div>
                                </div>
                                
                                <div className="flex items-end gap-4">
                                    <div className="flex-1">
                                        <label className="text-sm font-semibold mb-1 block">Minimum Quorum</label>
                                        <Input type="number" value={newPoll.min_quorum} onChange={e => setNewPoll({...newPoll, min_quorum: e.target.value})}/>
                                    </div>
                                    <div className="flex items-center h-10">
                                        <input type="checkbox" checked={newPoll.anonymous} onChange={e => setNewPoll({...newPoll, anonymous: e.target.checked})} className="w-4 h-4 mr-2"/>
                                        <label className="text-sm">Anonymous voting</label>
                                    </div>
                                </div>

                                <Button onClick={createPoll} variant="success" className="w-full mt-4">Create Poll</Button>
                            </div>
                        </DialogContent>
                    </Dialog>

                    <div className="space-y-6">
                        {polls.map(poll => {
                            const hasVoted = poll.voters?.includes(user.id);
                            return (
                                <Card key={poll.id} className="border-0 shadow-lg bg-white/80 backdrop-blur">
                                    <CardHeader>
                                        <div className="flex justify-between">
                                            <CardTitle className="text-xl">{poll.title}</CardTitle>
                                            {user.role === 'admin' && <button onClick={() => deletePoll(poll.id)} className="text-red-500"><Trash2 className="w-4 h-4"/></button>}
                                        </div>
                                        <p className="text-sm text-gray-500">{poll.description}</p>
                                        <div className="text-sm text-gray-500 flex gap-4 mt-2">
                                            <span className="flex items-center gap-1"><TrendingUp className="w-4 h-4"/> {poll.total_votes || 0} голосів</span>
                                            {hasVoted && <span className="text-green-600 flex items-center gap-1 font-medium"><CheckCircle2 className="w-4 h-4"/> Ви проголосували</span>}
                                        </div>
                                    </CardHeader>
                                    <CardContent className="space-y-4">
                                        {poll.options.map((opt, i) => {
                                            const votes = poll.results?.[i] || 0;
                                            const pct = poll.total_votes ? Math.round((votes/poll.total_votes)*100) : 0;
                                            return (
                                                <div key={i}>
                                                    <div className="flex justify-between mb-1 text-sm font-medium">
                                                        <span>{opt}</span>
                                                        {hasVoted && <span className="text-gray-500">{votes} ({pct}%)</span>}
                                                    </div>
                                                    {hasVoted ? (
                                                        <div className="h-3 bg-gray-100 rounded-full overflow-hidden">
                                                            <div className="h-full bg-emerald-500 transition-all duration-500" style={{width: `${pct}%`}}/>
                                                        </div>
                                                    ) : (
                                                        <Button variant="outline" className="w-full justify-start hover:border-blue-500 hover:text-blue-600 transition-all" onClick={() => vote(poll, i)}>Голосувати</Button>
                                                    )}
                                                </div>
                                            );
                                        })}
                                    </CardContent>
                                </Card>
                            );
                        })}
                    </div>
                </div>
            );
        }

        function Announcements({ user }) {
            const [anns, setAnns] = useState([]);
            const [isCreate, setIsCreate] = useState(false);
            const [newAnn, setNewAnn] = useState({ title: '', content: '', priority: 'Normal', category: 'General', requires_ack: false });
            const [ackData, setAckData] = useState([]);

            useEffect(() => {
                if (!user) return;
                const u1 = onSnapshot(query(getCollectionRef('announcements'), orderBy('created_date', 'desc')), snap => {
                        setAnns(snap.docs.map(d => ({ id: d.id, ...d.data() })));
                    }, (err) => console.log(err));
                const u2 = onSnapshot(getCollectionRef('acknowledgements'), snap => {
                        setAckData(snap.docs.map(d => d.data()));
                    }, (err) => console.log(err));
                return () => { u1(); u2(); };
            }, [user]);

            const create = async () => {
                if(!newAnn.title) return;
                await addDoc(getCollectionRef('announcements'), {
                    ...newAnn,
                    author_name: user.full_name,
                    created_date: new Date().toISOString()
                });
                logAction(user, 'create', 'Announcement', `Announcement created: ${newAnn.title}`);
                setIsCreate(false);
                setNewAnn({ title: '', content: '', priority: 'Normal', category: 'General', requires_ack: false });
            };

            const acknowledge = async (annId) => {
                await addDoc(getCollectionRef('acknowledgements'), { annId, userId: user.id });
            };
            
            const deleteAnn = async (id) => {
                if(confirm('Видалити оголошення?')) {
                    await deleteDoc(doc(getCollectionRef('announcements'), id));
                    logAction(user, 'delete', 'Announcement', `Announcement deleted: ${id}`);
                }
            }

            const isAck = (annId) => ackData.some(a => a.annId === annId && a.userId === user.id);

            return (
                <div className="space-y-6 animate-in fade-in">
                        <div className="flex justify-between items-center">
                        <div><h1 className="text-3xl font-bold">Оголошення</h1></div>
                        {user.role === 'admin' && <Button onClick={() => setIsCreate(true)} className="bg-[var(--primary)]"><Plus className="w-4 h-4 mr-2"/> Створити</Button>}
                    </div>

                    <Dialog open={isCreate} onOpenChange={setIsCreate}>
                        <DialogContent className="max-w-2xl">
                            <DialogHeader><DialogTitle className="text-xl">Create New Announcement</DialogTitle></DialogHeader>
                            <div className="space-y-4 py-2">
                                <div><label className="text-sm font-semibold mb-1 block">Title</label><Input placeholder="Announcement title" value={newAnn.title} onChange={e => setNewAnn({...newAnn, title: e.target.value})}/></div>
                                <div><label className="text-sm font-semibold mb-1 block">Content</label><Textarea placeholder="Announcement content" value={newAnn.content} onChange={e => setNewAnn({...newAnn, content: e.target.value})} className="min-h-[150px]"/></div>
                                
                                <div className="grid grid-cols-2 gap-4">
                                    <div>
                                        <label className="text-sm font-semibold mb-1 block">Category</label>
                                        <select className="w-full border rounded-lg h-10 px-3" value={newAnn.category} onChange={e => setNewAnn({...newAnn, category: e.target.value})}>
                                            <option>General</option><option>Urgent</option><option>Event</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label className="text-sm font-semibold mb-1 block">Priority</label>
                                        <select className="w-full border rounded-lg h-10 px-3" value={newAnn.priority} onChange={e => setNewAnn({...newAnn, priority: e.target.value})}>
                                            <option>Normal</option><option>High</option>
                                        </select>
                                    </div>
                                </div>
                                
                                <div className="flex items-center mt-2">
                                    <input type="checkbox" checked={newAnn.requires_ack} onChange={e => setNewAnn({...newAnn, requires_ack: e.target.checked})} className="w-4 h-4 mr-2"/>
                                    <label className="text-sm">Requires Acknowledgement</label>
                                </div>

                                <Button onClick={create} variant="success" className="w-full mt-4">Create Announcement</Button>
                            </div>
                        </DialogContent>
                    </Dialog>

                    <div className="space-y-6">
                        {anns.map(ann => (
                            <Card key={ann.id} className={`border-0 shadow-lg bg-white/80 backdrop-blur ${ann.priority === 'High' ? 'border-l-4 border-l-red-500' : ''}`}>
                                <CardHeader>
                                    <div className="flex justify-between items-start">
                                        <div>
                                            <div className="flex items-center gap-2 mb-2">
                                                <CardTitle className="text-xl">{ann.title}</CardTitle>
                                                {ann.priority === 'High' && <Badge className="bg-red-100 text-red-800"><AlertCircle className="w-3 h-3 mr-1"/> Високий пріоритет</Badge>}
                                                {isAck(ann.id) && <Badge className="bg-green-100 text-green-800"><CheckCircle2 className="w-3 h-3 mr-1"/> Підтверджено</Badge>}
                                            </div>
                                            <p className="text-sm text-gray-500">Автор: {ann.author_name} • {ann.created_date ? format(new Date(ann.created_date), 'dd.MM.yyyy') : ''}</p>
                                        </div>
                                        {user.role === 'admin' && <button onClick={() => deleteAnn(ann.id)}><Trash2 className="w-4 h-4 text-red-500"/></button>}
                                    </div>
                                </CardHeader>
                                <CardContent>
                                    <p className="text-gray-700 whitespace-pre-wrap leading-relaxed">{ann.content}</p>
                                    {ann.requires_ack && !isAck(ann.id) && (
                                        <div className="mt-4 pt-4 border-t">
                                            <Button variant="outline" className="border-green-200 text-green-700 hover:bg-green-50 w-full sm:w-auto" onClick={() => acknowledge(ann.id)}>
                                                <CheckCircle2 className="w-4 h-4 mr-2"/> Підтвердити ознайомлення
                                            </Button>
                                        </div>
                                    )}
                                </CardContent>
                            </Card>
                        ))}
                    </div>
                </div>
            );
        }

        function Documents({ user }) {
            const [docs, setDocs] = useState([]);
            const [folders, setFolders] = useState([]);
            const [currentFolder, setCurrentFolder] = useState(null);
            const [isCreateFolder, setIsCreateFolder] = useState(false);
            const [folderName, setFolderName] = useState('');
            const [isConvertOpen, setIsConvertOpen] = useState(false);

            useEffect(() => {
                if (!user) return;
                const u1 = onSnapshot(getCollectionRef('documents'), snap => setDocs(snap.docs.map(d => ({id: d.id, ...d.data()}))), (err) => console.log(err));
                const u2 = onSnapshot(getCollectionRef('folders'), snap => setFolders(snap.docs.map(d => ({id: d.id, ...d.data()}))), (err) => console.log(err));
                return () => { u1(); u2(); };
            }, [user]);

            const createFolder = async () => {
                if(!folderName) return;
                await addDoc(getCollectionRef('folders'), { 
                    name: folderName, 
                    parent_id: currentFolder?.id || null,
                    created_by: user.id 
                });
                setIsCreateFolder(false); setFolderName('');
            };

            const deleteFolder = async (folderId) => {
                if (!confirm("Видалити папку?")) return;
                await deleteDoc(doc(getCollectionRef('folders'), folderId));
            };

            const deleteFile = async (docId) => {
                if (!confirm("Видалити файл?")) return;
                await deleteDoc(doc(getCollectionRef('documents'), docId));
            };

            const uploadFile = async (e) => {
                const file = e.target.files[0];
                if(!file) return;
                await addDoc(getCollectionRef('documents'), {
                    name: file.name,
                    size: file.size,
                    type: file.type,
                    folder_id: currentFolder?.id || null,
                    url: URL.createObjectURL(file), 
                    uploaded_by: user.full_name,
                    uploader_id: user.id,
                    created_date: new Date().toISOString()
                });
            };

            const downloadFile = (fileUrl, fileName) => {
                const link = document.createElement('a');
                link.href = fileUrl;
                link.download = fileName;
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            };

            const filteredFolders = folders.filter(f => f.parent_id === (currentFolder?.id || null));
            const filteredDocs = docs.filter(d => d.folder_id === (currentFolder?.id || null));

            return (
                <div className="space-y-6 animate-in fade-in">
                    <div className="flex flex-col sm:flex-row justify-between gap-4">
                        <div><h1 className="text-3xl font-bold">Бібліотека документів</h1></div>
                        <div className="flex gap-2">
                                <Button variant="outline" onClick={() => setIsConvertOpen(true)} className="text-green-600 border-green-200 hover:bg-green-50"><FileSpreadsheet className="w-4 h-4 mr-2"/> Конвертувати (Sheets/Word)</Button>
                                <Button variant="outline" onClick={() => setIsCreateFolder(true)}><FolderPlus className="w-4 h-4 mr-2"/> Папка</Button>
                                <div className="relative">
                                    <input type="file" onChange={uploadFile} className="absolute inset-0 opacity-0 cursor-pointer"/>
                                    <Button className="bg-[var(--accent)] hover:bg-[var(--accent-light)]"><Upload className="w-4 h-4 mr-2"/> Завантажити</Button>
                                </div>
                        </div>
                    </div>

                    <Dialog open={isCreateFolder} onOpenChange={setIsCreateFolder}>
                        <DialogContent>
                            <DialogHeader><DialogTitle>Нова папка</DialogTitle></DialogHeader>
                            <Input value={folderName} onChange={e => setFolderName(e.target.value)} placeholder="Назва папки"/>
                            <Button onClick={createFolder} className="w-full mt-4">Створити</Button>
                        </DialogContent>
                    </Dialog>

                    <Dialog open={isConvertOpen} onOpenChange={setIsConvertOpen}>
                        <DialogContent>
                            <DialogHeader><DialogTitle>Конвертація Документів</DialogTitle></DialogHeader>
                            <div className="flex flex-col items-center py-6 text-center space-y-4">
                                <RefreshCw className="w-12 h-12 text-blue-500 animate-spin"/>
                                <p className="text-gray-600">Оберіть файл для конвертації між форматами Google Sheets та Word.</p>
                                <Button onClick={() => setIsConvertOpen(false)} variant="outline">Закрити</Button>
                            </div>
                        </DialogContent>
                    </Dialog>

                    <Card className="bg-white/80 backdrop-blur">
                        <CardContent className="p-4 flex items-center gap-2 text-sm">
                                <button onClick={() => setCurrentFolder(null)} className="flex items-center hover:text-blue-600"><Home className="w-4 h-4 mr-1"/> Home</button>
                                {currentFolder && (
                                    <>
                                        <ChevronRight className="w-4 h-4 text-gray-400"/>
                                        <span className="font-medium">{currentFolder.name}</span>
                                    </>
                                )}
                        </CardContent>
                    </Card>

                    <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                        {filteredFolders.map(f => (
                            <Card key={f.id} className="hover:shadow-lg transition-all cursor-pointer bg-blue-50/50 border-blue-100 group relative" onClick={() => setCurrentFolder(f)}>
                                <CardContent className="p-6 flex items-center gap-3">
                                    <Folder className="w-10 h-10 text-blue-500"/>
                                    <div><p className="font-semibold">{f.name}</p><p className="text-xs text-gray-500">Папка</p></div>
                                    {(user.role === 'admin' || f.created_by === user.id) && (
                                        <button onClick={(e) => {e.stopPropagation(); deleteFolder(f.id)}} className="absolute top-2 right-2 opacity-0 group-hover:opacity-100 p-1 hover:bg-red-100 rounded text-red-500"><Trash2 className="w-4 h-4"/></button>
                                    )}
                                </CardContent>
                            </Card>
                        ))}
                        {filteredDocs.map(d => (
                            <Card key={d.id} className="hover:shadow-lg transition-all group relative">
                                <CardContent className="p-6">
                                    <div className="flex items-start gap-3">
                                        <FileText className="w-8 h-8 text-gray-500"/>
                                        <div className="flex-1 min-w-0">
                                            <p className="font-semibold truncate">{d.name}</p>
                                            <p className="text-xs text-gray-500">{(d.size/1024).toFixed(1)} KB</p>
                                        </div>
                                        <button onClick={() => downloadFile(d.url, d.name)} className="text-blue-600 hover:bg-blue-50 p-1 rounded"><Download className="w-4 h-4"/></button>
                                    </div>
                                    {(user.role === 'admin' || d.uploader_id === user.id) && (
                                        <button onClick={() => deleteFile(d.id)} className="absolute top-2 right-2 opacity-0 group-hover:opacity-100 p-1 hover:bg-red-100 rounded text-red-500"><Trash2 className="w-4 h-4"/></button>
                                    )}
                                </CardContent>
                            </Card>
                        ))}
                        {filteredFolders.length === 0 && filteredDocs.length === 0 && <div className="col-span-full text-center py-12 text-gray-500">Папка порожня</div>}
                    </div>
                </div>
            );
        }

        function Calendar({ user }) {
            const [currentDate, setCurrentDate] = useState(new Date());
            const [events, setEvents] = useState([]);
            const [isCreate, setIsCreate] = useState(false);
            const [newEv, setNewEv] = useState({ title: '', date: format(new Date(), 'yyyy-MM-dd'), time: '', description: '' });

            useEffect(() => {
                if (!user) return;
                return onSnapshot(getCollectionRef('events'), snap => setEvents(snap.docs.map(d => ({id: d.id, ...d.data()}))), (err) => console.log(err));
            }, [user]);

            const create = async () => {
                if(!newEv.title) return;
                await addDoc(getCollectionRef('events'), { ...newEv, created_by: user.full_name });
                setIsCreate(false);
                setNewEv({ title: '', date: format(new Date(), 'yyyy-MM-dd'), time: '', description: '' });
            };

            const monthStart = startOfMonth(currentDate);
            const days = eachDayOfInterval({ start: monthStart, end: endOfMonth(currentDate) });

            return (
                <div className="space-y-6 animate-in fade-in">
                    <div className="flex justify-between items-center">
                        <h1 className="text-3xl font-bold">Календар подій</h1>
                        {user.role === 'admin' && <Button onClick={() => setIsCreate(true)} className="bg-[var(--accent)]"><Plus className="w-4 h-4 mr-2"/> Додати подію</Button>}
                    </div>

                    <Dialog open={isCreate} onOpenChange={setIsCreate}>
                        <DialogContent>
                            <DialogHeader><DialogTitle>Нова подія</DialogTitle></DialogHeader>
                            <div className="space-y-4 py-4">
                                <Input placeholder="Назва" value={newEv.title} onChange={e => setNewEv({...newEv, title: e.target.value})}/>
                                <Textarea placeholder="Опис" value={newEv.description} onChange={e => setNewEv({...newEv, description: e.target.value})}/>
                                <div className="grid grid-cols-2 gap-4">
                                    <Input type="date" value={newEv.date} onChange={e => setNewEv({...newEv, date: e.target.value})}/>
                                    <Input type="time" value={newEv.time} onChange={e => setNewEv({...newEv, time: e.target.value})}/>
                                </div>
                                <Button onClick={create} className="w-full">Зберегти</Button>
                            </div>
                        </DialogContent>
                    </Dialog>

                    <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        <div className="lg:col-span-2">
                            <Card className="border-0 shadow-lg bg-white/80 backdrop-blur">
                                <CardHeader className="border-b">
                                    <div className="flex justify-between items-center">
                                        <CardTitle className="capitalize">{format(currentDate, 'LLLL yyyy', { locale: uk })}</CardTitle>
                                        <div className="flex gap-2">
                                            <Button variant="outline" size="icon" onClick={() => setCurrentDate(subMonths(currentDate, 1))}><ChevronLeft className="w-4 h-4"/></Button>
                                            <Button variant="outline" size="icon" onClick={() => setCurrentDate(addMonths(currentDate, 1))}><ChevronRight className="w-4 h-4"/></Button>
                                        </div>
                                    </div>
                                </CardHeader>
                                <CardContent className="p-4">
                                    <div className="grid grid-cols-7 gap-2 mb-2 text-center text-sm font-semibold text-gray-600">
                                        {['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Нд'].map(d => <div key={d}>{d}</div>)}
                                    </div>
                                    <div className="grid grid-cols-7 gap-2">
                                        {Array.from({ length: (monthStart.getDay() + 6) % 7 }).map((_, i) => <div key={i}/>)}
                                        {days.map(day => {
                                            const dayEvs = events.filter(e => {
                                                try {
                                                    return isSameDay(parseISO(e.date), day);
                                                } catch { return false; }
                                            });
                                            return (
                                                <div key={day} className={`aspect-square border rounded-lg p-1 relative ${isSameDay(day, new Date()) ? 'bg-blue-50 border-blue-300' : ''}`}>
                                                    <span className="text-sm font-medium">{format(day, 'd')}</span>
                                                    <div className="flex gap-1 flex-wrap mt-1">
                                                        {dayEvs.map((_, i) => <div key={i} className="w-1.5 h-1.5 rounded-full bg-blue-500"/>)}
                                                    </div>
                                                </div>
                                            );
                                        })}
                                    </div>
                                </CardContent>
                            </Card>
                        </div>
                        <div>
                            <Card className="border-0 shadow-lg bg-white/80 backdrop-blur h-full">
                                <CardHeader><CardTitle>Найближчі події</CardTitle></CardHeader>
                                <CardContent className="space-y-4">
                                    {events
                                        .filter(e => new Date(e.date) >= new Date())
                                        .sort((a,b) => new Date(a.date) - new Date(b.date))
                                        .slice(0, 5)
                                        .map(e => (
                                            <div key={e.id} className="p-3 rounded-lg border-l-4 border-blue-500 bg-gray-50">
                                                <h4 className="font-semibold">{e.title}</h4>
                                                <p className="text-sm text-gray-500">{format(new Date(e.date), 'dd.MM.yyyy')} {e.time}</p>
                                            </div>
                                        ))}
                                    {events.length === 0 && <p className="text-gray-500 text-center">Немає подій</p>}
                                </CardContent>
                            </Card>
                        </div>
                    </div>
                </div>
            );
        }

        function AdminPanel({ user }) {
            const [users, setUsers] = useState([]);
            const [content, setContent] = useState({ anns: [], polls: [], msgs: [] });
            const [auditLogs, setAuditLogs] = useState([]);
            const [selectedUser, setSelectedUser] = useState(null);
            const [isEditOpen, setIsEditOpen] = useState(false);
            const [platformName, setPlatformName] = useState("Платформа ГГР");

            useEffect(() => {
                if(user.role !== 'admin') return;
                const u1 = onSnapshot(getCollectionRef('users'), snap => setUsers(snap.docs.map(d => ({ id: d.id, ...d.data() }))));
                const u2 = onSnapshot(getCollectionRef('announcements'), snap => setContent(p => ({...p, anns: snap.docs.map(d => ({id: d.id, ...d.data()}))})));
                const u3 = onSnapshot(getCollectionRef('polls'), snap => setContent(p => ({...p, polls: snap.docs.map(d => ({id: d.id, ...d.data()}))})));
                const u4 = onSnapshot(query(getCollectionRef('audit_logs'), orderBy('created_date', 'desc'), limit(50)), snap => setAuditLogs(snap.docs.map(d => ({id: d.id, ...d.data()}))));
                return () => { u1(); u2(); u3(); u4(); };
            }, [user]);

            const handleUpdateUser = async () => {
                if(!selectedUser) return;
                await updateDoc(doc(getCollectionRef('users'), selectedUser.id), {
                    role: selectedUser.role,
                    position: selectedUser.position || '',
                    department: selectedUser.department || '',
                    is_active: selectedUser.is_active
                });
                logAction(user, 'update_user', 'User', `Updated user ${selectedUser.full_name} role to ${selectedUser.role}`);
                setIsEditOpen(false); setSelectedUser(null);
            };

            const deleteItem = async (col, id) => {
                if(confirm('Видалити цей елемент?')) {
                    await deleteDoc(doc(getCollectionRef(col), id));
                    logAction(user, 'delete', col, `Deleted item ${id}`);
                }
            };

            if(user.role !== 'admin') return <div className="flex h-96 items-center justify-center text-red-500 font-bold">Доступ заборонено</div>;

            return (
                <div className="space-y-6 animate-in fade-in">
                    <div>
                        <h1 className="text-3xl font-bold text-gray-900">Адмін-панель</h1>
                        <p className="text-gray-500 mt-1">Налаштування системи та управління користувачами</p>
                    </div>
                    
                    <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <Card className="p-6 flex items-center justify-between border-0 shadow-sm bg-white">
                            <div>
                                <p className="text-sm font-medium text-gray-500">Всього членів</p>
                                <p className="text-4xl font-bold text-gray-900">{users.length}</p>
                            </div>
                            <div className="p-3 bg-blue-500 rounded-xl text-white"><Users className="w-6 h-6"/></div>
                        </Card>
                        <Card className="p-6 flex items-center justify-between border-0 shadow-sm bg-white">
                            <div>
                                <p className="text-sm font-medium text-gray-500">Активні завдання</p>
                                <p className="text-4xl font-bold text-gray-900">0</p>
                            </div>
                            <div className="p-3 bg-emerald-500 rounded-xl text-white"><Activity className="w-6 h-6"/></div>
                        </Card>
                        <Card className="p-6 flex items-center justify-between border-0 shadow-sm bg-white">
                            <div>
                                <p className="text-sm font-medium text-gray-500">Активні голосування</p>
                                <p className="text-4xl font-bold text-gray-900">{content.polls.length}</p>
                            </div>
                            <div className="p-3 bg-purple-500 rounded-xl text-white"><Shield className="w-6 h-6"/></div>
                        </Card>
                    </div>

                    <Tabs defaultValue="users" className="mt-6">
                        <TabsList className="bg-white p-1 rounded-lg shadow-sm border">
                            <TabsTrigger value="users">Управління користувачами</TabsTrigger>
                            <TabsTrigger value="audit">Аудит-лог</TabsTrigger>
                            <TabsTrigger value="content">Контент</TabsTrigger>
                            <TabsTrigger value="settings">Налаштування</TabsTrigger>
                        </TabsList>
                        
                        <TabsContent value="users" className="mt-6">
                            <Card className="border-0 shadow-sm overflow-hidden">
                                <div className="p-6 border-b"><h3 className="font-bold">Члени ради</h3></div>
                                <div className="overflow-x-auto">
                                    <table className="w-full text-left text-sm">
                                        <thead className="bg-gray-50 border-b">
                                            <tr>
                                                <th className="p-4 font-medium text-gray-500">Ім'я</th>
                                                <th className="p-4 font-medium text-gray-500">Email</th>
                                                <th className="p-4 font-medium text-gray-500">Роль</th>
                                                <th className="p-4 font-medium text-gray-500">Посада</th>
                                                <th className="p-4 font-medium text-gray-500">Відділ</th>
                                                <th className="p-4 font-medium text-gray-500">Останній вхід</th>
                                                <th className="p-4 font-medium text-gray-500">Статус</th>
                                                <th className="p-4 font-medium text-gray-500">Дії</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            {users.map(u => (
                                                <tr key={u.id} className="border-b hover:bg-gray-50 transition-colors">
                                                    <td className="p-4 font-bold text-gray-900">{u.full_name}</td>
                                                    <td className="p-4 text-gray-500">{u.email}</td>
                                                    <td className="p-4"><span className={`px-2 py-1 rounded text-xs font-medium ${u.role === 'admin' ? 'bg-purple-100 text-purple-800' : 'bg-gray-100 text-gray-800'}`}>{u.role}</span></td>
                                                    <td className="p-4 text-gray-500">{u.position || '-'}</td>
                                                    <td className="p-4 text-gray-500">{u.department || '-'}</td>
                                                    <td className="p-4 text-gray-500">{u.last_seen ? format(new Date(u.last_seen), 'dd.MM HH:mm') : 'Never'}</td>
                                                    <td className="p-4"><span className={`px-2 py-1 rounded text-xs font-medium ${u.is_active !== false ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'}`}>{u.is_active !== false ? 'Активний' : 'Блок'}</span></td>
                                                    <td className="p-4 flex gap-3">
                                                        <button onClick={() => { setSelectedUser(u); setIsEditOpen(true); }} className="text-gray-500 hover:text-blue-600"><Pencil className="w-4 h-4"/></button>
                                                        <button className="text-gray-500 hover:text-orange-600"><Power className="w-4 h-4"/></button>
                                                        <button onClick={() => deleteItem('users', u.id)} className="text-gray-500 hover:text-red-600"><Trash2 className="w-4 h-4"/></button>
                                                    </td>
                                                </tr>
                                            ))}
                                        </tbody>
                                    </table>
                                </div>
                            </Card>
                        </TabsContent>

                        <TabsContent value="audit" className="mt-6">
                            <Card className="border-0 shadow-sm">
                                <CardHeader><CardTitle>Журнал дій</CardTitle></CardHeader>
                                <CardContent className="max-h-96 overflow-y-auto">
                                    <table className="w-full text-left text-sm">
                                        <thead><tr><th className="p-2">Час</th><th className="p-2">Користувач</th><th className="p-2">Дія</th><th className="p-2">Деталі</th></tr></thead>
                                        <tbody>
                                            {auditLogs.map(log => (
                                                <tr key={log.id} className="border-t">
                                                    <td className="p-2 text-gray-500">{format(new Date(log.created_date), 'dd.MM HH:mm')}</td>
                                                    <td className="p-2 font-medium">{log.performed_by}</td>
                                                    <td className="p-2"><Badge>{log.action}</Badge></td>
                                                    <td className="p-2 text-gray-600">{log.details}</td>
                                                </tr>
                                            ))}
                                        </tbody>
                                    </table>
                                </CardContent>
                            </Card>
                        </TabsContent>

                        <TabsContent value="content" className="space-y-6">
                            <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
                                <Card className="border-0 shadow-lg">
                                    <CardHeader><CardTitle>Оголошення</CardTitle></CardHeader>
                                    <CardContent className="max-h-80 overflow-y-auto space-y-2">
                                        {content.anns.map(a => (
                                            <div key={a.id} className="flex justify-between items-center p-3 border rounded bg-gray-50">
                                                <span className="font-medium truncate max-w-[200px]">{a.title}</span>
                                                <Button variant="ghost" size="sm" className="text-red-500" onClick={() => deleteItem('announcements', a.id)}><Trash2 className="w-4 h-4"/></Button>
                                            </div>
                                        ))}
                                    </CardContent>
                                </Card>
                                <Card className="border-0 shadow-lg">
                                    <CardHeader><CardTitle>Голосування</CardTitle></CardHeader>
                                    <CardContent className="max-h-80 overflow-y-auto space-y-2">
                                        {content.polls.map(p => (
                                            <div key={p.id} className="flex justify-between items-center p-3 border rounded bg-gray-50">
                                                <span className="font-medium truncate max-w-[200px]">{p.title}</span>
                                                <Button variant="ghost" size="sm" className="text-red-500" onClick={() => deleteItem('polls', p.id)}><Trash2 className="w-4 h-4"/></Button>
                                            </div>
                                        ))}
                                    </CardContent>
                                </Card>
                            </div>
                        </TabsContent>

                        <TabsContent value="settings" className="mt-6">
                            <Card>
                                <CardHeader><CardTitle>Налаштування платформи</CardTitle></CardHeader>
                                <CardContent className="space-y-4">
                                    <div>
                                        <label className="block text-sm font-medium mb-1">Назва платформи</label>
                                        <Input value={platformName} onChange={e => setPlatformName(e.target.value)}/>
                                    </div>
                                    <Button onClick={() => alert("Налаштування збережено (Mock)")}>Зберегти</Button>
                                </CardContent>
                            </Card>
                        </TabsContent>
                    </Tabs>

                    <Dialog open={isEditOpen} onOpenChange={setIsEditOpen}>
                        <DialogContent className="max-w-md">
                            <DialogHeader><DialogTitle className="text-xl font-bold">Редагувати користувача</DialogTitle></DialogHeader>
                            {selectedUser && (
                                <div className="space-y-5 py-2">
                                    <div>
                                        <label className="text-sm font-bold text-gray-800 mb-1 block">Повне ім'я</label>
                                        <Input value={selectedUser.full_name} onChange={e => setSelectedUser({...selectedUser, full_name: e.target.value})}/>
                                    </div>
                                    <div>
                                        <label className="text-sm font-bold text-gray-800 mb-1 block">Email</label>
                                        <Input disabled value={selectedUser.email} className="bg-gray-50 text-gray-500"/>
                                        <p className="text-xs text-gray-400 mt-1">Email не можна змінити</p>
                                    </div>
                                    <div>
                                        <label className="text-sm font-bold text-gray-800 mb-1 block">Роль</label>
                                        <select className="w-full border rounded-lg p-2 bg-white h-10" value={selectedUser.role} onChange={e => setSelectedUser({...selectedUser, role: e.target.value})}>
                                            <option value="user">user</option>
                                            <option value="admin">admin</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label className="text-sm font-bold text-gray-800 mb-1 block">Посада</label>
                                        <Input placeholder="напр., Представник батьків, Вчитель" value={selectedUser.position || ''} onChange={e => setSelectedUser({...selectedUser, position: e.target.value})}/>
                                    </div>
                                    <div>
                                        <label className="text-sm font-bold text-gray-800 mb-1 block">Відділ/Комітет</label>
                                        <Input placeholder="напр., Фінансовий комітет, Події" value={selectedUser.department || ''} onChange={e => setSelectedUser({...selectedUser, department: e.target.value})}/>
                                    </div>
                                    <div className="flex items-center gap-2 mt-2">
                                        <input type="checkbox" checked={selectedUser.is_active !== false} onChange={e => setSelectedUser({...selectedUser, is_active: e.target.checked})} className="w-5 h-5 rounded border-gray-300 text-emerald-500 focus:ring-emerald-500"/>
                                        <label className="text-sm font-bold text-gray-800">Акаунт активний</label>
                                    </div>
                                    <Button onClick={handleUpdateUser} variant="success" className="w-full mt-4 bg-emerald-50/50 text-emerald-600 hover:bg-emerald-100 border-none shadow-none font-bold">Зберегти зміни</Button>
                                </div>
                            )}
                        </DialogContent>
                    </Dialog>
                </div>
            );
        }

        function Profile({ user }) {
            const [editData, setEditData] = useState({ full_name: user.full_name, bio: user.bio || '', position: user.position || '', department: user.department || '' });
            const [isEditing, setIsEditing] = useState(false);

            const save = async () => {
                await updateDoc(doc(getCollectionRef('users'), user.id), editData);
                if (auth.currentUser) await updateProfile(auth.currentUser, { displayName: editData.full_name });
                logAction(user, 'update_profile', 'User', 'User updated own profile');
                setIsEditing(false);
            };

            return (
                <div className="space-y-6 animate-in fade-in">
                    <div className="flex justify-between items-center">
                        <h1 className="text-3xl font-bold">Мій профіль</h1>
                        {!isEditing ? (
                            <Button onClick={() => setIsEditing(true)} className="bg-[var(--primary)]"><Edit className="w-4 h-4 mr-2"/> Редагувати</Button>
                        ) : (
                            <div className="flex gap-2">
                                <Button variant="outline" onClick={() => setIsEditing(false)}>Скасувати</Button>
                                <Button onClick={save} className="bg-green-600 hover:bg-green-700"><Save className="w-4 h-4 mr-2"/> Зберегти</Button>
                            </div>
                        )}
                    </div>

                    <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        <Card className="lg:col-span-1 border-0 shadow-lg bg-white/80 backdrop-blur">
                            <CardContent className="p-6 flex flex-col items-center text-center">
                                <div className="w-32 h-32 rounded-full bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center text-white text-4xl font-bold mb-4 shadow-lg">
                                    {user.avatar_url ? <img src={user.avatar_url} className="w-full h-full rounded-full object-cover"/> : (user.full_name?.[0] || 'U')}
                                </div>
                                <h2 className="text-2xl font-bold text-gray-900">{user.full_name}</h2>
                                <Badge className="mt-2 bg-blue-100 text-blue-800 capitalize">{user.role}</Badge>
                                <div className="w-full mt-6 pt-6 border-t space-y-3 text-left text-sm text-gray-600">
                                    <div className="flex items-center gap-3"><Briefcase className="w-4 h-4"/> {user.position || 'Посада не вказана'}</div>
                                    <div className="flex items-center gap-3"><Building className="w-4 h-4"/> {user.department || 'Відділ не вказано'}</div>
                                    <div className="flex items-center gap-3"><Clock className="w-4 h-4"/> В системі з {user.created_date ? format(new Date(user.created_date), 'dd.MM.yyyy') : '-'}</div>
                                </div>
                            </CardContent>
                        </Card>

                        <Card className="lg:col-span-2 border-0 shadow-lg bg-white/80 backdrop-blur">
                            <CardHeader><CardTitle>Детальна інформація</CardTitle></CardHeader>
                            <CardContent className="space-y-6">
                                <div className="space-y-2">
                                    <label className="text-sm font-medium text-gray-500">Повне ім'я</label>
                                    {isEditing ? <Input value={editData.full_name} onChange={e => setEditData({...editData, full_name: e.target.value})}/> : <p className="text-lg">{user.full_name}</p>}
                                </div>
                                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                                    <div className="space-y-2">
                                        <label className="text-sm font-medium text-gray-500">Посада</label>
                                        {isEditing ? <Input value={editData.position} onChange={e => setEditData({...editData, position: e.target.value})}/> : <p className="text-lg">{user.position || '-'}</p>}
                                    </div>
                                    <div className="space-y-2">
                                        <label className="text-sm font-medium text-gray-500">Відділ</label>
                                        {isEditing ? <Input value={editData.department} onChange={e => setEditData({...editData, department: e.target.value})}/> : <p className="text-lg">{user.department || '-'}</p>}
                                    </div>
                                </div>
                                <div className="space-y-2">
                                    <label className="text-sm font-medium text-gray-500">Про себе</label>
                                    {isEditing ? <Textarea value={editData.bio} onChange={e => setEditData({...editData, bio: e.target.value})}/> : <p className="text-gray-700">{user.bio || 'Інформація відсутня'}</p>}
                                </div>
                            </CardContent>
                        </Card>
                    </div>
                </div>
            );
        }
        
        const App = () => {
            const [user, setUser] = useState(null);
            const [loading, setLoading] = useState(true);
            const [currentPage, setCurrentPage] = useState('Dashboard');

            useEffect(() => {
                // Initialize Auth
                const initAuth = async () => {
                    if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                        await signInWithCustomToken(auth, __initial_auth_token);
                    } else {
                        // Optionally: await signInAnonymously(auth); 
                        // Not forcing anonymous sign-in to allow manual login UI
                    }
                };
                initAuth();
                
                const unsubscribe = onAuthStateChanged(auth, async (currentUser) => {
                    if (currentUser) {
                        const userRef = doc(db, 'artifacts', appId, 'public', 'data', 'users', currentUser.uid);
                        
                        const userSnap = await getDoc(userRef);
                        if (!userSnap.exists()) {
                            // Fallback create
                            await setDoc(userRef, {
                                id: currentUser.uid,
                                full_name: currentUser.displayName || 'User',
                                email: currentUser.email,
                                role: 'user',
                                is_active: true,
                                created_date: new Date().toISOString(),
                            }, { merge: true });
                        } else {
                             await updateDoc(userRef, { last_seen: new Date().toISOString() });
                        }

                        const unsubUser = onSnapshot(userRef, (doc) => {
                             if (doc.exists()) {
                                 setUser({ ...currentUser, ...doc.data() });
                             }
                             setLoading(false);
                        });
                        return () => unsubUser();
                    } else {
                        setUser(null);
                        setLoading(false);
                    }
                });
                return () => unsubscribe();
            }, []);

            const renderPage = () => {
                switch (currentPage) {
                    case 'Dashboard': return <Dashboard user={user} setPage={setCurrentPage} />;
                    case 'Chat': return <Chat user={user} />;
                    case 'Tasks': return <Tasks user={user} />;
                    case 'Voting': return <Voting user={user} />;
                    case 'Announcements': return <Announcements user={user} />;
                    case 'Documents': return <Documents user={user} />;
                    case 'Calendar': return <Calendar user={user} />;
                    case 'AdminPanel': return <AdminPanel user={user} />;
                    case 'Profile': return <Profile user={user} />;
                    default: return <Dashboard user={user} setPage={setCurrentPage} />;
                }
            };

            if (loading) return <div className="flex h-screen items-center justify-center text-blue-600">Завантаження платформи...</div>;
            if (!user) return <Auth setUser={setUser} />;

            if (user.is_active === false) {
                return (
                    <div className="flex h-screen flex-col items-center justify-center bg-gray-50 p-4 text-center">
                        <Shield className="h-16 w-16 text-red-500 mb-4"/>
                        <h1 className="text-2xl font-bold text-gray-900">Акаунт деактивовано</h1>
                        <p className="text-gray-600 mt-2 max-w-md">Ваш доступ до платформи призупинено адміністратором.</p>
                        <Button onClick={() => signOut(auth)} className="mt-6">Вийти</Button>
                    </div>
                )
            }

            return (
                <Layout user={user} currentPage={currentPage} setPage={setCurrentPage}>
                    {renderPage()}
                </Layout>
            );
        };

        // Mount App
        const root = createRoot(document.getElementById('root'));
        root.render(<App />);

    </script>
</body>
</html>
