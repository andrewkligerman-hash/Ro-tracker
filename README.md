<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vehicle Repair Management - RO-Tracker Pro</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons CDN -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        .sidebar-icon { @apply p-3 rounded-xl text-slate-400 hover:text-blue-600 hover:bg-blue-50 transition cursor-pointer flex items-center justify-center; }
        .sidebar-active { @apply text-blue-600 bg-blue-50 font-semibold; }
        .card-box { @apply bg-white border border-slate-200 rounded-2xl p-5 shadow-sm hover:shadow-md transition; }
        .badge-progress { @apply bg-blue-100 text-blue-700 text-xs font-semibold px-2.5 py-0.5 rounded-full uppercase tracking-wider; }
        .badge-pending { @apply bg-amber-100 text-amber-700 text-xs font-semibold px-2.5 py-0.5 rounded-full uppercase tracking-wider; }
        .badge-complete { @apply bg-emerald-100 text-emerald-700 text-xs font-semibold px-2.5 py-0.5 rounded-full uppercase tracking-wider; }
    </style>
</head>
<body class="bg-slate-100 text-slate-800 font-sans min-h-screen flex">

    <!-- Left Icon Sidebar -->
    <aside class="w-20 bg-white border-r border-slate-200 flex flex-col items-center py-6 justify-between shrink-0">
        <div class="flex flex-col items-center gap-6 w-full px-3">
            <div class="text-blue-600 text-2xl font-black mb-4">
                <i class="fa-solid fa-screwdriver-wrench"></i>
            </div>
            <nav class="flex flex-col gap-2 w-full">
                <div class="sidebar-icon sidebar-active" title="Dashboard">
                    <i class="fa-solid fa-house text-lg"></i>
                </div>
                <div class="sidebar-icon" title="Job Cards">
                    <i class="fa-solid fa-rectangle-list text-lg"></i>
                </div>
                <div class="sidebar-icon" title="Customers">
                    <i class="fa-solid fa-users text-lg"></i>
                </div>
                <div class="sidebar-icon" title="Vehicles">
                    <i class="fa-solid fa-car text-lg"></i>
                </div>
                <div class="sidebar-icon" title="Spare Parts">
                    <i class="fa-solid fa-boxes-stacked text-lg"></i>
                </div>
                <div class="sidebar-icon" title="Billing">
                    <i class="fa-solid fa-file-invoice-dollar text-lg"></i>
                </div>
            </nav>
        </div>
        <div class="flex flex-col gap-4">
            <div class="sidebar-icon" title="Settings">
                <i class="fa-solid fa-gear text-lg"></i>
            </div>
        </div>
    </aside>

    <!-- Main Workspace -->
    <div class="flex-grow flex flex-col min-w-0">
        
        <!-- Header -->
        <header class="bg-white border-b border-slate-200 px-8 py-4 flex justify-between items-center">
            <div class="flex items-center gap-4">
                <h1 class="text-xl font-bold text-slate-900">Vehicle Repair Management</h1>
            </div>

            <div class="flex items-center gap-6">
                <!-- Search -->
                <div class="relative">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                    <input type="text" placeholder="Search RO#, VIN, Customer..." class="bg-slate-50 border border-slate-200 rounded-xl pl-10 pr-4 py-2 text-sm w-64 focus:outline-none focus:border-blue-500">
                </div>
                
                <!-- Profile -->
                <div class="flex items-center gap-3 border-l border-slate-200 pl-6">
                    <div class="w-9 h-9 rounded-full bg-blue-600 text-white font-bold flex items-center justify-center text-sm">
                        RC
                    </div>
                    <div class="hidden sm:block">
                        <div class="text-xs font-bold text-slate-900 leading-tight">Robert C.</div>
                        <div class="text-[10px] text-slate-500">Service Advisor</div>
                    </div>
                </div>
            </div>
        </header>

        <!-- Dynamic Content Body -->
        <main class="p-8 overflow-y-auto space-y-6 flex-grow">

            <!-- MULTI-COLUMN WORKBOARD GRID -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                
                <!-- COLUMN 1: Job Cards -->
                <div class="card-box space-y-4">
                    <div class="flex justify-between items-center">
                        <h2 class="font-bold text-slate-900 flex items-center gap-2">
                            Job Cards <span class="bg-blue-50 text-blue-600 text-xs px-2 py-0.5 rounded-full font-bold">325</span>
                        </h2>
                        <span class="text-xs text-blue-600 hover:underline cursor-pointer font-medium">View All &gt;</span>
                    </div>

                    <div class="space-y-3">
                        <!-- Active Stress Test RO Card -->
                        <div onclick="openROModal()" class="p-3 border border-blue-200 bg-blue-50/40 rounded-xl hover:border-blue-400 cursor-pointer transition">
                            <div class="flex justify-between items-start mb-1">
                                <span class="text-xs font-bold text-blue-700">#RO-99882</span>
                                <span class="badge-progress">IN PROGRESS</span>
                            </div>
                            <div class="text-sm font-bold text-slate-900">Robert "Bob" Callahan</div>
                            <div class="text-xs text-slate-500 mb-2">2018 Ford F-150 SuperCrew</div>
                            <div class="text-[11px] text-slate-600 bg-white p-2 rounded-lg border border-slate-200">
                                <strong>Lines:</strong> Brakes (Overlap DETECTED), Suspension, DTC P0299
                            </div>
                        </div>

                        <!-- Sample RO 2 -->
                        <div class="p-3 border border-slate-100 rounded-xl hover:border-slate-300 cursor-pointer transition">
                            <div class="flex justify-between items-start mb-1">
                                <span class="text-xs font-bold text-slate-600">#RO-4588</span>
                                <span class="badge-pending">PENDING AUTH</span>
                            </div>
                            <div class="text-sm font-bold text-slate-900">Emily Richards</div>
                            <div class="text-xs text-slate-500">2021 BMW X5 xDrive40i</div>
                        </div>
                    </div>

                    <!-- Customers Section nested in Column 1 -->
                    <div class="pt-4 border-t border-slate-100 space-y-3">
                        <div class="flex justify-between items-center">
                            <h2 class="font-bold text-slate-900 flex items-center gap-2">
                                Customers <span class="bg-slate-100 text-slate-600 text-xs px-2 py-0.5 rounded-full font-bold">1,250</span>
                            </h2>
                        </div>
                        <div class="space-y-2">
                            <div class="flex items-center justify-between p-2 rounded-xl hover:bg-slate-50">
                                <div class="flex items-center gap-2">
                                    <div class="w-7 h-7 rounded-full bg-slate-200 text-slate-700 text-[10px] font-bold flex items-center justify-center">BC</div>
                                    <div>
                                        <div class="text-xs font-bold text-slate-900">Bob Callahan</div>
                                        <div class="text-[9px] text-slate-500">+1 555-019-2831</div>
                                    </div>
                                </div>
                                <span class="badge-progress">Active</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- COLUMN 2: Spare Parts & Billing -->
                <div class="card-box space-y-4">
                    <div class="flex justify-between items-center">
                        <h2 class="font-bold text-slate-900 flex items-center gap-2">
                            Spare Parts <span class="bg-slate-100 text-slate-600 text-xs px-2 py-0.5 rounded-full font-bold">342</span>
                        </h2>
                        <span class="text-xs text-blue-600 hover:underline cursor-pointer font-medium">+ Add Part</span>
                    </div>

                    <div class="space-y-2 text-xs">
                        <div class="flex justify-between items-center p-2 border-b border-slate-100">
                            <span class="font-medium text-slate-700">OEM Motorcraft Front Pads</span>
                            <span class="font-bold text-emerald-600">In Stock ($89.50)</span>
                        </div>
                        <div class="flex justify-between items-center p-2 border-b border-slate-100">
                            <span class="font-medium text-slate-700">Motorcraft Rotors (Pair)</span>
                            <span class="font-bold text-emerald-600">In Stock ($198.00)</span>
                        </div>
                        <div class="flex justify-between items-center p-2 border-b border-slate-100">
                            <span class="font-medium text-slate-700">Lower Control Arm (F-150)</span>
                            <span class="font-bold text-amber-600">Fitment Verified ($210.00)</span>
                        </div>
                    </div>

                    <!-- Billing Version History Section -->
                    <div class="pt-4 border-t border-slate-100 space-y-3">
                        <div class="flex justify-between items-center">
                            <h2 class="font-bold text-slate-900 flex items-center gap-2">
                                Billing Version History <span class="bg-purple-100 text-purple-700 text-xs px-2 py-0.5 rounded-full font-bold">RO-99882</span>
                            </h2>
                        </div>
                        <div class="space-y-2 text-xs">
                            <div class="p-2.5 bg-slate-50 border border-slate-200 rounded-xl">
                                <div class="flex justify-between font-bold text-slate-900">
                                    <span>Quote v1 (Full)</span>
                                    <span class="text-slate-600">$1,274.65</span>
                                </div>
                            </div>
                            <div class="p-2.5 bg-emerald-50 border border-emerald-200 rounded-xl">
                                <div class="flex justify-between font-bold text-emerald-900">
                                    <span>Quote v2 (Approved)</span>
                                    <span class="text-emerald-700">$590.72</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- COLUMN 3: Vehicles & Technicians -->
                <div class="card-box space-y-4">
                    <div class="flex justify-between items-center">
                        <h2 class="font-bold text-slate-900 flex items-center gap-2">
                            Vehicles <span class="bg-slate-100 text-slate-600 text-xs px-2 py-0.5 rounded-full font-bold">820</span>
                        </h2>
                        <button class="bg-blue-600 text-white text-[10px] font-semibold px-2.5 py-1 rounded-lg hover:bg-blue-700">+ Add Vehicle</button>
                    </div>

                    <div class="space-y-2">
                        <div class="p-2.5 bg-slate-50 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-center mb-1">
                                <span class="text-xs font-bold text-slate-900">Ford F-150 SuperCrew</span>
                                <span class="text-[9px] font-mono bg-blue-100 text-blue-700 px-1.5 py-0.5 rounded">2018</span>
                            </div>
                            <div class="text-[9px] text-slate-500 font-mono">VIN: 1FTFW1E84KFA99882</div>
                        </div>
                    </div>

                    <!-- Technicians Section -->
                    <div class="pt-4 border-t border-slate-100 space-y-3">
                        <div class="flex justify-between items-center">
                            <h2 class="font-bold text-slate-900 flex items-center gap-2">
                                Technicians <span class="bg-slate-100 text-slate-600 text-xs px-2 py-0.5 rounded-full font-bold">12</span>
                            </h2>
                        </div>
                        <div class="space-y-2 text-xs">
                            <div class="flex justify-between items-center p-2 bg-slate-50 rounded-xl">
                                <div class="flex items-center gap-2">
                                    <div class="w-6 h-6 rounded-full bg-blue-600 text-white font-bold flex items-center justify-center text-[9px]">DM</div>
                                    <span class="font-bold text-slate-900">Dave M.</span>
                                </div>
                                <span class="text-slate-500 text-[10px]">RO-99882 (2.3 Hrs)</span>
                            </div>
                        </div>
                    </div>
                </div>

            </div>

        </main>
    </div>

    <!-- MODAL: Stress Test RO Inspector -->
    <div id="roModal" class="fixed inset-0 bg-slate-900/60 backdrop-blur

