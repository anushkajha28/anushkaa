# anushkaa
i am a beginner and eventually hoping to make new , big and innovative projects.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mood Lens | Sentiment Tracker</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; transition: background 0.5s ease; }
        .glass { background: rgba(255, 255, 255, 0.2); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.3); }
    </style>
</head>
<body class="bg-slate-50 flex items-center justify-center min-h-screen p-6" id="body-bg">

    <div class="max-w-md w-full glass p-8 rounded-3xl shadow-2xl bg-white/80">
        <header class="text-center mb-8">
            <h1 class="text-3xl font-semibold text-slate-800">Mood Lens</h1>
            <p class="text-slate-500">How are you feeling right now?</p>
        </header>

        <div class="relative mb-6">
            <textarea 
                id="text-input"
                class="w-full p-4 rounded-2xl border border-slate-200 focus:ring-4 focus:ring-blue-100 focus:border-blue-400 outline-none transition-all resize-none h-40 text-slate-700"
                placeholder="Type your thoughts here..."></textarea>
        </div>

        <div id="mood-display" class="text-center p-6 rounded-2xl bg-white shadow-sm border border-slate-100 hidden">
            <div id="mood-emoji" class="text-6xl mb-2 animate-bounce">😐</div>
            <div id="mood-label" class="text-xl font-bold uppercase tracking-widest text-slate-600">Neutral</div>
            <p id="mood-advice" class="text-sm text-slate-400 mt-2">I'm listening...</p>
        </div>
    </div>

    <script>
        const input = document.getElementById('text-input');
        const display = document.getElementById('mood-display');
        const emoji = document.getElementById('mood-emoji');
        const label = document.getElementById('mood-label');
        const advice = document.getElementById('mood-advice');
        const bg = document.getElementById('body-bg');

        const moodMap = {
            happy: { emoji: '✨', label: 'Positive', color: '#f0fdf4', text: 'Keep that energy going!', bg: 'bg-green-50' },
            sad: { emoji: '🌧️', label: 'Melancholy', color: '#eff6ff', text: 'It is okay to feel this way. Take a breath.', bg: 'bg-blue-50' },
            angry: { emoji: '🔥', label: 'Frustrated', color: '#fef2f2', text: 'Deep breaths. You have got this.', bg: 'bg-red-50' },
            neutral: { emoji: '☁️', label: 'Neutral', color: '#f8fafc', text: 'Steady and calm.', bg: 'bg-slate-50' }
        };

        input.addEventListener('input', (e) => {
            const val = e.target.value.toLowerCase();
            if (val.length === 0) {
                display.classList.add('hidden');
                bg.className = 'bg-slate-50 flex items-center justify-center min-h-screen p-6';
                return;
            }

            display.classList.remove('hidden');

            // Simple Sentiment Logic
            let mood = 'neutral';
            const positiveWords = ['good', 'great', 'happy', 'amazing', 'love', 'blessed', 'excited', 'best'];
            const negativeWords = ['bad', 'sad', 'hate', 'terrible', 'angry', 'upset', 'depressed', 'tired'];
            const
