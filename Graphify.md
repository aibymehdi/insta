

توی دستیار کدنویسی هوش مصنوعی‌ات `/graphify` رو تایپ کن؛ کل پروژه‌ات — کد، داکیومنت‌ها، PDFها، عکس‌ها، ویدیوها — تبدیل می‌شه به یه knowledge graph که می‌تونی ازش سؤال بپرسی، بدون اینکه بین فایل‌ها بگردی و grep بزنی.

با Claude Code، Codex، OpenCode، Kilo Code، Cursor، Gemini CLI، GitHub Copilot CLI، VS Code Copilot Chat، Aider، Amp، OpenClaw، Factory Droid، Trae، Hermes، Kimi Code، Kiro، Pi، Devin CLI و Google Antigravity کار می‌کنه.

```
/graphify .
```

همین. سه تا فایل می‌گیری:

```
graphify-out/
├── graph.html       open in any browser — click nodes, filter, search
├── GRAPH_REPORT.md  the highlights: key concepts, surprising connections, suggested questions
└── graph.json       the full graph — query it anytime without re-reading your files
```

برای ساختن یه صفحه معماری خوانا با دیاگرام‌های Mermaid از نوع call-flow، اینو اجرا کن:

```bash
graphify export callflow-html
```

---

## پیش‌نیازها

