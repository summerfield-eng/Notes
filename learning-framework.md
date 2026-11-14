THE LOOP — your 6-step framework  
Use this for any topic: a JS concept, a Hack file, a wiki SOP, a system design.

## 1️⃣ PREVIEW before you ask anything 👀

**Skim the material yourself.** Write down 2–3 questions you expect it to answer.  
🤔 **Why first:** if you let AI generate the questions, you've skipped deciding what's confusing — and that decision is most of the learning.  
⚠️ **(Stanford flags exactly this:** AI-generated previews can remove your chance to engage with the text.)

## 2️⃣ PREDICT before you're told 🔮

**Guess the answer.** Out loud or in writing. Commit to it.

> "I think .then attaches the callback when the data arrives."  
> "I think concat mutates the array."  
> "I think arrays are mutable so ignoring the return is fine."

💡 **Every one of those was wrong — and every one taught you more than a correct guess would.** A wrong prediction creates a gap you can feel. Reading the right answer first never does.  
🧠 This is the single highest-leverage habit you already have. Keep it.

## 3️⃣ PRODUCE in your own words ✍️

**Write the explanation before asking for a correct one.**
Your event loop note is the model: six sections, drafted by you, corrected iteratively.

> Draft → get it checked → fix → re-check → fix

📈 Your own trajectory: 2 conceptual errors → 1 → 0. That's what understanding being built looks like. You cannot get that from reading a good explanation.

## 4️⃣ PROVE it with evidence 🔬

**Don't accept an explanation — test it.**

```JavaScript
console.log("A");
setTimeout(() => console.log("B"), 0);
console.log("C");
// → A C B   ✅ settled, permanently
```

🎯 You did this to resolve a tutorial-vs-rule conflict, and pwd to settle ~ vs root. The console is a laboratory and it never hallucinates. Prefer an experiment over any authority — including me. ⚠️ (**Stanford's warning is real:** AI produces plausible-sounding wrong answers, misattributes sources, and invents citations. Verification isn't optional.)

## 5️⃣ PROBE for the hidden axis 🧭

**When something feels contradictory, or each fix breaks something else, ask:**

> "Am I treating two separate questions as one?"

🧪 _The independence test:_
can I have one without the other, both directions? If yes → two axes → draw the grid → check every cell.

- "Is it a Web API?" vs "Is it async?"
- "Is the TYPE mutable?" vs "Does the METHOD mutate?"
- "Value or address?" vs "Stack or heap?"
- "Link or text?" vs "Image or not?"
- "primitive vs object" vs "stack vs heap" ← you caught this one yourself 🏆

📏 This is your specific failure mode. Checking for it takes 10 seconds and has been the answer five times.

## 6️⃣ PERSIST with spaced review 📅

Revisit on a widening schedule: next day → 3 days → 1 week → 1 month.  
🤔 Your own data makes the case: after a break you scored 9/10 on HTML and command line, but 3/10 on code-design concepts — and the difference was which ones you'd actively reused.  
Review isn't rereading; it's self-quizzing from memory, then checking.
