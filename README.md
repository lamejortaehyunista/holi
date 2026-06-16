<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Libro Ilustrado: Kanban para Metalmecánica</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Playfair+Display:ital,wght@0,600;0,700;1,400&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
        }
        .serif-title {
            font-family: 'Playfair Display', serif;
        }
        
        /* Estilos de impresión específicos para las tarjetas Kanban */
        @media print {
            body * {
                visibility: hidden;
            }
            #printable-card-area, #printable-card-area * {
                visibility: visible;
            }
            #printable-card-area {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                max-width: 500px;
                border: 2px dashed #000 !important;
                padding: 16px;
                background: white !important;
                color: black !important;
            }
            .no-print {
                display: none !important;
            }
        }
    </style>
</head>
<body class="bg-slate-900 text-slate-100 min-h-screen flex flex-col justify-between selection:bg-amber-500 selection:text-slate-900">

    <!-- Header / Navbar -->
    <header class="border-b border-slate-800 bg-slate-950/80 backdrop-blur sticky top-0 z-50 no-print">
        <div class="max-w-6xl mx-auto px-4 py-4 flex flex-col sm:flex-row items-center justify-between gap-4">
            <div class="flex items-center gap-3">
                <div class="p-2 bg-gradient-to-tr from-amber-500 to-orange-600 rounded-lg text-slate-950 font-bold shadow-lg shadow-amber-500/10">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 17V7m0 10a2 2 0 01-2 2H5a2 2 0 01-2-2V7a2 2 0 012-2h2a2 2 0 012 2m0 10a2 2 0 002 2h2a2 2 0 002-2M9 7a2 2 0 012-2h2a2 2 0 012 2m0 10V7m0 10a2 2 0 002 2h2a2 2 0 002-2V7a2 2 0 00-2-2h-2a2 2 0 00-2 2" />
                    </svg>
                </div>
                <div>
                    <h1 class="font-extrabold text-lg tracking-tight bg-gradient-to-r from-amber-400 to-orange-500 bg-clip-text text-transparent">KAIZEN METAL</h1>
                    <p class="text-xs text-slate-400">Guía Kanban para Prevención de Deterioro</p>
                </div>
            </div>
            
            <nav class="flex items-center gap-1 bg-slate-900 p-1 rounded-full border border-slate-800 text-sm">
                <button onclick="goToPage('book')" id="btn-nav-book" class="px-4 py-1.5 rounded-full transition-all font-medium text-amber-400 bg-slate-800">
                    📖 El Libro
                </button>
                <button onclick="goToPage('generator')" id="btn-nav-generator" class="px-4 py-1.5 rounded-full transition-all font-medium text-slate-400 hover:text-slate-100">
                    🛠️ Generador de Tarjetas
                </button>
            </nav>
        </div>
    </header>

    <!-- Main Container -->
    <main class="max-w-6xl mx-auto px-4 py-8 flex-grow w-full">
        
        <!-- SECTION 1: THE BOOK -->
        <div id="section-book" class="space-y-8">
            
            <!-- Book Welcome Banner -->
            <div class="relative overflow-hidden rounded-2xl bg-gradient-to-br from-slate-950 via-slate-900 to-slate-950 border border-slate-800 p-8 sm:p-12 shadow-2xl flex flex-col md:flex-row items-center gap-8">
                <div class="absolute top-0 right-0 w-96 h-96 bg-amber-500/5 rounded-full blur-3xl -z-10"></div>
                <div class="absolute bottom-0 left-0 w-96 h-96 bg-orange-600/5 rounded-full blur-3xl -z-10"></div>
                
                <div class="flex-1 space-y-4 text-center md:text-left">
                    <span class="px-3 py-1 text-xs font-semibold uppercase tracking-wider text-amber-400 bg-amber-500/10 rounded-full border border-amber-500/20">
                        Manual Práctico Ilustrado
                    </span>
                    <h2 class="serif-title text-4xl sm:text-5xl font-black text-slate-100 leading-tight">
                        Metales Impecables con <span class="text-amber-500">Kanban</span>
                    </h2>
                    <p class="text-slate-400 max-w-lg text-lg">
                        Aprende cómo el control visual evita la oxidación, las rayaduras y los golpes de tus materias primas en el taller. Una guía ágil para operarios y dueños.
                    </p>
                    <div class="flex flex-wrap justify-center md:justify-start gap-4 pt-2">
                        <button onclick="changeChapter(1)" class="px-5 py-2.5 bg-amber-500 hover:bg-amber-600 active:scale-95 text-slate-950 font-bold rounded-xl transition duration-200 shadow-lg shadow-amber-500/20 flex items-center gap-2">
                            Comenzar Lectura 
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                            </svg>
                        </button>
                        <button onclick="goToPage('generator')" class="px-5 py-2.5 bg-slate-800 hover:bg-slate-700 active:scale-95 text-slate-200 font-semibold rounded-xl transition duration-200 border border-slate-700">
                            Diseñar Tarjetas
                        </button>
                    </div>
                </div>
                
                <!-- Graphic Cover Illustration -->
                <div class="w-full md:w-80 flex justify-center">
                    <div class="relative bg-slate-950 p-6 rounded-2xl border-2 border-amber-500/30 shadow-xl w-64 rotate-2 hover:rotate-0 transition-transform duration-300">
                        <div class="absolute -top-3 -right-3 bg-red-500 text-white text-[10px] font-bold px-2 py-1 rounded shadow-md uppercase tracking-wider">
                            Antioxidación
                        </div>
                        <div class="space-y-4">
                            <!-- Visual Rack representation -->
                            <div class="h-28 bg-slate-900 rounded-lg flex flex-col justify-end p-2 border border-slate-800 relative">
                                <div class="absolute top-2 left-2 text-[10px] text-slate-500">Rack de Almacenamiento</div>
                                <!-- Metal Bars in rack -->
                                <div class="space-y-1.5">
                                    <div class="h-3 bg-slate-700 rounded-full w-full flex items-center justify-between px-2 overflow-hidden border border-slate-600">
                                        <div class="w-1.5 h-1.5 bg-emerald-500 rounded-full"></div>
                                        <span class="text-[8px] text-slate-400 font-bold">Acero Cal. 12</span>
                                    </div>
                                    <div class="h-3 bg-slate-700 rounded-full w-4/5 flex items-center justify-between px-2 overflow-hidden border border-slate-600">
                                        <div class="w-1.5 h-1.5 bg-emerald-500 rounded-full"></div>
                                        <span class="text-[8px] text-slate-400 font-bold">Inox 304</span>
                                    </div>
                                    <div class="h-3 bg-slate-800 rounded-full w-1/2 flex items-center justify-between px-2 overflow-hidden border border-slate-700 opacity-50">
                                        <div class="w-1.5 h-1.5 bg-red-500 rounded-full"></div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Small Card Overlay -->
                            <div class="bg-amber-500 text-slate-950 p-2.5 rounded border-l-4 border-amber-700 shadow-md">
                                <div class="text-[10px] font-bold tracking-wider uppercase">KANBAN DE PROTECCIÓN</div>
                                <div class="text-xs font-black mt-0.5">Barras Bronce 1"</div>
                                <div class="flex justify-between items-center mt-2 pt-1 border-t border-amber-600/30 text-[9px] font-semibold">
                                    <span>Apilado Máx: 5</span>
                                    <span>Lote: 10 u.</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Interactive Chapters Section -->
            <div class="grid grid-cols-1 lg:grid-cols-4 gap-8 pt-4">
                
                <!-- Chapters Navigation Sidebar -->
                <div class="lg:col-span-1 space-y-2">
                    <h3 class="text-sm font-bold uppercase tracking-wider text-slate-500 px-3">Índice del Libro</h3>
                    <div class="space-y-1">
                        <button onclick="changeChapter(1)" id="btn-chap-1" class="w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 bg-slate-800/80 text-amber-400 border-l-4 border-amber-500">
                            <span class="text-xs font-mono opacity-60">Cap. 1</span>
                            <span class="font-medium text-sm">El Enemigo Silencioso</span>
                        </button>
                        <button onclick="changeChapter(2)" id="btn-chap-2" class="w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 text-slate-400 hover:bg-slate-800/40 hover:text-slate-200">
                            <span class="text-xs font-mono opacity-60">Cap. 2</span>
                            <span class="font-medium text-sm">El Kanban de Cuidado</span>
                        </button>
                        <button onclick="changeChapter(3)" id="btn-chap-3" class="w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 text-slate-400 hover:bg-slate-800/40 hover:text-slate-200">
                            <span class="text-xs font-mono opacity-60">Cap. 3</span>
                            <span class="font-medium text-sm">Diseño de la Tarjeta</span>
                        </button>
                        <button onclick="changeChapter(4)" id="btn-chap-4" class="w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 text-slate-400 hover:bg-slate-800/40 hover:text-slate-200">
                            <span class="text-xs font-mono opacity-60">Cap. 4</span>
                            <span class="font-medium text-sm">Flujo en el Taller</span>
                        </button>
                        <button onclick="changeChapter(5)" id="btn-chap-5" class="w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 text-slate-400 hover:bg-slate-800/40 hover:text-slate-200">
                            <span class="text-xs font-mono opacity-60">Cap. 5</span>
                            <span class="font-medium text-sm">Plan de 5 Pasos</span>
                        </button>
                    </div>

                    <!-- Small Tip Card -->
                    <div class="p-4 bg-slate-950 rounded-xl border border-slate-800 space-y-2 mt-6">
                        <div class="flex items-center gap-2 text-amber-500">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                            <span class="text-xs font-bold uppercase tracking-wider">Sabías que...</span>
                        </div>
                        <p class="text-xs text-slate-400 leading-relaxed">
                            El exceso de inventario en metalmecánica no solo cuesta dinero, sino que incrementa en un 40% el riesgo de oxidación por almacenamiento estático y golpes en el traslado manual constante.
                        </p>
                    </div>
                </div>

                <!-- Active Chapter Content Display -->
                <div class="lg:col-span-3 bg-slate-950 border border-slate-800 rounded-2xl p-6 sm:p-10 shadow-xl min-h-[400px] flex flex-col justify-between">
                    
                    <div id="chapter-content" class="space-y-6">
                        <!-- Chapter contents injected dynamically here by JS -->
                    </div>

                    <!-- Navigation Footer inside Chapter Card -->
                    <div class="border-t border-slate-800/80 pt-6 mt-8 flex items-center justify-between">
                        <button onclick="navigateChapter(-1)" id="btn-prev-chap" class="px-4 py-2 bg-slate-900 hover:bg-slate-800 text-slate-300 rounded-lg text-sm font-medium transition flex items-center gap-2 disabled:opacity-30 disabled:pointer-events-none">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M9.707 16.707a1 1 0 01-1.414 0l-6-6a1 1 0 010-1.414l6-6a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l4.293 4.293a1 1 0 010 1.414z" clip-rule="evenodd" />
                            </svg>
                            Anterior
                        </button>
                        <span id="chapter-indicator" class="text-xs font-semibold tracking-widest text-slate-500 uppercase">
                            Capítulo 1 de 5
                        </span>
                        <button onclick="navigateChapter(1)" id="btn-next-chap" class="px-4 py-2 bg-amber-500 hover:bg-amber-600 text-slate-950 rounded-lg text-sm font-bold transition flex items-center gap-2">
                            Siguiente
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                            </svg>
                        </button>
                    </div>

                </div>

            </div>

        </div>

        <!-- SECTION 2: THE GENERATOR -->
        <div id="section-generator" class="hidden space-y-8">
            
            <div class="text-center max-w-2xl mx-auto space-y-2">
                <span class="px-3 py-1 text-xs font-bold uppercase tracking-wider text-orange-400 bg-orange-500/10 rounded-full border border-orange-500/20">
                    Herramienta de Taller
                </span>
                <h2 class="serif-title text-3xl sm:text-4xl font-extrabold text-slate-100">
                    Generador de Tarjetas Kanban Antideterioro
                </h2>
                <p class="text-slate-400 text-sm">
                    Completa los datos técnicos de tu material para generar una tarjeta visual lista para plastificar. El plastificado protege la tarjeta de los aceites de mecanizado y refrigerantes.
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">
                
                <!-- Generator Controls Panel (Left) -->
                <div class="lg:col-span-5 bg-slate-950 border border-slate-800 rounded-2xl p-6 space-y-5 shadow-xl">
                    <h3 class="text-sm font-bold uppercase tracking-wider text-slate-400 border-b border-slate-800 pb-2">
                        Configuración de la Tarjeta
                    </h3>
                    
                    <div class="space-y-4">
                        <!-- Card Type (Color Coding) -->
                        <div>
                            <label class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1.5">Categoría de Material (Color)</label>
                            <div class="grid grid-cols-3 gap-2">
                                <button onclick="setCardColor('steel')" id="col-btn-steel" class="border border-slate-700 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2 border-2 border-amber-500 ring-2 ring-amber-500/20">
                                    <span class="w-3 h-3 rounded-full bg-amber-500"></span> Acero Carb.
                                </button>
                                <button onclick="setCardColor('stainless')" id="col-btn-stainless" class="border border-slate-800 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2">
                                    <span class="w-3 h-3 rounded-full bg-blue-500"></span> Inoxidables
                                </button>
                                <button onclick="setCardColor('aluminum')" id="col-btn-aluminum" class="border border-slate-800 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2">
                                    <span class="w-3 h-3 rounded-full bg-emerald-500"></span> Alum/Bronce
                                </button>
                            </div>
                        </div>

                        <!-- Material Name -->
                        <div>
                            <label for="input-mat-name" class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1">Nombre del Material</label>
                            <input type="text" id="input-mat-name" oninput="updateCardPreview()" value="Plancha de Acero A36 - 1/8x4x8 pies" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-3 py-2 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
                        </div>

                        <!-- Grid: Code & Stack Limit -->
                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label for="input-mat-code" class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1">Código de Ubicación</label>
                                <input type="text" id="input-mat-code" oninput="updateCardPreview()" value="RACK-A2" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-3 py-2 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
                            </div>
                            <div>
                                <label for="input-max-stack" class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1">Límite Apilado</label>
                                <input type="text" id="input-max-stack" oninput="updateCardPreview()" value="Máximo 10 planchas" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-3 py-2 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
                            </div>
                        </div>

                        <!-- Grid: Batch Qty & Reorder Point -->
                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label for="input-batch-qty" class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1">Cantidad por Lote</label>
                                <input type="text" id="input-batch-qty" oninput="updateCardPreview()" value="15 Unidades" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-3 py-2 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
                            </div>
                            <div>
                                <label for="input-reorder-point" class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1">Punto de Re-pedido</label>
                                <input type="text" id="input-reorder-point" oninput="updateCardPreview()" value="3 Unidades (Mínimo)" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-3 py-2 text-sm text-slate-100 focus:outline-none focus:border-amber-500">
                            </div>
                        </div>

                        <!-- Degradation Preventive Measures checkbox list -->
                        <div class="space-y-2">
                            <label class="block text-xs font-bold uppercase tracking-wider text-slate-400">Medidas de Conservación Obligatorias</label>
                            
                            <label class="flex items-center gap-2 text-sm text-slate-300 bg-slate-900/50 p-2 rounded border border-slate-800/80 cursor-pointer hover:bg-slate-900">
                                <input type="checkbox" id="check-oil" onchange="updateCardPreview()" checked class="accent-amber-500">
                                <span>Aplicar aceite protector anti-óxido</span>
                            </label>

                            <label class="flex items-center gap-2 text-sm text-slate-300 bg-slate-900/50 p-2 rounded border border-slate-800/80 cursor-pointer hover:bg-slate-900">
                                <input type="checkbox" id="check-separator" onchange="updateCardPreview()" checked class="accent-amber-500">
                                <span>Usar tacos de madera/goma (no metal-metal)</span>
                            </label>

                            <label class="flex items-center gap-2 text-sm text-slate-300 bg-slate-900/50 p-2 rounded border border-slate-800/80 cursor-pointer hover:bg-slate-900">
                                <input type="checkbox" id="check-lona" onchange="updateCardPreview()" class="accent-amber-500">
                                <span>Mantener cubierto con lona impermeable</span>
                            </label>
                        </div>

                        <!-- Special Instructions -->
                        <div>
                            <label for="input-instructions" class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-1">Notas Especiales de Manejo</label>
                            <textarea id="input-instructions" oninput="updateCardPreview()" rows="2" class="w-full bg-slate-900 border border-slate-800 rounded-lg px-3 py-2 text-xs text-slate-100 focus:outline-none focus:border-amber-500 placeholder-slate-600" placeholder="Ej: No arrastrar para evitar rayones mecánicos. Transportar entre 2 personas."></textarea>
                        </div>
                    </div>

                </div>

                <!-- Preview / Action Column (Right) -->
                <div class="lg:col-span-7 flex flex-col items-center justify-center space-y-6">
                    
                    <div class="w-full max-w-[480px]">
                        <h4 class="text-xs font-bold text-center uppercase tracking-widest text-slate-500 mb-2">Vista previa en tiempo real</h4>
                        
                        <!-- Printable Area Core -->
                        <div id="printable-card-area" class="bg-slate-950 p-1.5 rounded-2xl border-4 border-dashed border-amber-500/50 shadow-2xl transition duration-200">
                            
                            <!-- The Card Container -->
                            <div class="bg-slate-900 text-slate-100 rounded-xl overflow-hidden border border-slate-800 max-w-[440px] mx-auto shadow-lg">
                                
                                <!-- Card Header (Color coded top bar) -->
                                <div id="card-header-bar" class="bg-amber-500 text-slate-950 p-4 transition-colors">
                                    <div class="flex justify-between items-start">
                                        <div>
                                            <span class="text-[9px] font-black tracking-widest uppercase bg-slate-950/20 px-2 py-0.5 rounded-full">
                                                TARJETA KANBAN DE ALMACÉN
                                            </span>
                                            <h3 id="card-title" class="text-lg font-black mt-1 leading-tight">
                                                Plancha de Acero A36 - 1/8x4x8 pies
                                            </h3>
                                        </div>
                                        <div class="text-right">
                                            <span class="text-[10px] font-mono opacity-80">Ubicación</span>
                                            <div id="card-code" class="text-sm font-black tracking-wider">RACK-A2</div>
                                        </div>
                                    </div>
                                </div>

                                <!-- Card Specs Matrix -->
                                <div class="p-4 grid grid-cols-3 gap-2 border-b border-slate-800 bg-slate-950/50">
                                    <div class="bg-slate-900/80 p-2 rounded border border-slate-800 text-center">
                                        <span class="text-[8px] uppercase font-bold tracking-wider text-slate-500 block">Tamaño Lote</span>
                                        <span id="card-batch" class="text-xs font-black text-slate-200">15 Unidades</span>
                                    </div>
                                    <div class="bg-slate-900/80 p-2 rounded border border-slate-800 text-center">
                                        <span class="text-[8px] uppercase font-bold tracking-wider text-slate-500 block">Re-Pedido</span>
                                        <span id="card-reorder" class="text-xs font-black text-red-400">3 Unidades</span>
                                    </div>
                                    <div class="bg-slate-900/80 p-2 rounded border border-slate-800 text-center">
                                        <span class="text-[8px] uppercase font-bold tracking-wider text-slate-500 block">Apilado Máx</span>
                                        <span id="card-stack" class="text-xs font-black text-amber-500">10 planchas</span>
                                    </div>
                                </div>

                                <!-- Prevention Measures -->
                                <div class="p-4 space-y-2.5">
                                    <h4 class="text-[9px] font-bold uppercase tracking-wider text-slate-500">REQUISITOS OBLIGATORIOS ANTI-DETERIORO:</h4>
                                    
                                    <div id="card-measures-container" class="space-y-1.5">
                                        <!-- Will be filled by JS -->
                                    </div>
                                </div>

                                <!-- Card Instructions / Notes -->
                                <div class="px-4 pb-4 pt-2 border-t border-slate-800/60 bg-slate-900">
                                    <span class="text-[8px] uppercase font-bold tracking-wider text-slate-500 block mb-0.5">NOTAS DE MANEJO SEGURO (Mecánico y Humedad):</span>
                                    <p id="card-notes" class="text-[11px] text-slate-400 italic leading-snug">
                                        No arrastrar para evitar rayones mecánicos. Transportar entre 2 personas.
                                    </p>
                                </div>

                                <!-- Footer Sign-off -->
                                <div class="bg-slate-950 px-4 py-2 flex justify-between items-center border-t border-slate-800 text-[8px] text-slate-500 font-medium">
                                    <span>Control de Calidad Taller Metalmecánico</span>
                                    <span>Retirar tarjeta para re-pedido</span>
                                </div>

                            </div>

                        </div>
                    </div>

                    <!-- Print and Lamination Notice/Actions -->
                    <div class="flex flex-col gap-3 w-full max-w-md">
                        <button onclick="window.print()" class="w-full bg-gradient-to-r from-amber-500 to-orange-600 hover:from-amber-600 hover:to-orange-700 active:scale-95 text-slate-950 font-extrabold py-3.5 px-6 rounded-xl transition duration-150 shadow-xl shadow-amber-500/10 flex items-center justify-center gap-2">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 002 2h2m2 4h6a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z" />
                            </svg>
                            Imprimir Tarjeta Kanban
                        </button>

                        <div class="bg-amber-500/5 border border-amber-500/20 p-4 rounded-xl text-xs space-y-1.5 text-amber-300">
                            <p class="font-bold flex items-center gap-1">
                                💡 Consejo de durabilidad de la tarjeta:
                            </p>
                            <p class="leading-relaxed opacity-80">
                                En el taller, las manos de los operarios suelen tener aceite, taladrina o virutas. Utiliza fundas de acrílico rígidas o plastifica cada tarjeta. Puedes colgar las tarjetas directamente del rack utilizando ganchos de alambre magnéticos o pinzas resistentes.
                            </p>
                        </div>
                    </div>

                </div>

            </div>

        </div>

    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-800/80 bg-slate-950 py-6 mt-12 text-center text-xs text-slate-500 no-print">
        <p>© 2026 Manual Visual de Taller. Diseñado para la conservación perfecta del metal.</p>
    </footer>

    <!-- JavaScript Engine -->
    <script>
        // Pages Management
        function goToPage(page) {
            const secBook = document.getElementById('section-book');
            const secGen = document.getElementById('section-generator');
            const btnBook = document.getElementById('btn-nav-book');
            const btnGen = document.getElementById('btn-nav-generator');

            if (page === 'book') {
                secBook.classList.remove('hidden');
                secGen.classList.add('hidden');
                btnBook.className = "px-4 py-1.5 rounded-full transition-all font-medium text-amber-400 bg-slate-800";
                btnGen.className = "px-4 py-1.5 rounded-full transition-all font-medium text-slate-400 hover:text-slate-100";
            } else {
                secBook.classList.add('hidden');
                secGen.classList.remove('hidden');
                btnBook.className = "px-4 py-1.5 rounded-full transition-all font-medium text-slate-400 hover:text-slate-100";
                btnGen.className = "px-4 py-1.5 rounded-full transition-all font-medium text-amber-400 bg-slate-800";
            }
        }

        // Chapters Data
        const chapters = [
            {
                num: 1,
                title: "El Enemigo Silencioso en el Taller",
                text: `
                    <div class="space-y-4">
                        <p class="text-slate-300 leading-relaxed text-lg">
                            En un taller metalmecánico, los materiales son dinero en estado físico. Sin embargo, suelen sufrir deterioros constantes antes de ser procesados debido a la falta de control visual.
                        </p>
                        <h4 class="text-sm font-bold text-amber-500 uppercase tracking-widest pt-2">¿Cómo se dañan tus materiales?</h4>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <div class="bg-slate-900 p-4 rounded-xl border border-slate-800/60">
                                <div class="text-2xl mb-1">💧</div>
                                <h5 class="font-bold text-sm text-slate-200">Oxidación Temprana</h5>
                                <p class="text-xs text-slate-400 mt-1">Planchas de hierro negro expuestas a humedad ambiental sin película protectora de aceite.</p>
                            </div>
                            <div class="bg-slate-900 p-4 rounded-xl border border-slate-800/60">
                                <div class="text-2xl mb-1">💥</div>
                                <h5 class="font-bold text-sm text-slate-200">Daño Mecánico</h5>
                                <p class="text-xs text-slate-400 mt-1">Rayaduras profundas en planchas pulidas o deformaciones en perfiles finos por apilamientos excesivos.</p>
                            </div>
                            <div class="bg-slate-900 p-4 rounded-xl border border-slate-800/60">
                                <div class="text-2xl mb-1">🔬</div>
                                <h5 class="font-bold text-sm text-slate-200">Corrosión Galvánica</h5>
                                <p class="text-xs text-slate-400 mt-1">Contacto directo y descuidado entre metales diferentes (como aluminio y acero) que acelera el desgaste químico.</p>
                            </div>
                        </div>
                        <p class="text-slate-400 text-sm italic">
                            El Kanban no es solo un indicador de cuándo comprar; es un escudo que restringe el inventario sobrante, manteniendo solo lo que puedes almacenar de forma segura.
                        </p>
                    </div>
                `
            },
            {
                num: 2,
                title: "El Kanban de Cuidado Limitador",
                text: `
                    <div class="space-y-4">
                        <p class="text-slate-300 leading-relaxed text-lg">
                            ¿Por qué tener exceso de materiales en el suelo si solo vas a procesar tres planchas hoy? El principio fundamental de Kanban es el <strong>WIP (Work In Progress / Trabajo en Proceso) limitado</strong>.
                        </p>
                        
                        <div class="bg-amber-500/5 border border-amber-500/20 p-5 rounded-xl space-y-3">
                            <h4 class="text-sm font-bold text-amber-500 flex items-center gap-2">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M11.3 1.046A1 1 0 0112 2v5h4a1 1 0 01.82 1.573l-7 10A1 1 0 018 18v-5H4a1 1 0 01-.82-1.573l7-10a1 1 0 011.12-.38z" clip-rule="evenodd" />
                                </svg>
                                Kanban Aplica la regla "PEPS" (FIFO):
                            </h4>
                            <p class="text-xs text-slate-300 leading-relaxed">
                                El primero en entrar al taller debe ser el primero en ser mecanizado. Si apilas material sin control visual, el metal del fondo (el más viejo) se oxidará sin que te des cuenta. Las tarjetas Kanban te obligan a organizar los lotes en forma de flujo continuo, garantizando que el material no envejezca ni se deteriore en la estantería.
                            </p>
                        </div>

                        <div class="space-y-2">
                            <h4 class="text-sm font-bold text-slate-200">Reglas Kanban en Metalmecánica:</h4>
                            <ul class="list-disc pl-5 text-xs text-slate-400 space-y-1.5">
                                <li><strong>Sin tarjeta no hay movimiento:</strong> Nadie retira una barra de acero de la estantería de almacenamiento sin extraer y depositar su tarjeta correspondiente.</li>
                                <li><strong>Límite físico estricto:</strong> Si la estantería indica un máximo de 5 espacios para perfiles pesados (para evitar dobleces), solo deben existir 5 tarjetas físicas Kanban para esa sección en circulación.</li>
                            </ul>
                        </div>
                    </div>
                `
            },
            {
                num: 3,
                title: "Diseño de una Tarjeta Antideterioro",
                text: `
                    <div class="space-y-4">
                        <p class="text-slate-300 leading-relaxed text-lg">
                            Una tarjeta de producción estándar solo muestra códigos y números. Una <strong>Tarjeta Kanban de Conservación</strong> para metalurgia añade instrucciones explícitas de preservación.
                        </p>
                        
                        <!-- Illustration of Card Areas -->
                        <div class="border border-slate-800 rounded-xl p-4 bg-slate-900/60 space-y-3">
                            <h4 class="text-xs font-bold text-slate-400 uppercase tracking-widest">Partes clave de la Tarjeta Kanban de Protección:</h4>
                            
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-xs">
                                <div class="flex items-start gap-2.5">
                                    <span class="p-1 bg-amber-500 text-slate-950 font-bold rounded text-[10px] w-5 h-5 flex items-center justify-center">1</span>
                                    <div>
                                        <p class="font-bold text-slate-200">Código de Color Visual</p>
                                        <p class="text-slate-400">Permite saber al instante si es acero dulce (propenso a óxido rápido), inoxidable o metales blandos.</p>
                                    </div>
                                </div>
                                <div class="flex items-start gap-2.5">
                                    <span class="p-1 bg-amber-500 text-slate-950 font-bold rounded text-[10px] w-5 h-5 flex items-center justify-center">2</span>
                                    <div>
                                        <p class="font-bold text-slate-200">Límite de Carga y Apilamiento</p>
                                        <p class="text-slate-400">Evita el colapso de estructuras metálicas o abolladuras por sobrepeso en planchas delgadas.</p>
                                    </div>
                                </div>
                                <div class="flex items-start gap-2.5">
                                    <span class="p-1 bg-amber-500 text-slate-950 font-bold rounded text-[10px] w-5 h-5 flex items-center justify-center">3</span>
                                    <div>
                                        <p class="font-bold text-slate-200">Checklist de Cuidado Químico</p>
                                        <p class="text-slate-400">Instrucciones básicas impresas en la tarjeta: "Aplicar capa protectora de aceite", "No apoyar sobre hormigón húmedo".</p>
                                    </div>
                                </div>
                                <div class="flex items-start gap-2.5">
                                    <span class="p-1 bg-amber-500 text-slate-950 font-bold rounded text-[10px] w-5 h-5 flex items-center justify-center">4</span>
                                    <div>
                                        <p class="font-bold text-slate-200">Punto de Pedido e Inventario Mínimo</p>
                                        <p class="text-slate-400">Te avisa cuándo contactar al proveedor antes de quedarte sin stock o acumular materiales de más.</p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <p class="text-slate-400 text-sm">
                            👉 Puedes crear y personalizar tu propia tarjeta usando nuestra pestaña <strong>"Generador de Tarjetas"</strong> arriba.
                        </p>
                    </div>
                `
            },
            {
                num: 4,
                title: "El Flujo del Taller en la Práctica",
                text: `
                    <div class="space-y-4">
                        <p class="text-slate-300 leading-relaxed text-lg">
                            Para evitar que el material sufra deterioros por manipulación innecesaria, el taller debe dividirse en zonas estrictas de flujo Kanban:
                        </p>
                        
                        <div class="relative pl-6 border-l-2 border-amber-500 space-y-5 text-sm">
                            <div class="relative">
                                <div class="absolute -left-[31px] top-1 w-4 h-4 rounded-full bg-amber-500 border-4 border-slate-950"></div>
                                <h4 class="font-bold text-slate-200">Paso A: Recepción del Material</h4>
                                <p class="text-xs text-slate-400">Se inspecciona la calidad. Si el material viene húmedo, se seca de inmediato. Se asocia un lote a su Tarjeta Kanban de Conservación física.</p>
                            </div>
                            <div class="relative">
                                <div class="absolute -left-[31px] top-1 w-4 h-4 rounded-full bg-amber-500 border-4 border-slate-950"></div>
                                <h4 class="font-bold text-slate-200">Paso B: Almacenamiento Protegido</h4>
                                <p class="text-xs text-slate-400">Se coloca en racks elevados con separadores de madera o goma para evitar rayaduras. La Tarjeta Kanban se cuelga en el exterior del rack.</p>
                            </div>
                            <div class="relative">
                                <div class="absolute -left-[31px] top-1 w-4 h-4 rounded-full bg-amber-500 border-4 border-slate-950"></div>
                                <h4 class="font-bold text-slate-200">Paso C: Disparador de Producción</h4>
                                <p class="text-xs text-slate-400">Cuando el área de corte/mecanizado toma el lote, retira la Tarjeta Kanban y la coloca en el casillero de "Re-pedido". Esto avisa automáticamente que se debe reponer ese lote de manera controlada.</p>
                            </div>
                        </div>

                        <div class="p-3 bg-blue-500/5 rounded-lg border border-blue-500/20 text-xs text-blue-300">
                            <strong>Nota de taller:</strong> Nunca dejes las planchas o barras directamente sobre el suelo de cemento. El cemento transmite humedad por capilaridad, lo que oxida los metales ferrosos en menos de 48 horas.
                        </div>
                    </div>
                `
            },
            {
                num: 5,
                title: "Plan de Implementación en 5 Pasos",
                text: `
                    <div class="space-y-4">
                        <p class="text-slate-300 leading-relaxed text-lg">
                            Implementar este sistema no requiere de software costoso. Puedes iniciar mañana mismo siguiendo estos 5 pasos prácticos de taller:
                        </p>

                        <div class="grid grid-cols-1 md:grid-cols-5 gap-3">
                            <div class="bg-slate-900 p-3 rounded border border-slate-800">
                                <span class="text-xl">🧹</span>
                                <p class="font-bold text-xs text-slate-200 mt-1">1. Limpieza total</p>
                                <p class="text-[10px] text-slate-400 mt-1">Libera racks y elimina metales ya oxidados o inutilizables.</p>
                            </div>
                            <div class="bg-slate-900 p-3 rounded border border-slate-800">
                                <span class="text-xl">🏷️</span>
                                <p class="font-bold text-xs text-slate-200 mt-1">2. Tarjetas</p>
                                <p class="text-[10px] text-slate-400 mt-1">Genera tus Tarjetas Kanban plastificadas para cada material.</p>
                            </div>
                            <div class="bg-slate-900 p-3 rounded border border-slate-800">
                                <span class="text-xl">📏</span>
                                <p class="font-bold text-xs text-slate-200 mt-1">3. Definir Límites</p>
                                <p class="text-[10px] text-slate-400 mt-1">Establece cuánto material máximo puede estar expuesto.</p>
                            </div>
                            <div class="bg-slate-900 p-3 rounded border border-slate-800">
                                <span class="text-xl">📢</span>
                                <p class="font-bold text-xs text-slate-200 mt-1">4. Inducción</p>
                                <p class="text-[10px] text-slate-400 mt-1">Explica a los operarios cómo mover el material con las tarjetas.</p>
                            </div>
                            <div class="bg-slate-900 p-3 rounded border border-slate-800">
                                <span class="text-xl">🕵️</span>
                                <p class="font-bold text-xs text-slate-200 mt-1">5. Auditoría</p>
                                <p class="text-[10px] text-slate-400 mt-1">Haz una revisión semanal de 10 minutos para verificar el flujo.</p>
                            </div>
                        </div>

                        <div class="bg-gradient-to-r from-amber-500/20 to-orange-500/20 p-5 rounded-xl text-center space-y-2 border border-amber-500/30">
                            <h4 class="font-bold text-amber-400 text-sm">¿Listo para crear tus primeras Tarjetas Kanban de taller?</h4>
                            <p class="text-xs text-slate-300">Ve a nuestra herramienta de generación para comenzar.</p>
                            <button onclick="goToPage('generator')" class="mt-2 px-4 py-2 bg-amber-500 text-slate-950 font-bold rounded-lg text-xs hover:bg-amber-600 transition">
                                Abrir Generador de Tarjetas
                            </button>
                        </div>
                    </div>
                `
            }
        ];

        let currentChapter = 1;

        function displayChapter(chapNum) {
            const chap = chapters.find(c => c.num === chapNum);
            if (!chap) return;

            const container = document.getElementById('chapter-content');
            container.innerHTML = `
                <div class="space-y-1">
                    <span class="text-xs font-bold text-amber-500 uppercase tracking-widest">Capítulo ${chap.num}</span>
                    <h3 class="serif-title text-2xl sm:text-3xl font-black text-slate-100">${chap.title}</h3>
                </div>
                <div class="prose prose-invert max-w-none">
                    ${chap.text}
                </div>
            `;

            // Update navigation indicator
            document.getElementById('chapter-indicator').innerText = `Capítulo ${chap.num} de ${chapters.length}`;

            // Handle button states
            const btnPrev = document.getElementById('btn-prev-chap');
            const btnNext = document.getElementById('btn-next-chap');

            btnPrev.disabled = chapNum === 1;
            
            if (chapNum === chapters.length) {
                btnNext.innerHTML = `
                    Ir al Generador
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                    </svg>
                `;
            } else {
                btnNext.innerHTML = `
                    Siguiente
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                    </svg>
                `;
            }

            // Highlight active chapter on list
            for (let i = 1; i <= chapters.length; i++) {
                const btn = document.getElementById(`btn-chap-${i}`);
                if (btn) {
                    if (i === chapNum) {
                        btn.className = "w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 bg-slate-800/80 text-amber-400 border-l-4 border-amber-500";
                    } else {
                        btn.className = "w-full text-left px-3 py-3 rounded-xl transition duration-150 flex items-center gap-3 text-slate-400 hover:bg-slate-800/40 hover:text-slate-200";
                    }
                }
            }
        }

        function changeChapter(num) {
            currentChapter = num;
            displayChapter(currentChapter);
            // Scroll to chapter area on mobile
            document.getElementById('chapter-content').scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }

        function navigateChapter(dir) {
            if (dir === 1 && currentChapter === chapters.length) {
                goToPage('generator');
                return;
            }
            const target = currentChapter + dir;
            if (target >= 1 && target <= chapters.length) {
                currentChapter = target;
                displayChapter(currentChapter);
            }
        }

        // Kanban Card Generator Engine
        let selectedColor = 'steel';

        function setCardColor(type) {
            selectedColor = type;
            const headerBar = document.getElementById('card-header-bar');
            const bSteel = document.getElementById('col-btn-steel');
            const bStainless = document.getElementById('col-btn-stainless');
            const bAluminum = document.getElementById('col-btn-aluminum');

            // Reset borders
            bSteel.className = "border border-slate-800 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2";
            bStainless.className = "border border-slate-800 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2";
            bAluminum.className = "border border-slate-800 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2";

            if (type === 'steel') {
                headerBar.className = "bg-amber-500 text-slate-950 p-4 transition-colors";
                bSteel.className = "border border-slate-700 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2 border-2 border-amber-500 ring-2 ring-amber-500/20";
            } else if (type === 'stainless') {
                headerBar.className = "bg-blue-500 text-slate-950 p-4 transition-colors";
                bStainless.className = "border border-slate-700 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2 border-2 border-blue-500 ring-2 ring-blue-500/20";
            } else if (type === 'aluminum') {
                headerBar.className = "bg-emerald-500 text-slate-950 p-4 transition-colors";
                bAluminum.className = "border border-slate-700 bg-slate-900 px-3 py-2 rounded-lg text-xs font-medium text-left flex items-center gap-2 border-2 border-emerald-500 ring-2 ring-emerald-500/20";
            }

            updateCardPreview();
        }

        function updateCardPreview() {
            // Get inputs
            const matName = document.getElementById('input-mat-name').value || "Nombre del Material";
            const matCode = document.getElementById('input-mat-code').value || "N/A";
            const maxStack = document.getElementById('input-max-stack').value || "Sin límites";
            const batchQty = document.getElementById('input-batch-qty').value || "N/A";
            const reorderPt = document.getElementById('input-reorder-point').value || "N/A";
            const notes = document.getElementById('input-instructions').value || "Ninguna nota de conservación especificada.";

            // Set targets
            document.getElementById('card-title').innerText = matName;
            document.getElementById('card-code').innerText = matCode;
            document.getElementById('card-stack').innerText = maxStack;
            document.getElementById('card-batch').innerText = batchQty;
            document.getElementById('card-reorder').innerText = reorderPt;
            document.getElementById('card-notes').innerText = notes;

            // Update preservation checks
            const checkOil = document.getElementById('check-oil').checked;
            const checkSeparator = document.getElementById('check-separator').checked;
            const checkLona = document.getElementById('check-lona').checked;

            const measuresContainer = document.getElementById('card-measures-container');
            measuresContainer.innerHTML = '';

            let hasMeasures = false;

            if (checkOil) {
                hasMeasures = true;
                measuresContainer.innerHTML += `
                    <div class="flex items-center gap-2 text-xs text-slate-300">
                        <span class="w-2 h-2 rounded-full bg-amber-500 shrink-0"></span>
                        <span>Reaplicar aceite protector anti-óxido al almacenar.</span>
                    </div>
                `;
            }

            if (checkSeparator) {
                hasMeasures = true;
                measuresContainer.innerHTML += `
                    <div class="flex items-center gap-2 text-xs text-slate-300">
                        <span class="w-2 h-2 rounded-full bg-amber-500 shrink-0"></span>
                        <span>Utilizar separadores de madera/goma entre capas.</span>
                    </div>
                `;
            }

            if (checkLona) {
                hasMeasures = true;
                measuresContainer.innerHTML += `
                    <div class="flex items-center gap-2 text-xs text-slate-300">
                        <span class="w-2 h-2 rounded-full bg-amber-500 shrink-0"></span>
                        <span>Mantener cubierto con lona impermeable.</span>
                    </div>
                `;
            }

            if (!hasMeasures) {
                measuresContainer.innerHTML = `
                    <p class="text-xs text-slate-500 italic">No se seleccionaron medidas adicionales de cuidado.</p>
                `;
            }
        }

        // Initialize application on window load
        window.onload = function() {
            displayChapter(1);
            updateCardPreview();
        }
    </script>
</body>
</html>
