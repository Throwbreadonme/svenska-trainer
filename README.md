# svenska-trainer
A browser-based Swedish vocabulary trainer built from the Kelly Corpus, a frequency-ranked, CEFR-tagged word list. Covers A1 and A2 vocabulary with spaced repetition, three exercise modes, and Swedish audio pronunciation via the browser's speech synthesis API.
Svenska — A Swedish Vocabulary Trainer
A browser-based Swedish vocabulary trainer built from the Kelly Corpus, a frequency-ranked, CEFR-tagged word list. Covers A1 and A2 vocabulary with spaced repetition, three exercise modes, and Swedish audio pronunciation via the browser's speech synthesis API.

Try it live: helena.cool/svenska.html


Why I built this
I am learning Swedish and could not find a tool that taught words in the right order. Most apps either ignore frequency data entirely or bury it under gamification. I wanted something that started with the words that actually matter (the ones you will hear and use first) and drilled them until they stuck.

So I built one.

The Kelly Corpus gives each word a frequency rank and a CEFR level. That is the foundation: start with A1, learn the highest-frequency words first, unlock A2 once you have covered 80% of A1. The spaced repetition algorithm (SM-2) handles the scheduling: words you know well come back less often, words you struggle with come back sooner.

I wrote about the whole process, including the product decisions behind it, at helena.cool/svenska_post.html.


Features
A1 + A2 vocabulary — 97 A1 words and 300+ A2 words sourced from the Kelly Corpus
Curated decks — Top 20, Verbs, Nouns, Numbers, Days & Time, Adjectives, or full level decks
SM-2 spaced repetition — classic algorithm scheduling reviews based on recall quality
Three exercise modes:
Flashcard — see the Swedish word, reveal the English meaning
Multiple choice — pick the correct translation from four options
Typing — type the answer from memory (harder, rewarded accordingly in SM-2)
Swedish audio — pronunciation via the browser's speechSynthesis API, no external dependency
Progress tracking — words learned, due today, retention stats per deck
Level unlocking — A2 unlocks after 80% of A1 is learned (or can be force-unlocked)
Persistent progress — state saved to localStorage, picks up where you left off
Zero dependencies — one HTML file, no build step, no server required


How to use it
Download svenska.html and open it in any modern browser. That is it.

# Or serve it locally if you prefer

python3 -m http.server 8000

# then open http://localhost:8000/svenska.html

No npm, no build step, no API keys. It runs entirely in the browser.


Technical decisions
Why a single HTML file? I wanted something I could host anywhere, share as a single link, and open on any device without setup. React and Tailwind are loaded from CDN. Everything else, vocabulary data, SM-2 logic, UI, lives in the file itself.

Why SM-2? It is the most widely validated spaced repetition algorithm and the one most language learning research is built on. Simple enough to implement clearly, effective enough to actually work.

Why the Kelly Corpus? Frequency-ranked and CEFR-tagged, which means I can teach words in the order that maximises usefulness. Most vocabulary lists are alphabetical or thematic. The Kelly Corpus is ordered by how often you will actually encounter each word.

Why 80% A1 before unlocking A2? Arbitrary but deliberate. You need a solid A1 foundation before A2 words are useful, but 100% felt punishing and 50% felt too easy. 80% means you have covered the core before moving on.


Data
Vocabulary data is embedded directly in the file. Words include:

Swedish term and English translation
Part of speech
CEFR level (A1 or A2)
Synonyms where relevant
A static example sentence in Swedish with English translation


Built with
React (via CDN, no build step)
Tailwind CSS (via CDN)
Browser speechSynthesis API for audio
localStorage for progress persistence
Kelly Corpus for vocabulary data


About
Built by Elena Martín Hernández — A curious PM who loves building and sharing things to make people’s life better.
