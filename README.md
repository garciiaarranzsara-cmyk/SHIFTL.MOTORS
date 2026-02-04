# SHIFTL.MOTORS
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
        .zone-1 { fill: #7DD3FC; } /* Azul Muy Claro */
        .zone-2 { fill: #38BDF8; } /* Azul Claro */
        .zone-3 { fill: #1E40AF; } /* Azul Oscuro */
        .zone-4 { fill: #94A3B8; } /* Gris Marca */
        .region:hover { filter: brightness(1.1); transform: scale(1.01); transform-origin: center; }

        /* Portal Privado */
        .portal-bg { background-color: #0F172A; color: white; }
        .kpi-card { 
            background: rgba(255,255,255,0.05); 
            border: 1px solid rgba(255,255,255,0.1); 
            border-radius: 1.5rem; 
            transition: all 0.3s ease;
            cursor: pointer;
        }
        .kpi-card.selected { background: rgba(56, 189, 248, 0.15); border-color: #38BDF8; }

        .check-circle {
            width: 24px; height: 24px; border: 2px solid rgba(255,255,255,0.3);
            border-radius: 50%; display: flex; align-items: center; justify-content: center;
        }
        .kpi-card.selected .check-circle { background: #38BDF8; border-color: #38BDF8; }

        /* Navbar centrado y fijo */
        nav.nav-fixed {
            position: fixed; top: 0; left: 0; width: 100%; z-index: 50;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid #f1f5f9;
        }
    </style>
</head>
<body class="bg-white text-slate-900 pt-20">

    <!-- NAVBAR FIJO Y CENTRADO -->
    <nav class="nav-fixed h-20 shadow-sm">
        <div class="max-w-7xl mx-auto px-6 h-full flex items-center justify-between">
            <!-- Logo con acceso a LinkedIn -->
            <a href="https://www.linkedin.com/company/shiftly-motors" target="_blank" class="flex items-center gap-2 group shrink-0">
                <div class="relative">
                    <svg width="35" height="35" viewBox="0 0 100 100" class="group-hover:rotate-12 transition-transform">
                        <path d="M20 50 L80 50 M80 50 L65 35 M80 50 L65 65" stroke="#0F172A" stroke-width="8" fill="none" stroke-linecap="round"/>
                        <circle cx="20" cy="50" r="8" fill="#38BDF8"/>
                    </svg>
                    <div class="absolute -top-1 -right-1 bg-blue-600 text-white rounded-full w-4 h-4 flex items-center justify-center text-[10px]">
                        <i class="fa-brands fa-linkedin-in"></i>
                    </div>
                </div>
                <span class="text-xl font-800 tracking-tighter font-montserrat uppercase hidden sm:inline">Shiftly<span class="text-sky-500">Motors</span></span>
            </a>

            <!-- Botones Centrados -->
            <div class="flex items-center justify-center gap-4 md:gap-10 mx-auto">
                <a href="#stock" class="font-bold text-xs md:text-sm text-slate-600 hover:text-sky-500 tracking-widest transition">STOCK</a>
                <a href="#zonas" class="font-bold text-xs md:text-sm text-slate-600 hover:text-sky-500 tracking-widest transition">ZONAS</a>
                <a href="#empleo" class="font-bold text-xs md:text-sm text-slate-600 hover:text-sky-500 tracking-widest transition">EMPLEO</a>
            </div>

            <!-- Acceso Empresa -->
            <button onclick="openPage('login')" class="bg-slate-900 text-white px-4 md:px-6 py-2 rounded-full text-xs md:text-sm font-bold hover:bg-sky-600 transition shrink-0">
                <i class="fa-solid fa-lock mr-2"></i> EMPRESA
            </button>
        </div>
    </nav>

    <!-- VISTA PRINCIPAL -->
    <main>
        <!-- Hero Section -->
        <section class="h-[85vh] relative flex items-center justify-center text-center px-6 overflow-hidden">
            <div class="absolute inset-0 z-0">
                <img src="https://images.unsplash.com/photo-1492144534655-ae79c964c9d7?auto=format&fit=crop&q=80&w=2000" class="w-full h-full object-cover" alt="Hero Car">
                <div class="absolute inset-0 bg-slate-900/60"></div>
            </div>
            <div class="relative z-10 max-w-4xl text-white">
                <h1 class="text-5xl md:text-7xl font-800 mb-6 font-montserrat leading-tight">
                    ¿Y si tu próximo destino <span class="text-sky-400">empieza</span> con un coche?
                </h1>
                <p class="text-xl text-slate-200 mb-10 font-light max-w-2xl mx-auto">Calidad certificada y transparencia en cada operación. Somos Shiftly Motors.</p>
                <div class="flex flex-wrap justify-center gap-4">
                    <a href="#stock" class="bg-sky-500 text-slate-900 px-10 py-4 rounded-xl font-bold hover:bg-sky-400 transition shadow-lg shadow-sky-500/20">Explorar Vehículos</a>
                </div>
            </div>
        </section>

        <!-- Stock de Coches (3 Unidades) -->
        <section id="stock" class="py-24 bg-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="flex flex-col md:flex-row justify-between items-end mb-12 gap-4">
                    <div>
                        <h2 class="text-3xl font-800 font-montserrat uppercase tracking-tight">Recién llegados</h2>
                        <p class="text-slate-400">Unidades exclusivas revisadas en 300 puntos.</p>
                    </div>
                </div>
                <div class="grid md:grid-cols-3 gap-8">
                    <!-- Coche 1 -->
                    <div class="group cursor-pointer bg-slate-50 rounded-3xl overflow-hidden shadow-sm hover:shadow-xl transition" 
                         onclick="openCar('Porsche 911 Carrera', 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=800', '135.000€', '450 CV • 2022')">
                        <div class="h-64 overflow-hidden relative">
                            <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=800" class="w-full h-full object-cover group-hover:scale-105 transition duration-500">
                            <div class="absolute top-4 right-4 bg-white/90 px-3 py-1 rounded-lg text-[10px] font-bold">ZONA 3</div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-bold">Porsche 911 Carrera</h3>
                            <div class="flex justify-between items-center mt-4">
                                <span class="text-2xl font-800 text-slate-900">135.000€</span>
                                <i class="fa-solid fa-circle-arrow-right text-sky-500 text-2xl"></i>
                            </div>
                        </div>
                    </div>
                    <!-- Coche 2 -->
                    <div class="group cursor-pointer bg-slate-50 rounded-3xl overflow-hidden shadow-sm hover:shadow-xl transition"
                         onclick="openCar('Audi RS6 Avant', 'https://images.unsplash.com/photo-1606152421802-db97b9c7a11b?auto=format&fit=crop&q=80&w=800', '118.900€', '600 CV • 2023')">
                        <div class="h-64 overflow-hidden relative">
                            <img src="https://images.unsplash.com/photo-1606152421802-db97b9c7a11b?auto=format&fit=crop&q=80&w=800" class="w-full h-full object-cover group-hover:scale-105 transition duration-500">
                            <div class="absolute top-4 right-4 bg-white/90 px-3 py-1 rounded-lg text-[10px] font-bold">ZONA 2</div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-bold">Audi RS6 Avant</h3>
                            <div class="flex justify-between items-center mt-4">
                                <span class="text-2xl font-800 text-slate-900">118.900€</span>
                                <i class="fa-solid fa-circle-arrow-right text-sky-500 text-2xl"></i>
                            </div>
                        </div>
                    </div>
                    <!-- Coche 3 -->
                    <div class="group cursor-pointer bg-slate-50 rounded-3xl overflow-hidden shadow-sm hover:shadow-xl transition"
                         onclick="openCar('Mercedes-AMG GT', 'https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&q=80&w=800', '142.500€', '523 CV • 2021')">
                        <div class="h-64 overflow-hidden relative">
                            <img src="https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&q=80&w=800" class="w-full h-full object-cover group-hover:scale-105 transition duration-500">
                            <div class="absolute top-4 right-4 bg-white/90 px-3 py-1 rounded-lg text-[10px] font-bold">ZONA 1</div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-bold">Mercedes-AMG GT</h3>
                            <div class="flex justify-between items-center mt-4">
                                <span class="text-2xl font-800 text-slate-900">142.500€</span>
                                <i class="fa-solid fa-circle-arrow-right text-sky-500 text-2xl"></i>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Zonas de Actuación (Mapa SVG) -->
        <section id="zonas" class="py-24 bg-slate-50">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-16">
                    <h2 class="text-4xl font-800 text-slate-900 mb-4 font-montserrat">Nuestra Cobertura</h2>
                    <p class="text-slate-500 max-w-2xl mx-auto">Selecciona tu zona para conocer el stock local disponible de inmediato.</p>
                </div>
                <div class="grid lg:grid-cols-2 gap-12 items-center">
                    <div class="bg-white p-10 rounded-[2.5rem] shadow-xl">
                        <svg viewBox="0 0 1000 700" class="w-full h-auto drop-shadow-2xl">
                            <!-- Zona 1: Norte -->
                            <path class="region zone-1" d="M150 50 L550 50 L550 180 L150 180 Z" />
                            <text x="310" y="125" fill="white" font-weight="800" font-size="28">ZONA 1</text>
                            <!-- Zona 2: Este -->
                            <path class="region zone-2" d="M550 50 L850 50 L850 400 L550 400 Z" />
                            <text x="660" y="230" fill="white" font-weight="800" font-size="28">ZONA 2</text>
                            <!-- Zona 3: Centro -->
                            <path class="region zone-3" d="M300 180 L550 180 L550 400 L300 400 Z" />
                            <text x="385" y="300" fill="white" font-weight="800" font-size="28">ZONA 3</text>
                            <!-- Zona 4: Sur e Islas -->
                            <path class="region zone-4" d="M150 400 L850 400 L850 650 L150 650 Z" />
                            <text x="460" y="540" fill="white" font-weight="800" font-size="28">ZONA 4</text>
                        </svg>
                    </div>
                    <div class="space-y-6">
                        <div class="flex items-center gap-4 p-5 bg-white rounded-2xl border-l-8 border-sky-300">
                            <span class="text-sky-500 font-bold">ZONA 1:</span>
                            <p class="text-sm text-slate-600">Galicia, Asturias, Cantabria, País Vasco, Navarra, La Rioja</p>
                        </div>
                        <div class="flex items-center gap-4 p-5 bg-white rounded-2xl border-l-8 border-sky-500">
                            <span class="text-sky-500 font-bold">ZONA 2:</span>
                            <p class="text-sm text-slate-600">Aragón, Cataluña, Islas Baleares, Comunidad Valenciana</p>
                        </div>
                        <div class="flex items-center gap-4 p-5 bg-white rounded-2xl border-l-8 border-blue-800">
                            <span class="text-blue-800 font-bold">ZONA 3:</span>
                            <p class="text-sm text-slate-600">Castilla y León, Comunidad de Madrid, Castilla La Mancha</p>
                        </div>
                        <div class="flex items-center gap-4 p-5 bg-white rounded-2xl border-l-8 border-slate-400">
                            <span class="text-slate-400 font-bold">ZONA 4:</span>
                            <p class="text-sm text-slate-600">Extremadura, Andalucía, Murcia, Canarias</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Employer Branding: Viaja con nosotros -->
        <section id="empleo" class="py-24 bg-slate-900 text-white overflow-hidden">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-16">
                    <span class="text-sky-400 font-bold uppercase tracking-widest text-xs">Employer Branding</span>
                    <h2 class="text-5xl font-800 font-montserrat my-4">Viaja con nosotros</h2>
                    <p class="text-slate-400 max-w-2xl mx-auto">Únete al equipo que está revolucionando la movilidad. Buscamos talento con hambre de carretera.</p>
                </div>
                
                <div class="grid md:grid-cols-2 gap-8">
                    <!-- Oferta 1 -->
                    <div class="bg-white/5 border border-white/10 p-8 rounded-3xl hover:border-sky-500 transition group">
                        <div class="flex justify-between items-start mb-6">
                            <h3 class="text-2xl font-bold font-montserrat">K.A. (Key Account)</h3>
                            <span class="bg-sky-500 text-slate-900 px-3 py-1 rounded-lg text-[10px] font-bold">OPEN</span>
                        </div>
                        <div class="space-y-4 mb-8">
                            <div class="flex items-center gap-3 text-slate-300">
                                <i class="fa-solid fa-money-bill-wave text-sky-400"></i>
                                <span class="font-bold">22.319,76€ Fijo</span>
                            </div>
                            <div class="flex items-center gap-3 text-slate-400 text-sm">
                                <i class="fa-solid fa-plus text-sky-400"></i>
                                <span>Retribución variable revisable según objetivos</span>
                            </div>
                        </div>
                        <button class="w-full border border-white/20 py-3 rounded-xl hover:bg-white hover:text-slate-900 transition font-bold">Inscribirme ahora</button>
                    </div>

                    <!-- Oferta 2 -->
                    <div class="bg-white/5 border border-white/10 p-8 rounded-3xl hover:border-sky-500 transition group">
                        <div class="flex justify-between items-start mb-6">
                            <h3 class="text-2xl font-bold font-montserrat">Coordinador Comercial</h3>
                            <span class="bg-sky-500 text-slate-900 px-3 py-1 rounded-lg text-[10px] font-bold">OPEN</span>
                        </div>
                        <div class="space-y-4 mb-8">
                            <div class="flex items-center gap-3 text-slate-300">
                                <i class="fa-solid fa-money-bill-wave text-sky-400"></i>
                                <span class="font-bold">22.420,06€ Fijo</span>
                            </div>
                            <div class="flex items-center gap-3 text-slate-400 text-sm">
                                <i class="fa-solid fa-plus text-sky-400"></i>
                                <span>Retribución variable revisable según objetivos</span>
                            </div>
                        </div>
                        <button class="w-full border border-white/20 py-3 rounded-xl hover:bg-white hover:text-slate-900 transition font-bold">Inscribirme ahora</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-slate-100 py-12 border-t border-slate-200">
            <div class="max-w-7xl mx-auto px-6 text-center">
                <p class="text-slate-500 text-sm">&copy; 2025 Shiftly Motors S.L. Todos los derechos reservados.</p>
            </div>
        </footer>
    </main>

    <!-- SUBPÁGINA: DETALLE COCHE -->
    <div id="page-car" class="page-overlay">
        <div class="max-w-6xl mx-auto px-6 py-20">
            <button onclick="closePage('car')" class="mb-10 text-slate-900 font-bold flex items-center gap-2 hover:text-sky-500">
                <i class="fa-solid fa-arrow-left"></i> VOLVER AL STOCK
            </button>
            <div class="grid lg:grid-cols-2 gap-16">
                <div class="rounded-[2.5rem] overflow-hidden shadow-2xl h-[500px]">
                    <img id="car-img" src="" class="w-full h-full object-cover">
                </div>
                <div>
                    <h2 id="car-title" class="text-5xl font-800 text-slate-900 mb-4 font-montserrat"></h2>
                    <p id="car-spec" class="text-sky-500 font-bold text-xl mb-6"></p>
                    <div id="car-price" class="text-4xl font-800 text-slate-900 mb-10"></div>
                    <div class="space-y-4 mb-10">
                        <div class="flex items-center gap-4 p-4 bg-slate-50 rounded-2xl">
                            <i class="fa-solid fa-shield-check text-sky-500"></i>
                            <span class="text-sm font-semibold">Garantía Platinum de 24 meses incluida.</span>
                        </div>
                    </div>
                    <button class="w-full bg-slate-900 text-white py-5 rounded-2xl font-bold shadow-xl">Contactar con un asesor</button>
                </div>
            </div>
        </div>
    </div>

    <!-- SUBPÁGINA: LOGIN -->
    <div id="page-login" class="page-overlay bg-slate-50 flex items-center justify-center">
        <div class="bg-white p-12 rounded-[2.5rem] shadow-2xl w-full max-w-md border border-slate-100">
            <div class="text-center mb-10">
                <h2 class="text-3xl font-800 font-montserrat text-slate-900">Shiftly Inside</h2>
                <p class="text-slate-400">Portal de Gestión Corporativa</p>
            </div>
            <div class="space-y-5">
                <input type="email" id="user-email" value="comercial@shiftly.com" class="w-full px-5 py-4 bg-slate-50 rounded-xl border border-slate-200 outline-none focus:border-sky-500 transition">
                <input type="password" id="user-pass" value="motors2025" class="w-full px-5 py-4 bg-slate-50 rounded-xl border border-slate-200 outline-none focus:border-sky-500 transition">
                <button onclick="login()" class="w-full bg-slate-900 text-white py-4 rounded-xl font-bold hover:bg-sky-600 transition">ACCEDER AL PANEL</button>
                <button onclick="closePage('login')" class="w-full text-slate-400 text-xs">Volver a la web</button>
            </div>
        </div>
    </div>

    <!-- SUBPÁGINA: DASHBOARD EMPLEADO (KPIs) -->
    <div id="page-dashboard" class="page-overlay portal-bg">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-6 mb-16 border-b border-white/10 pb-10">
                <div>
                    <h2 class="text-4xl font-800 font-montserrat">Mi Variable</h2>
                    <p class="text-sky-400">Seguimiento de KPIs • Asesor Comercial</p>
                </div>
                <div class="flex gap-4">
                    <div class="bg-white/5 px-6 py-3 rounded-2xl border border-white/10">
                        <span class="block text-[10px] text-slate-400 uppercase font-bold">Base Variable</span>
                        <span class="text-xl font-bold text-white">20.093,18€</span>
                    </div>
                    <button onclick="logout()" class="bg-red-500/20 text-red-400 px-6 py-3 rounded-2xl font-bold">SALIR</button>
                </div>
            </div>

            <div class="grid lg:grid-cols-3 gap-12">
                <div class="lg:col-span-2 space-y-4">
                    <h3 class="text-xl font-bold mb-6 font-montserrat">KPIs del Mes</h3>
                    
                    <div class="kpi-card p-6 flex items-center justify-between" onclick="toggleKPI(0)">
                        <div class="flex items-center gap-4">
                            <div class="check-circle" id="check-0"><i class="fa-solid fa-check text-white text-[10px]"></i></div>
                            <div>
                                <h4 class="font-bold">Unidades de Venta</h4>
                                <p class="text-xs text-slate-400">Meta: 5 unidades/mes</p>
                            </div>
                        </div>
                    </div>

                    <div class="kpi-card p-6 flex items-center justify-between" onclick="toggleKPI(1)">
                        <div class="flex items-center gap-4">
                            <div class="check-circle" id="check-1"><i class="fa-solid fa-check text-white text-[10px]"></i></div>
                            <div>
                                <h4 class="font-bold">Margen Bruto</h4>
                                <p class="text-xs text-slate-400">Meta: 10% por operación</p>
                            </div>
                        </div>
                    </div>

                    <div class="kpi-card p-6 flex items-center justify-between" onclick="toggleKPI(2)">
                        <div class="flex items-center gap-4">
                            <div class="check-circle" id="check-2"><i class="fa-solid fa-check text-white text-[10px]"></i></div>
                            <div>
                                <h4 class="font-bold">Financiación</h4>
                                <p class="text-xs text-slate-400">Meta: 45% de las ventas</p>
                            </div>
                        </div>
                    </div>

                    <div class="kpi-card p-6 flex items-center justify-between" onclick="toggleKPI(3)">
                        <div class="flex items-center gap-4">
                            <div class="check-circle" id="check-3"><i class="fa-solid fa-check text-white text-[10px]"></i></div>
                            <div>
                                <h4 class="font-bold">Satisfacción Cliente</h4>
                                <p class="text-xs text-slate-400">Meta: NPS > 80 puntos</p>
                            </div>
                        </div>
                    </div>

                    <div class="kpi-card p-6 flex items-center justify-between" onclick="toggleKPI(4)">
                        <div class="flex items-center gap-4">
                            <div class="check-circle" id="check-4"><i class="fa-solid fa-check text-white text-[10px]"></i></div>
                            <div>
                                <h4 class="font-bold">Uso CRM</h4>
                                <p class="text-xs text-slate-400">Meta: 100% de registros</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="lg:col-span-1">
                    <div class="bg-white rounded-[2.5rem] p-10 text-slate-900 sticky top-32 shadow-2xl">
                        <h3 class="font-bold text-xl mb-8">Estado de Retribución</h3>
                        <div class="space-y-4 mb-10">
                            <div class="flex justify-between pb-4 border-b">
                                <span class="text-slate-500 text-sm">KPIs Cumplidos:</span>
                                <span class="font-bold" id="res-count">0 / 5</span>
                            </div>
                            <div class="flex justify-between pb-4 border-b text-sky-600">
                                <span class="text-sm font-bold">% Variable:</span>
                                <span class="font-bold" id="res-percent">0%</span>
                            </div>
                        </div>
                        <div class="bg-slate-900 rounded-2xl p-6 text-white text-center">
                            <span class="block text-[10px] uppercase text-slate-400 mb-1">Total a Percibir</span>
                            <div class="text-4xl font-900" id="res-total">0,00€</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Funciones Navegación
        function openPage(id) {
            document.getElementById('page-' + id).classList.add('active');
            document.body.style.overflow = 'hidden';
        }
        function closePage(id) {
            document.getElementById('page-' + id).classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        // Detalle Coche
        function openCar(title, img, price, spec) {
            document.getElementById('car-title').innerText = title;
            document.getElementById('car-img').src = img;
            document.getElementById('car-price').innerText = price;
            document.getElementById('car-spec').innerText = spec;
            openPage('car');
        }

        // Login
        function login() {
            const email = document.getElementById('user-email').value;
            const pass = document.getElementById('user-pass').value;
            if(email === 'comercial@shiftly.com' && pass === 'motors2025') {
                closePage('login');
                openPage('dashboard');
            } else {
                alert("Usuario o contraseña incorrectos.");
            }
        }
        function logout() { closePage('dashboard'); }

        // KPIs Lógica
        const BASE_VAR = 20093.18;
        let kpisSelected = [false, false, false, false, false];

        function toggleKPI(index) {
            kpisSelected[index] = !kpisSelected[index];
            updateKPIUI();
        }

        function updateKPIUI() {
            const count = kpisSelected.filter(v => v).length;
            let perc = 0;
            if(count === 1) perc = 0.05;
            else if(count === 2) perc = 0.15;
            else if(count === 3) perc = 0.30;
            else if(count === 4) perc = 0.50;
            else if(count === 5) perc = 1.00;

            const total = BASE_VAR * perc;

            kpisSelected.forEach((sel, i) => {
                const card = document.querySelectorAll('.kpi-card')[i];
                if(sel) card.classList.add('selected');
                else card.classList.remove('selected');
            });

            document.getElementById('res-count').innerText = `${count} / 5`;
            document.getElementById('res-percent').innerText = `${(perc * 100)}%`;
            document.getElementById('res-total').innerText = total.toLocaleString('es-ES', { minimumFractionDigits: 2 }) + '€';
        }
    </script>
</body>
</html>
