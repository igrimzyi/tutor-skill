# tutor-skill

A Claude skill that tutors you in any subject by guiding you to the answer instead of giving it away. Type `/tutor` and start learning.

---

## Getting started

### 1. Install the skill

Pick the version of Claude you use.

<details open>
<summary><b>Claude app (claude.ai, desktop, mobile)</b></summary>

1. Download this repo: click the green **Code** button above, then **Download ZIP**, and unzip it.
2. Inside, find the **`tutor`** folder. Zip just that folder so you get `tutor.zip`.
   - **Mac:** right-click the `tutor` folder → **Compress "tutor"**
   - **Windows:** right-click the `tutor` folder → **Send to** → **Compressed (zipped) folder**
3. In Claude, go to **Customize → Skills**.
4. Click **+**, then **+ Create skill**, then **Upload a skill**.
5. Upload `tutor.zip`.
6. Make sure the **tutor** skill is toggled on.

> **Note:** Skills need **Code execution and file creation** turned on in your settings. The zip must contain the `tutor` folder itself (with `SKILL.md` inside it), and the folder name must stay `tutor`.

</details>

<details>
<summary><b>Claude Code</b></summary>

Clone the repo and copy the skill into your personal skills folder:

```bash
git clone https://github.com/igrimzyi/tutor-skill.git
mkdir -p ~/.claude/skills
cp -r tutor-skill/tutor ~/.claude/skills/
```

Restart Claude Code. Run `/skills` to confirm `tutor` is listed.

If you already installed the skill in the Claude app, it can sync to Claude Code automatically when you sign in with the same account.

</details>

### 2. Start a session

Type `/tutor` in a new chat. You can add a topic or a problem:

```
/tutor
/tutor fractions
/tutor I have a chemistry test on Friday
/tutor A train leaves the station at 3pm going 60 mph...
```

On its own, `/tutor` asks what you want to work on. With a topic or problem, it starts right away.

### 3. Work through it

The tutor will:

1. **Find out what you already know** with open-ended questions.
2. **Check the concept** behind the problem before diving into steps.
3. **Guide you with hints** that get more specific only when you're stuck.
4. **Ask how you got your answer** if you don't show your work.
5. **Review what you learned** and follow up once you solve it.

It **won't give you the answer** unless you ask. Type `--answer` or "just tell me" whenever you want it.

---

## Flags

Type a flag at any point during a session. `--similar`, `/similar`, and `similar` all work.

| Flag | What it does |
|---|---|
| `--similar` | A new problem built from the current one: same concept and theme, new details |
| `--harder` | A similar problem with one extra step of difficulty |
| `--easier` | A similar problem that's a bit simpler |
| `--hint` | The next hint, one level more specific than the last |
| `--answer` | The full solution, then an offer of a practice problem |
| `--check` | Reviews your work and points to where an error is, without fixing it |
| `--explain` | Explains the underlying concept directly |
| `--quiz` | 3–5 questions on the topic, one at a time, with a summary |
| `--recap` | Summary of the session and what to practice next |
| `--whatsasked` | A word problem where you only identify what it's asking |
| `--eli5` | Explains the problem so simply a 5th grader could understand it (also `--explain-to-a-five-year-old`) |
| `--normal` | Goes back to regular language after `--eli5` |
| `--flags` | Lists all flags |

Add details after a flag to adjust it:

```
--similar but with fractions
--harder with a unit conversion
--quiz on the causes of World War I
--eli5 what is photosynthesis
```

---

## Example

> **You:** /tutor What's 3/4 divided by 1/2?
>
> **Tutor:** Let's work it out together. Before computing anything, what do you think dividing by 1/2 actually means? How many halves fit into 3?
>
> **You:** 6. Oh, so it's asking how many halves fit into 3/4?
>
> **Tutor:** Exactly. Try it with 3/4 now.
>
> **You:** 1.5
>
> **Tutor:** How did you get 1.5? Walk me through your steps.

---

## Word problems

The tutor checks whether you understand what a word problem is asking before any math. It will ask you to:

1. Restate the problem in your own words
2. Say what you're solving for, including units
3. Sort the information into what you need and what's extra
4. Plan how to set it up, then solve and check that the answer makes sense

Use `--whatsasked` to practice just the reading part.

---

## Subjects

Works for any subject, including math, science, history, writing, reading, languages, coding, economics, and test prep. The tutor adapts what "the answer" and "showing your work" mean to each one. With `--eli5`, it works for younger learners too, around 5th grade and up.

---

## Repo structure

```
tutor-skill/
├── README.md
├── LICENSE
└── tutor/                           # The skill folder (this is what you install)
    ├── SKILL.md                     # Main tutoring instructions and flags
    └── references/
        ├── word-problems.md         # Detailed word-problem approach
        └── subject-adaptations.md   # How the method adapts per subject
```

---

## Troubleshooting

**`/tutor` doesn't seem to do anything.** Check that the skill is toggled on in **Customize → Skills**, and start a new chat.

**Upload failed.** Make sure you zipped the `tutor` folder, not the whole repo, and that the folder is still named `tutor` with `SKILL.md` inside.

**It gave me the answer without me asking.** Tell it "don't give me the answer, guide me," and consider opening an issue on this repo with the example.

---

## Updating

When this repo changes, download it again, re-zip the `tutor` folder, and upload it in **Customize → Skills** (delete the old version first). In Claude Code, copy the folder into `~/.claude/skills/` again.

---

## License

Released under the [MIT License](LICENSE). You're free to use, modify, and share this skill, including commercially, as long as the copyright notice is kept.
