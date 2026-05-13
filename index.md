<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Football Intelligence Master Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #050505;
            color: #e0e0e0;
            overflow-x: hidden;
        }

        .neon-accent { color: #00ff88; }
        .bg-neon { background-color: #00ff88; }
        .border-neon { border-color: #00ff88; }
        
        .glass {
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .tab-content { display: none; }
        .tab-content.active { display: block; animation: fadeIn 0.5s ease; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .hero-gradient {
            background: linear-gradient(to top, #000 0%, rgba(0,0,0,0.4) 50%, transparent 100%);
        }
    </style>
</head>
<body>

    <!-- TOP BAR / LIVE DATA -->
    <div class="bg-neon text-black h-8 flex items-center justify-between px-4 text-[10px] font-black uppercase tracking-tighter fixed w-full z-[60]">
        <div class="flex gap-4">
            <span class="flex items-center gap-1"><i class="fa-solid fa-ticket"></i> Preț Bilet Mediu: 85.00 EUR</span>
            <span class="hidden md:flex items-center gap-1"><i class="fa-solid fa-calendar"></i> Sezon 2024/25</span>
        </div>
        <div class="flex gap-4">
            <span id="live-date"></span>
            <span id="live-time" class="tabular-nums"></span>
        </div>
    </div>

    <!-- NAVIGARE -->
    <nav class="fixed top-8 w-full z-50 bg-black/90 backdrop-blur-xl border-b border-white/5 h-14 flex items-center px-4">
        <div class="max-w-[1600px] w-full mx-auto flex items-center justify-between">
            <div class="flex items-center gap-2 cursor-pointer" onclick="showTab('home')">
                <i class="fa-solid fa-bolt neon-accent text-lg"></i>
                <span class="text-xl font-black italic tracking-tighter uppercase">FB<span class="neon-accent">CORE</span></span>
            </div>
            
            <div class="hidden lg:flex gap-6 text-[10px] font-black uppercase tracking-widest">
                <button onclick="showTab('home')" class="nav-link neon-accent border-b-2 border-neon pb-1">Acasă</button>
                <button onclick="showTab('istorie')" class="nav-link text-gray-500 hover:text-white pb-1">Istorie</button>
                <button onclick="showTab('reguli')" class="nav-link text-gray-500 hover:text-white pb-1">Reguli</button>
                <button onclick="showTab('antrenament')" class="nav-link text-gray-500 hover:text-white pb-1">Antrenament</button>
                <button onclick="showTab('legende')" class="nav-link text-gray-500 hover:text-white pb-1">Legende</button>
            </div>
            
            <button class="bg-white/5 border border-white/10 px-4 py-1.5 rounded text-[10px] font-bold uppercase hover:bg-neon hover:text-black transition-all">
                Cont Premium
            </button>
        </div>
    </nav>

    <main class="max-w-[1600px] mx-auto p-4 pt-28">
        
        <!-- HOME SECTION -->
        <section id="home" class="tab-content active">
            <div class="relative h-[450px] rounded-3xl overflow-hidden border border-white/10 shadow-2xl mb-4">
                <img src="https://images.unsplash.com/photo-1574629810360-7efbbe195018?q=80&w=2000" class="absolute inset-0 w-full h-full object-cover opacity-40" alt="[Imagine Stadion]">
                <div class="absolute inset-0 hero-gradient p-12 flex flex-col justify-end">
                    <span class="neon-accent text-xs font-black uppercase tracking-[0.5em] mb-4">Analiză & Strategie</span>
                    <h1 class="text-6xl md:text-8xl font-black italic uppercase leading-none mb-6 tracking-tighter">
                        Fotbalul este <br> <span class="neon-accent">Știință.</span>
                    </h1>
                    <div class="flex gap-4">
                        <button onclick="showTab('istorie')" class="bg-neon text-black px-8 py-4 rounded-xl font-black uppercase text-xs hover:scale-105 transition-all">Începe Călătoria</button>
                        <button onclick="showTab('reguli')" class="bg-white/10 backdrop-blur-md border border-white/20 px-8 py-4 rounded-xl font-black uppercase text-xs">Reguli Oficiale</button>
                    </div>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="glass p-6 rounded-2xl hover:border-neon/30 transition-all cursor-pointer" onclick="showTab('legende')">
                    <i class="fa-solid fa-star neon-accent mb-4 text-xl"></i>
                    <h3 class="text-xl font-black italic uppercase">Legendele</h3>
                    <p class="text-[10px] text-gray-500 mt-2">De la recordurile lui Ronaldo la magia lui Messi și Pelé.</p>
                </div>
                <div class="glass p-6 rounded-2xl hover:border-neon/30 transition-all cursor-pointer" onclick="showTab('antrenament')">
                    <i class="fa-solid fa-dumbbell neon-accent mb-4 text-xl"></i>
                    <h3 class="text-xl font-black italic uppercase">Antrenament</h3>
                    <p class="text-[10px] text-gray-500 mt-2">Circuite fizice, nutriție și refacere post-meci.</p>
                </div>
                <div class="glass p-6 rounded-2xl hover:border-neon/30 transition-all cursor-pointer" onclick="showTab('istorie')">
                    <i class="fa-solid fa-clock-rotate-left neon-accent mb-4 text-xl"></i>
                    <h3 class="text-xl font-black italic uppercase">Arhivă</h3>
                    <p class="text-[10px] text-gray-500 mt-2">Evoluția mingilor, a cupelor și momentele istorice.</p>
                </div>
            </div>
        </section>

        <!-- ISTORIE SECTION -->
        <section id="istorie" class="tab-content">
            <div class="grid grid-cols-1 md:grid-cols-12 gap-4">
                <div class="md:col-span-8 glass p-8 rounded-3xl">
                    <h2 class="text-4xl font-black italic uppercase mb-8 border-b border-white/10 pb-4">Originile & <span class="neon-accent">Evoluția</span></h2>
                    <div class="space-y-8">
                        <div class="flex gap-6">
                            <div class="neon-accent font-black text-xl italic w-24">Antichitate</div>
                            <div>
                                <h4 class="text-xs font-black uppercase text-white mb-2">Cuju & Harpastum</h4>
                                <p class="text-[11px] text-gray-400 leading-relaxed italic">Originile în China militară și în jocurile de antrenament ale legiunilor romane. Scopul era controlul mingii din piele fără mâini.</p>
                            </div>
                        </div>
                        <div class="flex gap-6">
                            <div class="neon-accent font-black text-xl italic w-24">1930</div>
                            <div>
                                <h4 class="text-xs font-black uppercase text-white mb-2">Apariția Primei Cupe Mondiale</h4>
                                <p class="text-[11px] text-gray-400 leading-relaxed italic">Jules Rimet a fondat turneul în Uruguay. 13 echipe au participat, iar gazdele au învins Argentina cu 4-2 în prima finală istorică.</p>
                            </div>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 pt-8">
                            <div class="bg-white/5 p-4 rounded-xl">
                                <h5 class="text-[10px] font-black neon-accent uppercase mb-2">Mingea & Echipamentul</h5>
                                <p class="text-[10px] text-gray-400">De la vezica de porc învelită în piele grea la mingile sintetice termo-lipite de azi.</p>
                            </div>
                            <div class="bg-white/5 p-4 rounded-xl">
                                <h5 class="text-[10px] font-black neon-accent uppercase mb-2">Modern vs Vechi</h5>
                                <p class="text-[10px] text-gray-400">Viteză medie crescută cu 35%, distanță parcursă dublă (de la 5km la 11km).</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="md:col-span-4 glass p-8 rounded-3xl relative overflow-hidden">
                    <h3 class="text-xl font-black italic uppercase mb-6 neon-accent">Momente Cheie</h3>
                    <div class="space-y-4">
                        <div class="flex justify-between border-b border-white/5 pb-2">
                            <span class="text-[10px] font-black text-gray-500">1863</span>
                            <span class="text-[10px] font-black uppercase text-white">Codul Londonez</span>
                        </div>
                        <div class="flex justify-between border-b border-white/5 pb-2">
                            <span class="text-[10px] font-black text-gray-500">1954</span>
                            <span class="text-[10px] font-black uppercase text-white">Revoluția Maghiară</span>
                        </div>
                        <div class="flex justify-between border-b border-white/5 pb-2">
                            <span class="text-[10px] font-black text-gray-500">1970</span>
                            <span class="text-[10px] font-black uppercase text-white">Era Pele</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- REGULI SECTION -->
        <section id="reguli" class="tab-content">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="glass p-8 rounded-3xl">
                    <i class="fa-solid fa-clock neon-accent mb-4 text-2xl"></i>
                    <h3 class="text-xl font-black italic uppercase mb-4">Meci & Timp</h3>
                    <ul class="text-[11px] text-gray-400 space-y-3 font-medium">
                        <li>• <span class="text-white">Durata:</span> 90 minute (2x45 min).</li>
                        <li>• <span class="text-white">Pauză:</span> Maxim 15 minute.</li>
                        <li>• <span class="text-white">Lovituri:</span> Departajare prin penalty-uri.</li>
                    </ul>
                </div>
                <div class="glass p-8 rounded-3xl">
                    <i class="fa-solid fa-bullseye neon-accent mb-4 text-2xl"></i>
                    <h3 class="text-xl font-black italic uppercase mb-4">Fazele Jocului</h3>
                    <ul class="text-[11px] text-gray-400 space-y-3 font-medium">
                        <li>• <span class="text-white">Lovitură Liberă:</span> Directă/Indirectă.</li>
                        <li>• <span class="text-white">Autul:</span> Deasupra capului, ambele mâini.</li>
                        <li>• <span class="text-white">Corner:</span> De la colțul terenului.</li>
                    </ul>
                </div>
                <div class="glass p-8 rounded-3xl">
                    <i class="fa-solid fa-shield-halved neon-accent mb-4 text-2xl"></i>
                    <h3 class="text-xl font-black italic uppercase mb-4">Arbitraj</h3>
                    <ul class="text-[11px] text-gray-400 space-y-3 font-medium">
                        <li>• <span class="text-white uppercase">Galben:</span> Avertisment.</li>
                        <li>• <span class="text-white uppercase text-red-500">Roșu:</span> Eliminare.</li>
                        <li>• <span class="text-white">VAR:</span> Arbitraj video pentru erori.</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- ANTRENAMENT SECTION -->
        <section id="antrenament" class="tab-content">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="bg-gradient-to-br from-[#0a0a0a] to-black p-10 rounded-3xl border border-[#00ff88]/10">
                    <h2 class="text-3xl font-black italic uppercase mb-8">Program <span class="neon-accent">Pro-Athlete</span></h2>
                    <div class="grid grid-cols-2 gap-8 text-[10px]">
                        <div>
                            <h4 class="font-black uppercase neon-accent mb-4">Luni-Miercuri: Fizic</h4>
                            <ul class="space-y-2 text-gray-400">
                                <li>Viteză / Sprinturi</li>
                                <li>Plyometrics</li>
                            </ul>
                        </div>
                        <div>
                            <h4 class="font-black uppercase neon-accent mb-4">Joi-Sâmbătă: Tehnic</h4>
                            <ul class="space-y-2 text-gray-400">
                                <li>Control minge</li>
                                <li>Finalizare</li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="glass p-10 rounded-3xl">
                    <h3 class="text-xl font-black italic uppercase mb-6 flex items-center gap-2">
                        <i class="fa-solid fa-apple-whole neon-accent"></i> Nutriție
                    </h3>
                    <div class="space-y-4 text-[10px]">
                        <div class="p-4 bg-white/5 rounded-xl border-l-4 border-neon">
                            <h5 class="font-black uppercase">Glicogen Re-Load</h5>
                            <p class="text-gray-500">Carbohidrați complecși cu 48h înainte.</p>
                        </div>
                        <div class="p-4 bg-white/5 rounded-xl border-l-4 border-blue-500">
                            <h5 class="font-black uppercase">Crioterapie</h5>
                            <p class="text-gray-500">Băi de gheață la 10°C post-efort.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- LEGENDE SECTION -->
        <section id="legende" class="tab-content">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="glass rounded-[2.5rem] p-8 flex flex-col md:flex-row gap-8 hover:border-neon/50 transition-all">
                    <div class="w-40 h-40 bg-white/5 rounded-3xl flex items-center justify-center text-6xl shrink-0">🐐</div>
                    <div>
                        <h3 class="text-4xl font-black italic uppercase mb-2">Lionel <span class="neon-accent">Messi</span></h3>
                        <p class="text-[10px] text-gray-500 font-bold uppercase mb-4">Magicianul / GOAT</p>
                        <div class="grid grid-cols-3 gap-2 mb-6">
                            <div class="bg-black p-2 rounded text-center">
                                <div class="neon-accent font-black text-xs">8</div>
                                <div class="text-[8px] uppercase text-gray-600">B. D'Or</div>
                            </div>
                            <div class="bg-black p-2 rounded text-center">
                                <div class="neon-accent font-black text-xs">44</div>
                                <div class="text-[8px] uppercase text-gray-600">Trofee</div>
                            </div>
                        </div>
                        <p class="text-[10px] text-gray-400 leading-relaxed italic">Viziune extraterestră și centru de greutate jos.</p>
                    </div>
                </div>
                <div class="glass rounded-[2.5rem] p-8 flex flex-col md:flex-row gap-8 hover:border-red-500/50 transition-all">
                    <div class="w-40 h-40 bg-white/5 rounded-3xl flex items-center justify-center text-6xl shrink-0">🤖</div>
                    <div>
                        <h3 class="text-4xl font-black italic uppercase mb-2">Cristiano <span class="text-red-500">Ronaldo</span></h3>
                        <p class="text-[10px] text-gray-500 font-bold uppercase mb-4">CR7 / Mașinăria</p>
                        <div class="grid grid-cols-3 gap-2 mb-6">
                            <div class="bg-black p-2 rounded text-center">
                                <div class="text-red-500 font-black text-xs">5</div>
                                <div class="text-[8px] uppercase text-gray-600">B. D'Or</div>
                            </div>
                            <div class="bg-black p-2 rounded text-center">
                                <div class="text-red-500 font-black text-xs">850+</div>
                                <div class="text-[8px] uppercase text-gray-600">Goluri</div>
                            </div>
                        </div>
                        <p class="text-[10px] text-gray-400 leading-relaxed italic">Putere fizică extremă și mentalitate de fier.</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <footer class="mt-20 border-t border-white/5 p-10 bg-black text-center md:text-left">
        <div class="max-w-[1600px] mx-auto grid grid-cols-1 md:grid-cols-4 gap-8">
            <div class="col-span-2">
                <h4 class="neon-accent font-black italic text-2xl mb-4 uppercase">Football Intelligence Hub</h4>
                <p class="text-gray-500 text-xs max-w-md">Analiză tehnică, date biometrice și arhivă istorică.</p>
            </div>
            <div>
                <h5 class="text-[10px] font-black uppercase text-white mb-4">Contact</h5>
                <p class="text-xs text-neon font-bold">contact@fbcore.ro</p>
            </div>
            <div class="text-right">
                <p class="text-[10px] text-gray-600 uppercase tracking-widest italic">Football Systems © 2024</p>
            </div>
        </div>
    </footer>

    <script>
        // Funcția de schimbare Tab-uri
        function showTab(tabId) {
            // Ascunde toate secțiunile
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            // Dezactivează toate butoanele din nav
            document.querySelectorAll('.nav-link').forEach(link => {
                link.classList.remove('neon-accent', 'border-b-2', 'border-neon');
                link.classList.add('text-gray-500');
            });

            // Afișează secțiunea selectată
            document.getElementById(tabId).classList.add('active');
            
            // Activează butonul corespunzător
            event.currentTarget.classList.add('neon-accent', 'border-b-2', 'border-neon');
            event.currentTarget.classList.remove('text-gray-500');

            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Live Clock și Data
        function updateTime() {
            const now = new Date();
            document.getElementById('live-date').textContent = now.toLocaleDateString('ro-RO');
            document.getElementById('live-time').textContent = now.toLocaleTimeString('ro-RO');
        }
        
        setInterval(updateTime, 1000);
        updateTime();
    </script>
</body>
</html>
