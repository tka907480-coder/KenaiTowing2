
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Kenai Towing & Recovery | 24/7 Peninsula Dispatch</title>
    <meta name="description" content="Fast, reliable towing and roadside assistance in Kenai, Soldotna, and the entire Peninsula. Request dispatch via text or call 907-252-6044.">
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #f3f4f6; -webkit-tap-highlight-color: transparent; }
        .kenai-blue { background-color: #0c2340; }
        .kenai-gold { color: #f2a900; }
        .kenai-gold-bg { background-color: #f2a900; }
        .scrollbar-hide::-webkit-scrollbar { display: none; }
        .glass-effect { background: rgba(255, 255, 255, 0.9); backdrop-filter: blur(10px); }
        
        @keyframes slideUp {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        .animate-slide-up { animation: slideUp 0.4s ease-out forwards; }
        
        .service-btn.active {
            border-color: #f2a900;
            background-color: #fffbeb;
            transform: scale(0.98);
        }
        .service-btn.active-cash {
            border-color: #059669;
            background-color: #ecfdf5;
            transform: scale(0.98);
        }
    </style>
</head>
<body class="bg-gray-100 min-h-screen pb-24">

    <header class="kenai-blue text-white p-4 sticky top-0 z-50 shadow-lg border-b-4 border-[#f2a900]">
        <div class="max-w-4xl mx-auto flex justify-between items-center">
            <div class="flex items-center gap-3">
                <div class="bg-white p-1 rounded-lg">
                    <i class="fas fa-truck-pickup text-[#0c2340] text-xl"></i>
                </div>
                <div>
                    <h1 class="font-extrabold text-lg leading-tight tracking-tight uppercase">Kenai Towing</h1>
                    <div class="flex items-center gap-1">
                        <span class="inline-block w-2 h-2 bg-green-400 rounded-full animate-pulse"></span>
                        <p class="text-[10px] uppercase tracking-widest text-[#f2a900] font-bold">Live Dispatch Active</p>
                    </div>
                </div>
            </div>
            <div class="text-right">
                <a href="tel:9072526044" class="bg-red-600 hover:bg-red-700 px-4 py-2 rounded-xl font-bold text-sm transition-all flex items-center gap-2 shadow-inner">
                    <i class="fas fa-phone-alt animate-bounce"></i> 907-252-6044
                </a>
            </div>
        </div>
    </header>

    <main class="max-w-2xl mx-auto p-4 space-y-6">
        <div class="grid grid-cols-2 gap-3">
            <button onclick="setService('Standard Towing')" id="btn-standard" class="service-btn bg-white p-4 rounded-2xl border-2 border-[#f2a900] bg-yellow-50 shadow-sm transition-all text-center flex flex-col items-center justify-center">
                <i class="fas fa-trailer text-2xl text-blue-900 mb-2"></i>
                <p class="text-[11px] font-bold uppercase text-blue-900">Standard</p>
            </button>
            <button onclick="setService('Roadside')" id="btn-roadside" class="service-btn bg-white p-4 rounded-2xl border-2 border-transparent shadow-sm transition-all text-center flex flex-col items-center justify-center">
                <i class="fas fa-tools text-2xl text-blue-900 mb-2"></i>
                <p class="text-[11px] font-bold uppercase text-blue-900">Roadside</p>
            </button>
            <button onclick="setService('Recovery')" id="btn-recovery" class="service-btn bg-white p-4 rounded-2xl border-2 border-transparent shadow-sm transition-all text-center flex flex-col items-center justify-center">
                <i class="fas fa-mountain text-2xl text-blue-900 mb-2"></i>
                <p class="text-[11px] font-bold uppercase text-blue-900">Recovery</p>
            </button>
            <button onclick="setService('Cash Discount')" id="btn-cash" class="service-btn bg-white p-4 rounded-2xl border-2 border-transparent shadow-sm transition-all text-center flex flex-col items-center justify-center border-dashed border-green-500 bg-green-50">
                <i class="fas fa-hand-holding-usd text-2xl text-green-700 mb-2"></i>
                <p class="text-[11px] font-bold uppercase text-green-700">Cash Discount!</p>
            </button>
        </div>

        <div id="serviceInfoCard" class="bg-blue-50 border-l-4 border-blue-900 p-4 rounded-xl animate-slide-up">
            <div class="flex gap-3">
                <i class="fas fa-info-circle text-blue-900 mt-1"></i>
                <div>
                    <h4 id="serviceTitle" class="text-xs font-bold text-blue-900 uppercase">Standard Towing</h4>
                    <p id="serviceDesc" class="text-[11px] text-blue-800 leading-tight mt-1">Best for mechanical breakdowns or engine failure. We utilize professional rollback flatbeds to ensure the safest transport for your vehicle to any repair shop or residence.</p>
                </div>
            </div>
        </div>

        <div id="dispatchForm" class="bg-white rounded-3xl shadow-xl overflow-hidden border border-gray-200 animate-slide-up">
            <div class="p-6 space-y-5">
                <div class="flex justify-between items-center border-b pb-3 border-gray-100">
                    <h3 class="font-black text-blue-900 uppercase tracking-tight text-sm flex items-center gap-2">
                        <i class="fas fa-clipboard-list text-[#f2a900]"></i> Dispatch Details
                    </h3>
                    <span class="text-[10px] font-bold text-green-600 uppercase bg-green-50 px-2 py-1 rounded">24/7 Monitoring</span>
                </div>
                
                <div class="space-y-4">
                    <div>
                        <label class="block text-[10px] font-bold text-gray-500 uppercase ml-1 mb-1">Pickup Location</label>
                        <input type="text" id="pickup" placeholder="e.g. Soldotna Fred Meyer / MM 92" class="w-full p-4 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#f2a900] outline-none transition-all">
                        <div class="flex gap-2 mt-2 overflow-x-auto pb-2 scrollbar-hide">
                            <button onclick="setPickup('Soldotna Fred Meyer')" class="whitespace-nowrap px-3 py-1.5 bg-gray-200 rounded-lg text-[10px] font-bold hover:bg-blue-900 hover:text-white transition-colors">Fred Meyer</button>
                            <button onclick="setPickup('K-Beach Rd')" class="whitespace-nowrap px-3 py-1.5 bg-gray-200 rounded-lg text-[10px] font-bold hover:bg-blue-900 hover:text-white transition-colors">K-Beach</button>
                            <button onclick="setPickup('Sterling Hwy MM 85')" class="whitespace-nowrap px-3 py-1.5 bg-gray-200 rounded-lg text-[10px] font-bold hover:bg-blue-900 hover:text-white transition-colors">MM 85</button>
                        </div>
                    </div>

                    <div>
                        <label class="block text-[10px] font-bold text-gray-500 uppercase ml-1 mb-1">Drop-off Destination</label>
                        <input type="text" id="dropoff" placeholder="e.g. Ellis Auto / Residence" class="w-full p-4 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#f2a900] outline-none transition-all">
                    </div>

                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-[10px] font-bold text-gray-500 uppercase ml-1 mb-1">Vehicle Info</label>
                            <input type="text" id="vehicleDetails" placeholder="White Ford F-150" class="w-full p-4 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#f2a900] outline-none">
                        </div>
                        <div>
                            <label class="block text-[10px] font-bold text-gray-500 uppercase ml-1 mb-1">Selected Service</label>
                            <input type="text" id="serviceType" readonly value="Standard Towing" class="w-full p-4 bg-gray-100 border border-gray-200 rounded-2xl font-bold text-blue-900 text-sm">
                        </div>
                    </div>

                    <div>
                        <label class="block text-[10px] font-bold text-gray-500 uppercase ml-1 mb-1">Notes / Special Instructions</label>
                        <textarea id="extraDetails" rows="3" placeholder="e.g. Stuck in ditch, keys are in gas cap..." class="w-full p-4 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#f2a900] outline-none resize-none"></textarea>
                    </div>
                </div>

                <div class="pt-2">
                    <button onclick="submitRequest()" class="w-full kenai-gold-bg hover:bg-yellow-500 text-blue-900 font-extrabold py-5 rounded-2xl shadow-xl transform active:scale-[0.98] transition-all flex justify-center items-center gap-3 uppercase tracking-tight">
                        <i class="fas fa-paper-plane"></i> Send to Dispatch via Text
                    </button>
                    <p class="text-center text-[10px] text-gray-400 mt-4 font-medium italic">
                        Clicking above will pre-fill a text message to our dispatch line at 907-252-6044.
                    </p>
                </div>
            </div>
        </div>
    </main>

    <div id="aiAssistant" class="fixed bottom-6 right-6 z-[200]">
        <div id="chatWindow" class="hidden absolute bottom-20 right-0 w-80 bg-white rounded-3xl shadow-2xl border border-gray-200 overflow-hidden flex flex-col glass-effect">
            <div class="kenai-blue p-4 text-white flex justify-between items-center">
                <div class="flex items-center gap-2">
                    <div class="w-2.5 h-2.5 bg-green-400 rounded-full animate-pulse shadow-[0_0_8px_rgba(74,222,128,0.8)]"></div>
                    <span class="font-bold text-xs">Peninsula Roadside AI</span>
                </div>
                <button onclick="toggleChat()"><i class="fas fa-times"></i></button>
            </div>
            <div id="chatMessages" class="h-80 overflow-y-auto p-4 space-y-3 text-[11px] leading-relaxed">
                <div class="bg-gray-100 p-3 rounded-2xl rounded-tl-none mr-8 text-gray-700">
                    Hi! I'm the Kenai Towing AI. Need to know about mile markers, road conditions, or estimated local costs?
                </div>
            </div>
            <div class="p-3 border-t flex gap-2 bg-gray-50">
                <input type="text" id="chatInput" placeholder="Ask a question..." class="flex-1 bg-white border border-gray-200 p-3 rounded-xl text-xs outline-none" onkeypress="if(event.key === 'Enter') sendChatMessage()">
                <button onclick="sendChatMessage()" class="bg-blue-900 text-white w-10 h-10 rounded-xl flex items-center justify-center shadow-lg"><i class="fas fa-paper-plane"></i></button>
            </div>
        </div>
        <button onclick="toggleChat()" class="w-16 h-16 kenai-blue text-white rounded-full shadow-2xl flex items-center justify-center hover:scale-110 active:scale-95 transition-all group">
            <i class="fas fa-robot text-2xl group-hover:rotate-12 transition-transform"></i>
        </button>
    </div>

    <script>
        const serviceData = {
            'Standard Towing': "Best for mechanical breakdowns or engine failure. We utilize professional rollback flatbeds to ensure the safest transport for your vehicle to any repair shop or residence.",
            'Roadside': "For minor emergencies: Jumpstarts, lockouts, tire changes, or fuel delivery. Select this if your vehicle is on solid ground and just needs a quick fix.",
            'Recovery': "Select this if you are stuck in a ditch, snow, mud, or off-road. We use specialized winches and gear to safely extract your vehicle without damage.",
            'Cash Discount': "No insurance? No problem. We support our Peninsula neighbors with competitive private-pay rates. We are always happy to work with you on a reasonable basis to get you home safely."
        };

        function setService(type) {
            document.getElementById('serviceType').value = type;
            document.getElementById('serviceTitle').innerText = type === 'Cash Discount' ? 'Private Pay Savings' : type;
            document.getElementById('serviceDesc').innerText = serviceData[type];

            const btns = document.querySelectorAll('.service-btn');
            btns.forEach(b => {
                b.classList.remove('border-[#f2a900]', 'bg-yellow-50', 'border-green-600', 'bg-green-100');
                b.classList.add('border-transparent', 'bg-white');
            });
            
            const selectedBtnId = 'btn-' + type.toLowerCase().split(' ')[0];
            const activeBtn = document.getElementById(selectedBtnId);
            if(activeBtn) {
                if(type === 'Cash Discount') {
                    activeBtn.classList.add('border-green-600', 'bg-green-100');
                } else {
                    activeBtn.classList.add('border-[#f2a900]', 'bg-yellow-50');
                }
                activeBtn.classList.remove('border-transparent', 'bg-white');
            }
        }

        function setPickup(location) {
            document.getElementById('pickup').value = location;
        }

        function submitRequest() {
            const pickup = document.getElementById('pickup').value.trim();
            const dropoff = document.getElementById('dropoff').value.trim();
            const service = document.getElementById('serviceType').value;
            const vehicle = document.getElementById('vehicleDetails').value.trim();
            const extra = document.getElementById('extraDetails').value.trim();

            if (!pickup || !vehicle || !dropoff) {
                showToast("Missing Required Details", "red");
                return;
            }

            const dispatchNumber = "9072526044";
            const messageBody = `KENAI TOWING REQ:\nSERVICE: ${service}\nVEHICLE: ${vehicle}\nPICKUP: ${pickup}\nDROPOFF: ${dropoff}\nNOTES: ${extra || 'None'}`;
            const smsUrl = `sms:${dispatchNumber}?body=${encodeURIComponent(messageBody)}`;
            
            window.location.href = smsUrl;
        }

        function showToast(text, color) {
            const msg = document.createElement('div');
            msg.className = `fixed top-24 left-1/2 -translate-x-1/2 bg-${color}-600 text-white px-8 py-4 rounded-2xl font-bold shadow-2xl z-[400] animate-bounce text-xs border-2 border-white/20`;
            msg.innerHTML = `<i class="fas fa-exclamation-triangle mr-2"></i> ${text}`;
            document.body.appendChild(msg);
            setTimeout(() => msg.remove(), 3000);
        }

        function toggleChat() {
            document.getElementById('chatWindow').classList.toggle('hidden');
        }

        function sendChatMessage() {
            const input = document.getElementById('chatInput');
            const msg = input.value.trim();
            if(!msg) return;

            addMessage(msg, 'user');
            input.value = '';

            setTimeout(() => {
                let response = "I'm checking driver logs. For Soldotna/Kenai calls, we're usually on-site within 30-45 minutes. Contact dispatch at 907-252-6044 for a precise window.";
                const lower = msg.toLowerCase();
                if(lower.includes('price') || lower.includes('cost')) response = "Towing base rates for local Peninsula jumps/tows start around $85-100 plus mileage. Ask dispatch for a firm quote!";
                if(lower.includes('road')) response = "Watch for black ice on K-Beach and the Sterling Highway. Stay in your vehicle if you're stuck!";
                
                addMessage(response, 'bot');
            }, 800);
        }

        function addMessage(text, sender) {
            const container = document.getElementById('chatMessages');
            const div = document.createElement('div');
            div.className = sender === 'user' 
                ? 'bg-blue-900 text-white p-3 rounded-2xl rounded-tr-none ml-8 shadow-sm mb-2' 
                : 'bg-gray-100 p-3 rounded-2xl rounded-tl-none mr-8 text-gray-700 shadow-sm border border-gray-200 mb-2';
            div.textContent = text;
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
        }
    </script>
</body>
</html>

```