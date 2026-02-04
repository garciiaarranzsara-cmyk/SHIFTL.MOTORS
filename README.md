# SHIFTLY.MOTORS
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shiftly Motors | Tu Destino Empieza Aquí</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700;800&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --azul-oscuro: #0F172A;
            --azul-claro: #38BDF8;
            --gris-marca: #64748B;
        }
        body { font-family: 'Inter', sans-serif; scroll-behavior: smooth; overflow-x: hidden; }
        h1, h2, h3, .font-montserrat { font-family: 'Montserrat', sans-serif; }

        /* Capas de subpáginas */
        .page-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: white; z-index: 100; display: none;
            overflow-y: auto; opacity: 0; transform: translateY(30px);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .page-overlay.active { display: block; opacity: 1; transform: translateY(0); }

        /* Mapa Interactivo */
        .region { transition: all 0.3s ease; cursor: pointer; stroke: #fff; stroke-width: 1.5; }
        .zone-1 { fill: #7DD3FC; } 
        .zone-2 { fill: #38BDF8; } 
        .zone-3 { fill: #1E40AF; } 
        .zone-4 { fill: #94A3B8; } 
        .region:hover { filter: brightness(1.1); transform: scale(1.01); }

        /* Portal Privado */
        .portal-bg { background-color: #0F172A; color: white; }
        .kpi-card, .course-card { 
            background: rgba(255,255,255,0.05); 
            border: 1px solid rgba(255,255,255,0.1); 
            border-radius: 1.5rem; 
            transition: all 0.3s ease;
        }
        .kpi-card.selected { background: rgba(56, 189, 248, 0.15); border-color: #38BDF8; }
        
        /* Timeline / Road de Evaluación */
        .road-step { position: relative; padding-left: 3rem; border-left: 2px dashed rgba(255,255,255,0.2); margin-bottom: 2rem; }
        .road-step::before { 
            content: ''; position: absolute; left: -9px; top: 0; 
            width: 16px; height: 16px; border-radius: 50%; background: #1e293b; border: 2px solid #38BDF8;
        }
        .road-step.active::before { background: #38BDF8; box-shadow: 0 0 15px #38BDF8; }
        .road-step.locked { opacity: 0.4; filter: grayscale(1); cursor: not-allowed; }

        /* Navbar centrado y fijo */
        nav.nav-fixed {
            position: fixed; top: 0; left: 0; width: 100%; z-index: 50;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid #f1f5f9;
        }

        .internal-tab.active { color: #38BDF8; border-bottom: 2px solid #38BDF8; }
        
        .logo-img { height: 45px; width: auto; object-fit: contain; }
    </style>
</head>
<body class="bg-white text-slate-900 pt-20">

    <!-- NAVBAR FIJO Y CENTRADO -->
    <nav class="nav-fixed h-20 shadow-sm">
        <div class="max-w-7xl mx-auto px-6 h-full flex items-center justify-between">
            <!-- LOGOTIPO OFICIAL CON ENLACE LINKEDIN -->
            <a href="https://www.linkedin.com/company/shiftly-motors" target="_blank" class="flex items-center gap-3 group shrink-0 relative">
                <img src="WhatsApp Image 2026-01-26 at 21.22.06.jpeg" alt="Shiftly Motors Logo" class="logo-img group-hover:scale-105 transition-transform" onerror="this.src='https://via.placeholder.com/150x50?text=Shiftly+Motors'">
                <div class="absolute -top-1 -right-2 bg-blue-600 text-white rounded-full w-4 h-4 flex items-center justify-center text-[10px]"><i class="fa-brands fa-linkedin-in"></i></div>
            </a>

            <!-- Botones Centrados -->
            <div class="flex items-center justify-center gap-6 md:gap-10 mx-auto">
                <a href="#stock" class="font-bold text-xs md:text-sm text-slate-600 hover:text-sky-500 tracking-widest transition">STOCK</a>
                <a href="#zonas" class="font-bold text-xs md:text-sm text-slate-600 hover:text-sky-500 tracking-widest transition">ZONAS</a>
                <a href="#empleo" class="font-bold text-xs md:text-sm text-slate-600 hover:text-sky-500 tracking-widest transition">EMPLEO</a>
            </div>

            <!-- Acceso Empresa -->
            <button onclick="openPage('login')" class="bg-slate-900 text-white px-4 md:px-6 py-2 rounded-full text-xs md:text-sm font-bold hover:bg-sky-600 transition">
                <i class="fa-solid fa-lock mr-2"></i> EMPRESA
            </button>
        </div>
    </nav>

    <!-- VISTA PRINCIPAL -->
    <main>
        <!-- Hero Section -->
        <section class="h-[80vh] relative flex items-center justify-center text-center px-6 overflow-hidden">
            <div class="absolute inset-0 z-0">
                <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=2000" class="w-full h-full object-cover">
                <div class="absolute inset-0 bg-slate-900/60"></div>
            </div>
            <div class="relative z-10 max-w-4xl text-white">
                <h1 class="text-5xl md:text-7xl font-800 mb-6 font-montserrat leading-tight">¿Y si tu próximo destino <span class="text-sky-400">empieza</span> con un coche?</h1>
                <p class="text-xl text-slate-200 mb-10 font-light max-w-2xl mx-auto">Calidad, transparencia y el logotipo que marca el camino. Somos Shiftly Motors.</p>
                <a href="#stock" class="bg-sky-500 text-slate-900 px-10 py-4 rounded-xl font-bold hover:bg-sky-400 transition shadow-lg">Explorar Stock</a>
            </div>
        </section>

        <!-- Stock (3 Unidades) -->
        <section id="stock" class="py-24 max-w-7xl mx-auto px-6">
            <h2 class="text-3xl font-800 mb-12 font-montserrat border-l-4 border-sky-500 pl-4">VEHÍCULOS DESTACADOS</h2>
            <div class="grid md:grid-cols-3 gap-8">
                <!-- Coche 1 -->
                <div class="group cursor-pointer bg-slate-50 rounded-3xl overflow-hidden shadow-sm" onclick="openCar('Porsche 911 Carrera', 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=800', '135.000€', '2022')">
                    <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=800" class="h-64 w-full object-cover group-hover:scale-105 transition duration-500">
                    <div class="p-6 flex justify-between items-center"><span class="font-bold text-xl uppercase">Porsche 911</span><span class="text-sky-500 font-800">135k€</span></div>
                </div>
                <!-- Coche 2 -->
                <div class="group cursor-pointer bg-slate-50 rounded-3xl overflow-hidden shadow-sm" onclick="openCar('Audi RS6 Performance', 'https://images.unsplash.com/photo-1606152421802-db97b9c7a11b?auto=format&fit=crop&q=80&w=800', '118.900€', '2023')">
                    <img src="https://images.unsplash.com/photo-1606152421802-db97b9c7a11b?auto=format&fit=crop&q=80&w=800" class="h-64 w-full object-cover group-hover:scale-105 transition duration-500">
                    <div class="p-6 flex justify-between items-center"><span class="font-bold text-xl uppercase">Audi RS6</span><span class="text-sky-500 font-800">118k€</span></div>
                </div>
                <!-- Coche 3 -->
                <div class="group cursor-pointer bg-slate-50 rounded-3xl overflow-hidden shadow-sm" onclick="openCar('Mercedes AMG GT', 'https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&q=80&w=800', '142.500€', '2021')">
                    <img src="https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&q=80&w=800" class="h-64 w-full object-cover group-hover:scale-105 transition duration-500">
                    <div class="p-6 flex justify-between items-center"><span class="font-bold text-xl uppercase">Mercedes AMG</span><span class="text-sky-500 font-800">142k€</span></div>
                </div>
            </div>
        </section>

        <!-- Zonas (Mapa) -->
        <section id="zonas" class="py-24 bg-slate-50">
            <div class="max-w-7xl mx-auto px-6 text-center">
                <h2 class="text-3xl font-800 mb-12 font-montserrat uppercase">Cobertura Nacional</h2>
                <div class="flex flex-col lg:flex-row gap-12 items-center bg-white p-10 rounded-3xl shadow-xl">
                    <svg viewBox="0 0 1000 600" class="w-full max-w-2xl h-auto drop-shadow-2xl">
                        <path class="region zone-1" d="M150 50 L550 50 L550 150 L150 150 Z" />
                        <path class="region zone-2" d="M550 50 L850 50 L850 350 L550 350 Z" />
                        <path class="region zone-3" d="M300 150 L550 150 L550 350 L300 350 Z" />
                        <path class="region zone-4" d="M150 350 L850 350 L850 550 L150 550 Z" />
                        <text x="320" y="110" fill="white" font-weight="bold" font-size="24">ZONA 1</text>
                        <text x="650" y="220" fill="white" font-weight="bold" font-size="24">ZONA 2</text>
                        <text x="400" y="270" fill="white" font-weight="bold" font-size="24">ZONA 3</text>
                        <text x="480" y="470" fill="white" font-weight="bold" font-size="24">ZONA 4</text>
                    </svg>
                    <div class="text-left space-y-4 w-full">
                        <div class="p-4 bg-sky-50 rounded-xl border-l-4 border-sky-300"><strong>Zona 1:</strong> Norte de España</div>
                        <div class="p-4 bg-sky-100 rounded-xl border-l-4 border-sky-500"><strong>Zona 2:</strong> Este y Baleares</div>
                        <div class="p-4 bg-blue-50 rounded-xl border-l-4 border-blue-800"><strong>Zona 3:</strong> Centro</div>
                        <div class="p-4 bg-slate-50 rounded-xl border-l-4 border-slate-400"><strong>Zona 4:</strong> Sur e Canarias</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Empleo -->
        <section id="empleo" class="py-24 bg-slate-900 text-white">
            <div class="max-w-7xl mx-auto px-6">
                <h2 class="text-4xl font-800 mb-12 text-center font-montserrat">Viaja con nosotros</h2>
                <div class="grid md:grid-cols-2 gap-8">
                    <div class="bg-white/5 p-8 rounded-3xl border border-white/10 hover:border-sky-500 transition">
                        <h3 class="text-2xl font-bold mb-4">K.A. (Key Account)</h3>
                        <div class="text-sky-400 font-bold text-xl mb-2">22.319,76€ Fijo</div>
                        <p class="text-sm text-slate-400 mb-6">+ Retribución variable revisable</p>
                        <button class="w-full bg-sky-500 text-slate-900 py-3 rounded-xl font-bold uppercase tracking-widest text-xs">Postularse</button>
                    </div>
                    <div class="bg-white/5 p-8 rounded-3xl border border-white/10 hover:border-sky-500 transition">
                        <h3 class="text-2xl font-bold mb-4">Coordinador Comercial</h3>
                        <div class="text-sky-400 font-bold text-xl mb-2">22.420,06€ Fijo</div>
                        <p class="text-sm text-slate-400 mb-6">+ Retribución variable revisable</p>
                        <button class="w-full bg-sky-500 text-slate-900 py-3 rounded-xl font-bold uppercase tracking-widest text-xs">Postularse</button>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- SUBPÁGINA: LOGIN -->
    <div id="page-login" class="page-overlay bg-slate-50 flex items-center justify-center">
        <div class="bg-white p-12 rounded-[2.5rem] shadow-2xl w-full max-w-md border border-slate-100">
            <div class="text-center mb-10">
                <img src="WhatsApp Image 2026-01-26 at 21.22.06.jpeg" class="h-16 mx-auto mb-6" onerror="this.src='https://via.placeholder.com/150x50?text=Logo'">
                <h2 class="text-xl font-800 font-montserrat text-slate-900 uppercase tracking-tighter">Shiftly Inside</h2>
            </div>
            <div class="space-y-4">
                <input type="email" id="u-email" value="comercial@shiftly.com" class="w-full px-5 py-4 border rounded-xl outline-none focus:border-sky-500">
                <input type="password" id="u-pass" value="motors2025" class="w-full px-5 py-4 border rounded-xl outline-none focus:border-sky-500">
                <button onclick="login()" class="w-full bg-slate-900 text-white py-4 rounded-xl font-bold hover:bg-sky-600 transition">ACCEDER AL PANEL</button>
                <button onclick="closePage('login')" class="w-full text-slate-400 text-xs">Volver a la web</button>
            </div>
        </div>
    </div>

    <!-- PORTAL DEL EMPLEADO (DINÁMICO) -->
    <div id="page-dashboard" class="page-overlay portal-bg">
        <div class="max-w-7xl mx-auto px-6 py-10">
            <!-- Header Dashboard con Logo -->
            <div class="flex flex-col md:flex-row justify-between items-center mb-12 border-b border-white/10 pb-8">
                <div class="flex items-center gap-6 mb-4 md:mb-0">
                    <img src="WhatsApp Image 2026-01-26 at 21.22.06.jpeg" class="h-12 brightness-0 invert" onerror="this.style.display='none'">
                    <div class="h-8 w-px bg-white/20 hidden md:block"></div>
                    <div class="flex gap-6">
                        <button onclick="showTab('kpis')" id="tab-kpis" class="internal-tab active font-bold py-2 transition text-sm">Rendimiento</button>
                        <button onclick="showTab('formaciones')" id="tab-formaciones" class="internal-tab font-bold py-2 transition text-sm">Formaciones</button>
                        <button onclick="showTab('evaluacion')" id="tab-evaluacion" class="internal-tab font-bold py-2 transition text-sm">¿Cuántos km llevas?</button>
                    </div>
                </div>
                <button onclick="closePage('dashboard')" class="bg-red-500/10 hover:bg-red-500/20 text-red-500 px-6 py-2 rounded-xl font-bold text-xs">Cerrar Sesión</button>
            </div>

            <!-- TAB 1: KPIs -->
            <div id="view-kpis" class="tab-content">
                <div class="grid lg:grid-cols-3 gap-12">
                    <div class="lg:col-span-2 space-y-4">
                        <h3 class="text-2xl font-bold font-montserrat mb-6">Mis Objetivos Mensuales</h3>
                        <div class="kpi-card p-6 flex justify-between cursor-pointer" onclick="toggleKPI(0)">
                            <div><h4 class="font-bold">Unidades de Venta</h4><p class="text-xs text-slate-400">Meta: 5u / mes</p></div>
                            <div class="w-8 h-8 rounded-full border-2 border-white/20 flex items-center justify-center kpi-check" id="k-0"><i class="fa-solid fa-check opacity-0"></i></div>
                        </div>
                        <div class="kpi-card p-6 flex justify-between cursor-pointer" onclick="toggleKPI(1)">
                            <div><h4 class="font-bold">Margen Bruto</h4><p class="text-xs text-slate-400">Meta: 10% por operación</p></div>
                            <div class="w-8 h-8 rounded-full border-2 border-white/20 flex items-center justify-center kpi-check" id="k-1"><i class="fa-solid fa-check opacity-0"></i></div>
                        </div>
                        <div class="kpi-card p-6 flex justify-between cursor-pointer" onclick="toggleKPI(2)">
                            <div><h4 class="font-bold">Financiación</h4><p class="text-xs text-slate-400">Meta: 45% de las ventas</p></div>
                            <div class="w-8 h-8 rounded-full border-2 border-white/20 flex items-center justify-center kpi-check" id="k-2"><i class="fa-solid fa-check opacity-0"></i></div>
                        </div>
                        <div class="kpi-card p-6 flex justify-between cursor-pointer" onclick="toggleKPI(3)">
                            <div><h4 class="font-bold">Satisfacción Cliente</h4><p class="text-xs text-slate-400">Meta: NPS > 80</p></div>
                            <div class="w-8 h-8 rounded-full border-2 border-white/20 flex items-center justify-center kpi-check" id="k-3"><i class="fa-solid fa-check opacity-0"></i></div>
                        </div>
                        <div class="kpi-card p-6 flex justify-between cursor-pointer" onclick="toggleKPI(4)">
                            <div><h4 class="font-bold">Uso CRM</h4><p class="text-xs text-slate-400">Meta: 100% registros</p></div>
                            <div class="w-8 h-8 rounded-full border-2 border-white/20 flex items-center justify-center kpi-check" id="k-4"><i class="fa-solid fa-check opacity-0"></i></div>
                        </div>
                    </div>
                    <div class="bg-white text-slate-900 p-8 rounded-[2rem] shadow-2xl h-fit">
                        <h3 class="font-bold mb-4 uppercase text-xs text-slate-400 tracking-widest">Retribución Variable</h3>
                        <div class="text-slate-400 text-[10px] mb-1">Base de Cálculo: 20.093,18€</div>
                        <div class="text-5xl font-900 mb-6 text-slate-900" id="v-total">0,00€</div>
                        <div class="bg-sky-50 p-4 rounded-xl border border-sky-100 text-[10px] text-sky-700 leading-relaxed">
                            <i class="fa-solid fa-circle-info mr-1"></i> El variable se calcula según el número de KPIs marcados (5%, 15%, 30%, 50%, 100%).
                        </div>
                    </div>
                </div>
            </div>

            <!-- TAB 2: Formaciones -->
            <div id="view-formaciones" class="tab-content hidden">
                <h3 class="text-2xl font-bold font-montserrat mb-8">Mis Formaciones Interactiva</h3>
                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                    <!-- Soft Skills -->
                    <div class="course-card p-8 group hover:border-sky-500 transition relative">
                        <div class="absolute top-4 right-4 text-[10px] bg-sky-500/20 text-sky-400 px-2 py-1 rounded">Q1</div>
                        <i class="fa-solid fa-comments text-3xl text-sky-400 mb-6"></i>
                        <h4 class="font-bold text-lg mb-2">Soft Skills</h4>
                        <p class="text-[10px] text-slate-400 mb-6 uppercase tracking-wider font-semibold">01/01 al 31/03</p>
                        <button class="w-full py-3 bg-sky-500 text-slate-900 rounded-xl font-bold text-[10px] uppercase group-hover:bg-white transition">Empezar Curso</button>
                    </div>
                    <!-- Orientación -->
                    <div class="course-card p-8 group hover:border-sky-500 transition relative">
                        <i class="fa-solid fa-chart-line text-3xl text-sky-400 mb-6"></i>
                        <h4 class="font-bold text-lg mb-2">Objetivos y Desempeño</h4>
                        <p class="text-[10px] text-slate-400 mb-6 uppercase tracking-wider font-semibold">01/01 al 31/03</p>
                        <button class="w-full py-3 bg-sky-500 text-slate-900 rounded-xl font-bold text-[10px] uppercase group-hover:bg-white transition">Empezar Curso</button>
                    </div>
                    <!-- CRM -->
                    <div class="course-card p-8 group hover:border-sky-500 transition relative">
                        <i class="fa-solid fa-laptop-code text-3xl text-sky-400 mb-6"></i>
                        <h4 class="font-bold text-lg mb-2">Herramientas CRM</h4>
                        <p class="text-[10px] text-slate-400 mb-6 uppercase tracking-wider font-semibold">01/01 al 31/03</p>
                        <button class="w-full py-3 bg-sky-500 text-slate-900 rounded-xl font-bold text-[10px] uppercase group-hover:bg-white transition">Empezar Curso</button>
                    </div>
                    <!-- Fidelización -->
                    <div class="course-card p-8 group hover:border-sky-500 transition relative">
                        <i class="fa-solid fa-heart-circle-check text-3xl text-sky-400 mb-6"></i>
                        <h4 class="font-bold text-lg mb-2">Experiencia Cliente</h4>
                        <p class="text-[10px] text-slate-400 mb-6 uppercase tracking-wider font-semibold">01/01 al 31/03</p>
                        <button class="w-full py-3 bg-sky-500 text-slate-900 rounded-xl font-bold text-[10px] uppercase group-hover:bg-white transition">Empezar Curso</button>
                    </div>
                </div>
            </div>

            <!-- TAB 3: Evaluación KM -->
            <div id="view-evaluacion" class="tab-content hidden">
                <div class="flex items-center gap-4 mb-10">
                    <h3 class="text-3xl font-800 font-montserrat uppercase tracking-tight">¿Cuántos km llevas?</h3>
                </div>
                <div class="max-w-3xl space-y-4">
                    <!-- ROADMAP -->
                    <div class="road-step active">
                        <div class="bg-white/5 p-6 rounded-2xl border border-sky-500/30">
                            <h4 class="font-bold text-xl text-white">Definimos tus objetivos</h4>
                            <p class="text-sky-400 text-sm font-bold mb-3 uppercase tracking-widest">Enero - Marzo</p>
                            <p class="text-slate-400 text-sm leading-relaxed mb-4">Estamos en el punto de salida. Establecemos juntos las metas de este viaje para que sepas qué velocidad alcanzar.</p>
                            <button class="px-8 py-3 bg-sky-500 text-slate-900 rounded-xl font-bold text-xs shadow-lg shadow-sky-500/20">ACCEDER A EVALUACIÓN</button>
                        </div>
                    </div>
                    
                    <div class="road-step locked">
                        <div class="p-6 rounded-2xl bg-white/5 border border-white/5">
                            <h4 class="font-bold text-lg">Primera revisión</h4>
                            <p class="text-slate-500 text-xs uppercase mb-2">Abril - Junio</p>
                            <span class="text-[10px] bg-red-500/10 text-red-400 px-2 py-1 rounded border border-red-500/20"><i class="fa-solid fa-lock mr-1"></i> CERRADO AL ACCESO</span>
                        </div>
                    </div>
                    
                    <div class="road-step locked">
                        <div class="p-6 rounded-2xl bg-white/5 border border-white/5">
                            <h4 class="font-bold text-lg">Todos nos evaluamos</h4>
                            <p class="text-slate-500 text-xs uppercase mb-2">Mayo - Julio</p>
                            <span class="text-[10px] bg-red-500/10 text-red-400 px-2 py-1 rounded border border-red-500/20"><i class="fa-solid fa-lock mr-1"></i> CERRADO AL ACCESO</span>
                        </div>
                    </div>

                    <div class="road-step locked">
                        <div class="p-6 rounded-2xl bg-white/5 border border-white/5">
                            <h4 class="font-bold text-lg">Calibramos Ajustes</h4>
                            <p class="text-slate-500 text-xs uppercase mb-2">Julio - Septiembre</p>
                            <span class="text-[10px] bg-red-500/10 text-red-400 px-2 py-1 rounded border border-red-500/20"><i class="fa-solid fa-lock mr-1"></i> CERRADO AL ACCESO</span>
                        </div>
                    </div>

                    <div class="road-step locked">
                        <div class="p-6 rounded-2xl bg-white/5 border border-white/5">
                            <h4 class="font-bold text-lg">Enviaremos tu feedback</h4>
                            <p class="text-slate-500 text-xs uppercase mb-2">Octubre - Noviembre</p>
                            <span class="text-[10px] bg-red-500/10 text-red-400 px-2 py-1 rounded border border-red-500/20"><i class="fa-solid fa-lock mr-1"></i> CERRADO AL ACCESO</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- DETALLE COCHE -->
    <div id="page-car" class="page-overlay">
        <div class="max-w-4xl mx-auto px-6 py-20 text-center">
            <button onclick="closePage('car')" class="mb-10 font-bold text-slate-900"><i class="fa-solid fa-arrow-left"></i> VOLVER AL CATÁLOGO</button>
            <img id="c-img" class="w-full h-[450px] object-cover rounded-[3rem] mb-10 shadow-2xl">
            <h2 id="c-title" class="text-5xl font-800 font-montserrat mb-4"></h2>
            <p id="c-price" class="text-3xl text-sky-500 font-900"></p>
        </div>
    </div>

    <!-- FOOTER -->
    <footer class="bg-slate-100 py-12 border-t border-slate-200">
        <div class="max-w-7xl mx-auto px-6 flex flex-col items-center gap-6">
            <img src="WhatsApp Image 2026-01-26 at 21.22.06.jpeg" class="h-10 grayscale opacity-50" onerror="this.style.display='none'">
            <p class="text-slate-400 text-xs">&copy; 2025 Shiftly Motors S.L. Tu próximo destino empieza aquí.</p>
        </div>
    </footer>

    <script>
        function openPage(id) { document.getElementById('page-'+id).classList.add('active'); document.body.style.overflow='hidden'; }
        function closePage(id) { document.getElementById('page-'+id).classList.remove('active'); document.body.style.overflow='auto'; }
        function openCar(t, i, p) { document.getElementById('c-title').innerText=t; document.getElementById('c-img').src=i; document.getElementById('c-price').innerText=p; openPage('car'); }
        
        function login() { 
            const e = document.getElementById('u-email').value; const p = document.getElementById('u-pass').value;
            if(e==='comercial@shiftly.com' && p==='motors2025') { closePage('login'); openPage('dashboard'); } else { alert("Acceso Denegado: Credenciales no válidas."); }
        }

        function showTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(c => c.classList.add('hidden'));
            document.querySelectorAll('.internal-tab').forEach(t => t.classList.remove('active'));
            document.getElementById('view-' + tabId).classList.remove('hidden');
            document.getElementById('tab-' + tabId).classList.add('active');
        }

        let kSelected = [false, false, false, false, false];
        const BASE = 20093.18;
        function toggleKPI(i) {
            kSelected[i] = !kSelected[i];
            const count = kSelected.filter(v=>v).length;
            let perc = 0;
            if(count===1) perc = 0.05; else if(count===2) perc = 0.15; else if(count===3) perc = 0.30; else if(count===4) perc = 0.50; else if(count===5) perc = 1.0;
            
            document.querySelectorAll('.kpi-check').forEach((el, idx) => {
                const card = el.closest('.kpi-card');
                if(kSelected[idx]) { el.classList.add('bg-sky-50'); el.classList.add('border-sky-500'); el.querySelector('i').classList.remove('opacity-0'); card.classList.add('selected'); }
                else { el.classList.remove('bg-sky-50'); el.classList.remove('border-sky-500'); el.querySelector('i').classList.add('opacity-0'); card.classList.remove('selected'); }
            });
            document.getElementById('v-total').innerText = (BASE * perc).toLocaleString('es-ES', {minimumFractionDigits:2}) + '€';
        }
    </script>
</body>
</html>