| نیازمندی | حداقل نسخه | چک کردن | نصب |
|---|---|---|---|
| Python | 3.10+ | `python --version` | [python.org](https://www.python.org/downloads/) |
| uv *(پیشنهادی)* | هر نسخه‌ای | `uv --version` | `curl -LsSf https://astral.sh/uv/install.sh \| sh` |
| pipx *(جایگزین)* | هر نسخه‌ای | `pipx --version` | `pip install pipx` |

**نصب سریع روی macOS با Homebrew:**
```bash
brew install python@3.12 uv
```

**نصب سریع روی Windows:**
```powershell
winget install astral-sh.uv
```

**Ubuntu/Debian:**
```bash
sudo apt install python3.12 python3-pip pipx
# or install uv:
curl -LsSf https://astral.sh/uv/install.sh | sh
```

---

## نصب

> **پکیج رسمی:** پکیج PyPI اسمش `graphifyy` هست، با دو تا y. بقیه پکیج‌های `graphify*` روی PyPI وابسته به این پروژه نیستن. دستور CLI همچنان `graphify` هست.

**مرحله ۱ — پکیج رو نصب کن:**

```bash
# Recommended (uv puts graphify on PATH automatically):
uv tool install graphifyy

# Alternatives:
pipx install graphifyy
pip install graphifyy  # may need PATH setup — see note below
```

**مرحله ۲ — skill رو برای دستیار AI خودت ثبت کن:**

```bash
graphify install
```

همین. دستیار AI خودت رو باز کن و تایپ کن `/graphify .`

برای اینکه skill دستیار به‌جای پروفایل کاربری، داخل همین repository فعلی نصب بشه، فلگ `--project` رو اضافه کن:

```bash
graphify install --project
graphify install --project --platform codex
```

نصب‌های project-scoped زیر دایرکتوری فعلی نوشته می‌شن؛ مثلا
`.claude/skills/graphify/SKILL.md` یا `.agents/skills/graphify/SKILL.md`
به‌همراه یه sidecar به اسم `references/` که skill موقع نیاز لودش می‌کنه.
همچنین یه راهنمای `git add` هم چاپ می‌کنه برای فایل‌هایی که می‌تونی commit کنی.
دستورهای مخصوص هر پلتفرم که نصب project-scoped رو ساپورت می‌کنن، همین فلگ رو قبول می‌کنن؛
مثلا `graphify claude install --project` یا `graphify codex install --project`.

> **نکته PowerShell:** از `graphify .` استفاده کن، نه `/graphify .`؛ چون اسلش اول در PowerShell جداکننده مسیر حساب می‌شه.

> **خطای `graphify: command not found`؟** از `uv tool install graphifyy` یا `pipx install graphifyy` استفاده کن؛ هر دو CLI رو خودکار روی PATH می‌ذارن. اگر با `pip` معمولی نصب کردی، باید `~/.local/bin` در Linux یا `~/Library/Python/3.x/bin` در Mac رو به PATH اضافه کنی، یا با `python -m graphify` اجراش کنی.

> **اگه می‌تونی روی Mac/Windows از `pip install` استفاده نکن.** این skill موقع اجرا Python رو از `graphify-out/.graphify_python` پیدا می‌کنه؛ اگر اون به محیطی متفاوت از جایی که `pip` پکیج رو نصب کرده اشاره کنه، خطای `ModuleNotFoundError: No module named 'graphify'` می‌گیری. `uv tool install` و `pipx install` پکیج رو توی محیط جدا نصب می‌کنن و کلا این مشکل رو دور می‌زنن.

> **Git hooks و uv tool / pipx:** دستور `graphify hook install` موقع نصب، مسیر interpreter فعلی رو مستقیم داخل hook scriptها می‌نویسه؛ برای همین post-commit hook حتی توی git clientهای گرافیکی و CI runnerهایی که `~/.local/bin` توی PATH نیست هم درست اجرا می‌شه. اگر graphify رو دوباره نصب یا آپگرید کردی، دوباره `graphify hook install` رو اجرا کن تا مسیر embed‌شده تازه بشه.

### پلتفرمت رو انتخاب کن

| پلتفرم | دستور نصب |
|----------|----------------|
| Claude Code (Linux/Mac) | `graphify install` |
| Claude Code (Windows) | `graphify install` (خودکار تشخیص می‌ده) یا `graphify install --platform windows` |
| CodeBuddy | `graphify install --platform codebuddy` |
| Codex | `graphify install --platform codex` |
| OpenCode | `graphify install --platform opencode` |
| Kilo Code | `graphify install --platform kilo` |
| GitHub Copilot CLI | `graphify install --platform copilot` |
| VS Code Copilot Chat | `graphify vscode install` |
| Aider | `graphify install --platform aider` |
| OpenClaw | `graphify install --platform claw` |
| Factory Droid | `graphify install --platform droid` |
| Trae | `graphify install --platform trae` |
| Trae CN | `graphify install --platform trae-cn` |
| Gemini CLI | `graphify install --platform gemini` |
| Hermes | `graphify install --platform hermes` |
| Kimi Code | `graphify install --platform kimi` |
| Amp | `graphify amp install` |
| Kiro IDE/CLI | `graphify kiro install` |
| Pi coding agent | `graphify install --platform pi` |
| Cursor | `graphify cursor install` |
| Devin CLI | `graphify devin install` |
| Google Antigravity | `graphify antigravity install` |

کاربرهای Codex برای استخراج موازی باید توی `~/.codex/config.toml` زیر `[features]` مقدار `multi_agent = true` رو هم داشته باشن. CodeBuddy از همون مکانیسم Agent tool و PreToolUse hook مثل Claude Code استفاده می‌کنه. Factory Droid برای dispatch کردن subagentهای موازی از ابزار `Task` استفاده می‌کنه. OpenClaw و Aider استخراج رو ترتیبی انجام می‌دن، چون پشتیبانی از agent موازی توی این پلتفرم‌ها هنوز اول راهه. Trae برای dispatch موازی subagentها از Agent tool استفاده می‌کنه و از PreToolUse hook پشتیبانی نمی‌کنه؛ پس `AGENTS.md` مکانیسم همیشه‌فعالشه.

> Codex به‌جای `/graphify` از `$graphify` استفاده می‌کنه.

### گزینه‌های اضافه اختیاری

فقط چیزهایی رو نصب کن که لازم داری:

| Extra | چی اضافه می‌کنه | نصب |
|---|---|---|
| `pdf` | استخراج از PDF | `uv tool install "graphifyy[pdf]"` |
| `office` | پشتیبانی از `.docx` و `.xlsx` | `uv tool install "graphifyy[office]"` |
| `google` | رندر کردن Google Sheets | `uv tool install "graphifyy[google]"` |
| `video` | تبدیل ویدیو/صدا به متن، با faster-whisper و yt-dlp | `uv tool install "graphifyy[video]"` |
| `mcp` | سرور MCP stdio | `uv tool install "graphifyy[mcp]"` |
| `neo4j` | امکان push به Neo4j | `uv tool install "graphifyy[neo4j]"` |
| `svg` | خروجی گرفتن گراف به SVG | `uv tool install "graphifyy[svg]"` |
| `leiden` | تشخیص community با Leiden، فقط برای Python کمتر از 3.13 | `uv tool install "graphifyy[leiden]"` |
| `ollama` | inference محلی با Ollama | `uv tool install "graphifyy[ollama]"` |
| `openai` | OpenAI / APIهای سازگار با OpenAI | `uv tool install "graphifyy[openai]"` |
| `gemini` | Google Gemini API | `uv tool install "graphifyy[gemini]"` |
| `anthropic` | Anthropic Claude API با `--backend claude` و `ANTHROPIC_API_KEY` | `uv tool install "graphifyy[anthropic]"` |
| `bedrock` | AWS Bedrock، با IAM و بدون API key | `uv tool install "graphifyy[bedrock]"` |
| `azure` | Azure OpenAI Service با `--backend azure` و `AZURE_OPENAI_API_KEY` + `AZURE_OPENAI_ENDPOINT` | `uv tool install "graphifyy[openai]"` |
| `sql` | استخراج schema از SQL | `uv tool install "graphifyy[sql]"` |
| `postgres` | introspection زنده از PostgreSQL با `--postgres DSN` | `uv tool install "graphifyy[postgres]"` |
| `dm` | استخراج AST برای BYOND DreamMaker `.dm`/`.dme`؛ اگر wheel مناسب پلتفرمت نباشه شاید C compiler و `python3-dev` لازم بشه | `uv tool install "graphifyy[dm]"` |
| `terraform` | استخراج AST برای Terraform / HCL `.tf`/`.tfvars`/`.hcl` | `uv tool install "graphifyy[terraform]"` |
| `chinese` | بخش‌بندی queryهای چینی با jieba | `uv tool install "graphifyy[chinese]"` |
| `all` | همه موارد بالا | `uv tool install "graphifyy[all]"` |

---

## کاری کن دستیار همیشه از گراف استفاده کنه

بعد از اینکه توی پروژه‌ات گراف ساختی، اینو یک‌بار اجرا کن:

| پلتفرم | دستور |
|----------|---------|
| Claude Code | `graphify claude install` |
| CodeBuddy | `graphify codebuddy install` |
| Codex | `graphify codex install` |
| OpenCode | `graphify opencode install` |
| Kilo Code | `graphify kilo install` |
| GitHub Copilot CLI | `graphify copilot install` |
| VS Code Copilot Chat | `graphify vscode install` |
| Aider | `graphify aider install` |
| OpenClaw | `graphify claw install` |
| Factory Droid | `graphify droid install` |
| Trae | `graphify trae install` |
| Trae CN | `graphify trae-cn install` |
| Cursor | `graphify cursor install` |
| Gemini CLI | `graphify gemini install` |
| Hermes | `graphify hermes install` |
| Kimi Code | `graphify install --platform kimi` |
| Amp | `graphify amp install` |
| Kiro IDE/CLI | `graphify kiro install` |
| Pi coding agent | `graphify pi install` |
| Devin CLI | `graphify devin install` |
| Google Antigravity | `graphify antigravity install` |

این یه فایل کانفیگ کوچیک می‌نویسه که به دستیار می‌گه برای سؤال‌های مربوط به codebase اول بره سراغ knowledge graph؛ یعنی queryهای محدودی مثل `graphify query "<question>"` رو به خواندن کل گزارش یا grep زدن روی فایل‌های خام ترجیح بده. روی پلتفرم‌هایی که hookهای دارای payload رو ساپورت می‌کنن، مثل Claude Code و Gemini CLI، قبل از tool callهای شبیه search یه hook خودکار اجرا می‌شه. در Claude Code حتی قبل از خوندن یکی‌یکی source fileها با ابزارهای Read/Glob هم این یادآوری انجام می‌شه و دستیار رو به مسیر گراف هل می‌ده. روی بقیه پلتفرم‌ها مثل Codex، OpenCode، Cursor و غیره، فایل‌های instruction دائمی مثل `AGENTS.md` و `.cursor/rules/` همین راهنمای query-first رو می‌دن. فایل `GRAPH_REPORT.md` هم هنوز برای مرور کلی معماری در دسترسه.

**CodeBuddy** هم همون دو کار Claude Code رو انجام می‌ده: یه بخش توی `CODEBUDDY.md` می‌نویسه که به CodeBuddy می‌گه قبل از جواب دادن به سؤال‌های معماری، `graphify-out/GRAPH_REPORT.md` رو بخونه؛ و **PreToolUse hooks** داخل `.codebuddy/settings.json` نصب می‌کنه که قبل از دستورهای Bash search و file read اجرا می‌شن و به‌جاش `graphify query` رو پیشنهاد می‌دن.

**Codex** داخل `AGENTS.md` می‌نویسه و یه **PreToolUse hook** هم توی `.codex/hooks.json` نصب می‌کنه که قبل از هر Bash tool call اجرا می‌شه؛ یعنی همون مکانیسم همیشه‌فعال Claude Code.

برای حذف graphify از همه پلتفرم‌ها با هم: `graphify uninstall` رو اجرا کن. اگر `--purge` رو هم اضافه کنی، `graphify-out/` هم پاک می‌شه. یا از دستور مخصوص هر پلتفرم استفاده کن، مثلا `graphify claude uninstall`.

---

**Kilo Code**، skill گرافیفای رو توی `~/.config/kilo/skills/graphify/SKILL.md` نصب می‌کنه و یه دستور native به اسم `/graphify` هم توی `~/.config/kilo/command/graphify.md` می‌سازه. دستور `graphify kilo install` علاوه‌بر این، `AGENTS.md` و یه پلاگین native از نوع **`tool.execute.before`** هم می‌نویسه: `.kilo/plugins/graphify.js` به‌همراه ثبت در `.kilo/kilo.json` یا `.kilo/kilo.jsonc`. نتیجه‌اش اینه که Kilo هم از طریق کانفیگ native `.kilo` همون یادآوری همیشه‌فعال برای استفاده از گراف رو می‌گیره.

**Cursor** فایل `.cursor/rules/graphify.mdc` رو با `alwaysApply: true` می‌نویسه؛ Cursor اون رو خودکار توی هر گفتگو وارد می‌کنه، پس hook لازم نیست.

## داخل گزارش چی هست

- **God nodes** — متصل‌ترین conceptهای پروژه‌ات. تقریبا همه‌چیز از این‌ها رد می‌شه.
- **Surprising connections** — لینک‌هایی بین چیزهایی که توی فایل‌ها یا ماژول‌های جدا هستن. بر اساس اینکه چقدر غیرمنتظره‌ان رتبه‌بندی می‌شن.
- **The "why"** — کامنت‌های inline مثل `# NOTE:`، `# WHY:`، `# HACK:`، docstringها و منطق طراحی داخل docs به‌عنوان nodeهای جدا استخراج می‌شن و به کدی که توضیحش می‌دن وصل می‌شن.
- **Suggested questions** — چهار پنج تا سؤال که graph مخصوصا برای جواب دادن به اون‌ها خوبه.
- **Confidence tags** — هر رابطه استنباطی با `EXTRACTED`، `INFERRED` یا `AMBIGUOUS` علامت می‌خوره. همیشه می‌فهمی کدوم چیز واقعا پیدا شده و کدوم حدس زده شده.

---

## چه فایل‌هایی رو پوشش می‌ده

| نوع | پسوندها |
|------|-----------|
| کد، شامل ۲۸ گرامر tree-sitter | `.py .ts .js .jsx .tsx .mjs .go .rs .java .c .cpp .h .hpp .rb .cs .kt .scala .php .swift .lua .luau .zig .ps1 .ex .exs .m .mm .jl .vue .svelte .astro .groovy .gradle .dart .v .sv .svh .sql .f .f90 .f95 .f03 .f08 .pas .pp .dpr .dpk .lpr .inc .dfm .lfm .lpk .sh .bash .json .dm .dme .dmi .dmm .dmf .sln .slnx .csproj .fsproj .vbproj .razor .cshtml` (`.dm`/`.dme` نیاز به `uv tool install graphifyy[dm]` داره) |
| Salesforce Apex | `.cls .trigger`؛ مبتنی بر regex، شامل classها، interfaceها، enumها، methodها، triggerها و edgeهای SOQL/DML |
| Terraform / HCL | `.tf .tfvars .hcl`؛ نیاز به `uv tool install graphifyy[terraform]` داره |
| کانفیگ‌های MCP | `.mcp.json` `mcp.json` `mcp_servers.json` `claude_desktop_config.json`؛ server nodeها، package referenceها و نیازمندی‌های env var رو استخراج می‌کنه |
| داکیومنت‌ها | `.md .mdx .qmd .html .txt .rst .yaml .yml` |
| Office | `.docx .xlsx`؛ نیاز به `uv tool install graphifyy[office]` داره |
| Google Workspace | `.gdoc .gsheet .gslides`؛ opt-in هست، نیاز به auth با `gws` و `--google-workspace` داره؛ Sheets هم `uv tool install graphifyy[google]` می‌خواد |
| PDFها | `.pdf` |
| عکس‌ها | `.png .jpg .webp .gif` |
| ویدیو / صدا | `.mp4 .mov .mp3 .wav` و موارد بیشتر؛ نیاز به `uv tool install graphifyy[video]` داره |
| YouTube / URLها | هر URL ویدیویی؛ نیاز به `uv tool install graphifyy[video]` داره |

کدها به‌صورت محلی و بدون هیچ API call استخراج می‌شن، با AST از طریق tree-sitter. هر چیز غیر از کد، از طریق API مدل دستیار AI خودت پردازش می‌شه.

فایل‌های `.gdoc`، `.gsheet` و `.gslides` مربوط به Google Drive for desktop درواقع shortcut pointer هستن، نه محتوای اصلی سند. برای اینکه Google Docs، Sheets و Slides واقعی توی استخراج headless وارد بشن، CLI مربوط به [`gws`](https://github.com/googleworkspace/cli) رو نصب و authenticate کن، بعد این دستورها رو اجرا کن:

```bash
uv tool install "graphifyy[google]"  # needed for Google Sheets table rendering
gws auth login -s drive
graphify extract ./docs --google-workspace
```

می‌تونی `GRAPHIFY_GOOGLE_WORKSPACE=1` رو هم set کنی. Graphify shortcutها رو داخل `graphify-out/converted/` به‌صورت sidecarهای Markdown export می‌کنه و بعد همون فایل‌ها رو استخراج می‌کنه.

---

## دستورهای رایج

```bash
/graphify .                        # build graph for current folder
/graphify ./docs --update          # re-extract only changed files
/graphify . --cluster-only         # rerun clustering without re-extracting
/graphify . --cluster-only --resolution 1.5      # more granular communities
/graphify . --cluster-only --exclude-hubs 99     # suppress utility super-hubs from god-node rankings
/graphify . --no-viz               # skip the HTML, just the report + JSON
/graphify . --wiki                 # build a markdown wiki from the graph
graphify export callflow-html      # Mermaid architecture/call-flow HTML (auto-regenerates on every git commit if hook is installed)

/graphify query "what connects auth to the database?"
/graphify path "UserService" "DatabasePool"
/graphify explain "RateLimiter"

/graphify add https://arxiv.org/abs/1706.03762   # fetch a paper and add it
/graphify add <youtube-url>                       # transcribe and add a video

graphify hook install              # auto-rebuild on git commit
graphify merge-graphs a.json b.json              # combine two graphs

graphify prs                       # PR dashboard: CI state, review status, worktree mapping
graphify prs 42                    # deep dive on PR #42 with graph impact
graphify prs --triage              # AI ranks your review queue (uses whatever backend is configured)
graphify prs --conflicts           # PRs sharing graph communities — merge-order risk
```

مرجع کامل دستورها رو پایین‌تر در [full command reference](#full-command-reference) ببین.

---
