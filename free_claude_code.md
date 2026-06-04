<div dir="rtl" align="right">

## راه‌اندازی سریع

### ۱. نصب/به‌روزرسانی پروکسی

برای macOS/Linux:

</div>

<div dir="ltr" align="left">

```bash
curl -fsSL "https://github.com/Alishahryar1/free-claude-code/blob/main/scripts/install.sh?raw=1" | sh
```

</div>

<div dir="rtl" align="right">

برای Windows PowerShell:

</div>

<div dir="ltr" align="left">

```powershell
irm "https://github.com/Alishahryar1/free-claude-code/blob/main/scripts/install.ps1?raw=1" | iex
```

</div>

<div dir="rtl" align="right">

نصب‌کننده‌ها را در مسیرهای زیر بررسی کنید:  
<span dir="ltr">scripts/install.sh</span> و <span dir="ltr">scripts/install.ps1</span>.  
برای به‌روزرسانی به آخرین نسخه، همین دستورها را دوباره اجرا کنید.

### ۲. اجرای پروکسی

</div>

<div dir="ltr" align="left">

```bash
fcc-server
```

</div>

<div dir="rtl" align="right">

بعد از راه‌اندازی، <span dir="ltr">Uvicorn</span> آدرس اتصال پروکسی را چاپ می‌کند و لاگ‌های برنامه نشانی <span dir="ltr">Admin UI</span> را نشان می‌دهند:

</div>

<div dir="ltr" align="left">

```text
INFO:     Admin UI: http://127.0.0.1:8082/admin (local-only)
```

</div>

<div dir="rtl" align="right">

در بسیاری از ترمینال‌ها، این آدرس‌ها قابل کلیک هستند. اگر پورت تنظیم‌شده شما <span dir="ltr">8082</span> نیست، از مقدار <span dir="ltr">PORT</span> پیکربندی‌شده خودتان استفاده کنید.

### ۳. باز کردن Admin UI و پیکربندی NVIDIA NIM

آدرس <span dir="ltr">Admin UI</span> را که در خروجی ترمینال نمایش داده شده است، باز کنید.

به کلید API برای <span dir="ltr">NVIDIA NIM</span> نیاز دارید؟ ابتدا بخش «ارائه‌دهنده NVIDIA NIM» را در پایین ببینید و سپس به این قسمت برگردید.

کلید API مربوط به <span dir="ltr">NVIDIA NIM</span> را در فیلد <span dir="ltr">NVIDIA_NIM_API_KEY</span> قرار دهید، سپس روی <span dir="ltr">Validate</span> و بعد <span dir="ltr">Apply</span> کلیک کنید.

مدل پیش‌فرض از قبل روی مقدار زیر تنظیم شده است:

<span dir="ltr">nvidia_nim/nvidia/nemotron-3-super-120b-a12b</span>

بعداً می‌توانید همین مدل را از داخل همان <span dir="ltr">Admin UI</span> تغییر دهید.

### ۴. اجرای Claude Code

</div>

<div dir="ltr" align="left">

```bash
fcc-claude
```

</div>

<div dir="rtl" align="right">

دستور <span dir="ltr">fcc-claude</span> در هر بار اجرا، پورت و توکن احراز هویت فعلی را از تنظیمات می‌خواند، متغیرهای محیطی <span dir="ltr">Claude Code</span> را تنظیم می‌کند، از جمله مقدار <span dir="ltr">CLAUDE_CODE_AUTO_COMPACT_WINDOW</span> با پنجره <span dir="ltr">190k-token</span> برای فشرده‌سازی خودکار، و سپس دستور واقعی <span dir="ltr">claude</span> را اجرا می‌کند.

---

## انتخاب ارائه‌دهنده

یک ارائه‌دهنده را انتخاب کنید، کلید API یا URL محلی آن را در <span dir="ltr">Admin UI</span> وارد کنید، و مقدار <span dir="ltr">MODEL</span> را روی یک شناسه مدل با پیشوند ارائه‌دهنده تنظیم کنید. مقدار <span dir="ltr">MODEL</span> مسیر پیش‌فرض یا fallback است. مقادیر <span dir="ltr">MODEL_OPUS</span>، <span dir="ltr">MODEL_SONNET</span> و <span dir="ltr">MODEL_HAIKU</span> می‌توانند مسیریابی را برای سطح‌های مختلف مدل‌های <span dir="ltr">Claude Code</span> تغییر دهند.

### ۱. NVIDIA NIM

کلید را از مسیر <span dir="ltr">build.nvidia.com/settings/api-keys</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">NVIDIA_NIM_API_KEY</span> قرار دهید. مقدار پیش‌فرض <span dir="ltr">MODEL</span> برابر است با:

<span dir="ltr">nvidia_nim/nvidia/nemotron-3-super-120b-a12b</span>

نمونه‌های پرکاربرد:

- <span dir="ltr">nvidia_nim/nvidia/nemotron-3-super-120b-a12b</span>
- <span dir="ltr">nvidia_nim/z-ai/glm5.1</span>
- <span dir="ltr">nvidia_nim/moonshotai/kimi-k2.5</span>
- <span dir="ltr">nvidia_nim/minimaxai/minimax-m2.5</span>

مدل‌ها را در <span dir="ltr">build.nvidia.com</span> مرور کنید.

### ۲. OpenRouter

کلید را از <span dir="ltr">openrouter.ai/keys</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، کلید را در <span dir="ltr">OPENROUTER_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه <span dir="ltr">OpenRouter</span> مانند مقدار زیر تنظیم کنید:

<span dir="ltr">open_router/openrouter/free</span>

می‌توانید همه مدل‌ها یا مدل‌های رایگان را در سایت <span dir="ltr">OpenRouter</span> ببینید.

### ۳. Google AI Studio / Gemini

کلید API مربوط به <span dir="ltr">Gemini</span> را از <span dir="ltr">Google AI Studio</span> دریافت کنید. برای اطلاعات بیشتر، مستندات سازگاری <span dir="ltr">Gemini OpenAI compatibility</span> گوگل را ببینید.

در <span dir="ltr">Admin UI</span>، کلید را در <span dir="ltr">GEMINI_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه مدل <span dir="ltr">Gemini</span> تنظیم کنید؛ برای مثال:

<span dir="ltr">gemini/models/gemini-3.1-flash-lite</span>

API مربوط به <span dir="ltr">Gemini</span> یک endpoint سازگار با <span dir="ltr">OpenAI</span> در مسیر زیر ارائه می‌کند:

<span dir="ltr">https://generativelanguage.googleapis.com/v1beta/openai/</span>

سهمیه‌های رایگان به‌صورت جداگانه برای هر مدل محاسبه می‌شوند. ممکن است promptها برای بهبود محصولات گوگل استفاده شوند، مگر در برخی مناطق مثل UK، سوئیس، منطقه اقتصادی اروپا یا اتحادیه اروپا، یا در صورتی که منطقه حساب شما شرایط دیگری داشته باشد. شرایط گوگل را بررسی کنید.

نمونه پرکاربرد:

- <span dir="ltr">gemini/models/gemini-3.1-flash-lite</span>

### ۴. DeepSeek

کلید را از <span dir="ltr">platform.deepseek.com/api_keys</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">DEEPSEEK_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه <span dir="ltr">DeepSeek</span> تنظیم کنید؛ مانند:

<span dir="ltr">deepseek/deepseek-chat</span>

این ارائه‌دهنده از endpoint سازگار با <span dir="ltr">Anthropic</span> مربوط به <span dir="ltr">DeepSeek</span> استفاده می‌کند، نه از endpoint مربوط به <span dir="ltr">OpenAI chat-completions</span>.

### ۵. Mistral La Plateforme

<span dir="ltr">Mistral</span> یک API سازگار با <span dir="ltr">OpenAI Chat Completions</span> در این مسیر ارائه می‌کند:

<span dir="ltr">https://api.mistral.ai/v1</span>

برای دسترسی رایگان API با محدودیت نرخ، طرح <span dir="ltr">Experiment</span> را در کنسول <span dir="ltr">Mistral</span> فعال کنید. برای سهمیه‌های بالاتر باید ارتقا دهید.

در <span dir="ltr">Admin UI</span>، کلید API را در <span dir="ltr">MISTRAL_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه مدل <span dir="ltr">Mistral</span> تنظیم کنید؛ مانند:

- <span dir="ltr">mistral/devstral-small-latest</span>
- <span dir="ltr">mistral/mistral-small-latest</span>

مدل‌ها را در مستندات <span dir="ltr">Mistral</span> مرور کنید.

### ۶. Mistral Codestral

درگاه <span dir="ltr">Codestral</span> متعلق به <span dir="ltr">Mistral</span> از یک کلید API جداگانه نسبت به <span dir="ltr">La Plateforme</span> استفاده می‌کند. باید مقدار <span dir="ltr">CODESTRAL_API_KEY</span> را فراهم کنید و سپس با پیشوند <span dir="ltr">mistral_codestral/</span> مسیریابی کنید.

upstream پیش‌فرض این مسیر است:

<span dir="ltr">https://codestral.mistral.ai/v1</span>

این endpoint با <span dir="ltr">OpenAI-compatible Chat Completions</span> سازگار است و همان ساختار درخواست ارائه‌دهنده <span dir="ltr">mistral</span> را دارد. برای حوزه‌های کدنویسی و <span dir="ltr">FIM</span>، مستندات <span dir="ltr">Mistral</span> را ببینید. فهرست curated مربوط به APIهای رایگان LLM نیز معمولاً شرایط دسترسی <span dir="ltr">Codestral</span> را خلاصه می‌کند.

نمونه پرکاربرد:

- <span dir="ltr">mistral_codestral/codestral-latest</span>

### ۷. OpenCode Zen

کلید API را از <span dir="ltr">opencode.ai/auth</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">OPENCODE_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه مدل <span dir="ltr">OpenCode Zen</span> تنظیم کنید؛ مانند:

<span dir="ltr">opencode/gpt-5.3-codex</span>

همین مقدار <span dir="ltr">OPENCODE_API_KEY</span> برای <span dir="ltr">OpenCode Go</span> نیز استفاده می‌شود. برای آن بخش از شناسه‌های دارای پیشوند <span dir="ltr">opencode_go/</span> استفاده کنید.

<span dir="ltr">OpenCode Zen</span> یک درگاه مدل curated است که از طریق یک کلید API واحد و endpoint سازگار با <span dir="ltr">OpenAI</span> در مسیر زیر، به مدل‌هایی از <span dir="ltr">Anthropic</span>، <span dir="ltr">OpenAI</span>، گوگل، <span dir="ltr">DeepSeek</span> و ارائه‌دهندگان دیگر دسترسی می‌دهد:

<span dir="ltr">https://opencode.ai/zen/v1</span>

نمونه‌های پرکاربرد:

- <span dir="ltr">opencode/gpt-5.3-codex</span>
- <span dir="ltr">opencode/claude-sonnet-4</span>
- <span dir="ltr">opencode/deepseek-v4-flash-free</span> — رایگان
- <span dir="ltr">opencode/gemini-3-flash</span>
- <span dir="ltr">opencode/big-pickle</span> — رایگان
- <span dir="ltr">opencode/glm-5.1</span>

مدل‌های موجود را در <span dir="ltr">opencode.ai</span> مرور کنید.

### ۸. OpenCode Go

کلید API را از <span dir="ltr">opencode.ai/auth</span> دریافت کنید. این همان کلید <span dir="ltr">OpenCode Zen</span> است.

در <span dir="ltr">Admin UI</span>، از <span dir="ltr">OPENCODE_API_KEY</span> استفاده کنید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه مدل <span dir="ltr">OpenCode Go</span> تنظیم کنید؛ مانند:

<span dir="ltr">opencode_go/minimax-m2.7</span>

<span dir="ltr">OpenCode Go</span> یک درگاه اشتراکی با فهرست curated مخصوص خود و endpoint سازگار با <span dir="ltr">OpenAI</span> در مسیر زیر است:

<span dir="ltr">https://opencode.ai/zen/go/v1</span>

این سرویس همان کلید API مربوط به <span dir="ltr">Zen</span> را استفاده می‌کند؛ تفاوت فقط در پیشوند شناسه مدل و مسیر upstream است: <span dir="ltr">opencode_go/</span> در برابر <span dir="ltr">opencode/</span>.

نمونه پرکاربرد:

- <span dir="ltr">opencode_go/minimax-m2.7</span>

مدل‌های موجود را در <span dir="ltr">opencode.ai</span> مرور کنید.

### ۹. Wafer

کلید را از <span dir="ltr">wafer.ai</span> دریافت کنید. در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">WAFER_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک مدل <span dir="ltr">Wafer Pass</span> تنظیم کنید؛ مانند:

<span dir="ltr">wafer/DeepSeek-V4-Pro</span>

نمونه‌های پرکاربرد:

- <span dir="ltr">wafer/DeepSeek-V4-Pro</span>
- <span dir="ltr">wafer/MiniMax-M2.7</span>
- <span dir="ltr">wafer/Qwen3.5-397B-A17B</span>
- <span dir="ltr">wafer/GLM-5.1</span>

این ارائه‌دهنده از endpoint سازگار با <span dir="ltr">Anthropic</span> متعلق به <span dir="ltr">Wafer</span> در مسیر زیر استفاده می‌کند:

<span dir="ltr">https://pass.wafer.ai/v1/messages</span>

### ۱۰. Kimi

کلید را از <span dir="ltr">platform.moonshot.ai/console/api-keys</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">KIMI_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه <span dir="ltr">Kimi</span> تنظیم کنید؛ مانند:

<span dir="ltr">kimi/kimi-k2.5</span>

این ارائه‌دهنده API پیام‌های سازگار با <span dir="ltr">Anthropic</span> متعلق به <span dir="ltr">Kimi</span> را فراخوانی می‌کند:

<span dir="ltr">https://api.moonshot.ai/anthropic/v1/messages</span>

کشف مدل از مسیر سازگار با <span dir="ltr">OpenAI</span> انجام می‌شود:

<span dir="ltr">GET https://api.moonshot.ai/v1/models</span>

این مسیر، مسیر <span dir="ltr">OpenAI Chat Completions</span> نیست.

مدل‌ها را در <span dir="ltr">platform.moonshot.ai</span> مرور کنید.

### ۱۱. Cerebras Inference

ثبت‌نام کنید و در <span dir="ltr">Cerebras Cloud Console</span> یک کلید API بسازید. برای شروع، راهنمای <span dir="ltr">Quickstart</span> مربوط به <span dir="ltr">Cerebras</span> را ببینید.

در <span dir="ltr">Admin UI</span>، مقدار <span dir="ltr">CEREBRAS_API_KEY</span> را تنظیم کنید، سپس با <span dir="ltr">MODEL</span> مسیریابی کنید؛ مانند:

- <span dir="ltr">cerebras/llama3.1-8b</span>
- <span dir="ltr">cerebras/gpt-oss-120b</span>

شناسه‌ها را می‌توانید از فهرست مدل‌های <span dir="ltr">Cerebras</span> بردارید.

<span dir="ltr">Cerebras</span> یک API سازگار با <span dir="ltr">OpenAI</span> در مسیر زیر ارائه می‌کند:

<span dir="ltr">https://api.cerebras.ai/v1</span>

فیلدهای غیر استاندارد درخواست باید هنگام استفاده از کلاینت <span dir="ltr">OpenAI</span> داخل <span dir="ltr">extra_body</span> قرار بگیرند. برای مدل‌های reasoning و پارامترهای آن‌ها، مستندات <span dir="ltr">Reasoning</span> را ببینید. این پروکسی، مشابه سایر adapterهای سازگار با <span dir="ltr">OpenAI</span>، هنگام فعال بودن thinking به سبک Claude، محتوای thinking را از طریق <span dir="ltr">reasoning_content</span> مدیریت می‌کند.

### ۱۲. Groq

کلید API را از <span dir="ltr">console.groq.com/keys</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">GROQ_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک مدل سازگار با <span dir="ltr">OpenAI</span> متعلق به <span dir="ltr">Groq</span> تنظیم کنید؛ مانند:

<span dir="ltr">groq/llama-3.3-70b-versatile</span>

<span dir="ltr">Groq</span> از مسیر زیر استفاده می‌کند:

<span dir="ltr">https://api.groq.com/openai/v1</span>

برخی از فیلدهای درخواست ممکن است خطای HTTP 400 ایجاد کنند؛ این adapter شکل‌های شناخته‌شده‌ای را که پشتیبانی نمی‌شوند حذف می‌کند.

مدل‌های سنگین‌تر reasoning پارامترهای بیشتری دارند که در مستندات reasoning مربوط به <span dir="ltr">Groq</span> آمده است. این نسخه، مشابه سایر adapterهای سازگار با <span dir="ltr">OpenAI</span>، هنگام فعال بودن thinking به سبک Claude از deltaهای <span dir="ltr">reasoning_content</span> استفاده می‌کند. در صورت نیاز می‌توانید پارامترهای پیشرفته را از طریق <span dir="ltr">extra_body</span> درخواست تنظیم کنید.

مدل‌ها را در مستندات مدل‌های <span dir="ltr">Groq</span> مرور کنید.

### ۱۳. Fireworks AI

کلید API را از <span dir="ltr">fireworks.ai/account/api-keys</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">FIREWORKS_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه مدل <span dir="ltr">Fireworks</span> تنظیم کنید؛ مانند:

<span dir="ltr">fireworks/accounts/fireworks/models/llama-v3p3-70b-instruct</span>

<span dir="ltr">Fireworks</span> یک API پیام‌های سازگار با <span dir="ltr">Anthropic</span> در مسیر زیر ارائه می‌کند:

<span dir="ltr">https://api.fireworks.ai/inference/v1/messages</span>

این همان host قبلی inference است و در اینجا از <span dir="ltr">Chat Completions</span> استفاده نمی‌شود. کلیدهای JSON اختصاصی فروشنده نیز، در صورت مجاز بودن، می‌توانند از <span dir="ltr">extra_body</span> درخواست ادغام شوند.

مدل‌ها را در <span dir="ltr">fireworks.ai/models</span> مرور کنید.

### ۱۴. Z.ai

کلید API را از <span dir="ltr">Z.ai/manage-apikey/apikey-list</span> دریافت کنید.

در <span dir="ltr">Admin UI</span>، آن را در <span dir="ltr">ZAI_API_KEY</span> قرار دهید، سپس <span dir="ltr">MODEL</span> را روی یک شناسه مدل <span dir="ltr">Z.ai</span> تنظیم کنید؛ مانند:

<span dir="ltr">zai/glm-5.1</span>

این ارائه‌دهنده API پیام‌های سازگار با <span dir="ltr">Anthropic</span> متعلق به <span dir="ltr">Z.ai</span> را فراخوانی می‌کند:

<span dir="ltr">https://api.z.ai/api/anthropic/v1/messages</span>

مبنای قبلی <span dir="ltr">OpenAI Coding Plan</span> در مسیر زیر، توسط این gateway استفاده نمی‌شود:

<span dir="ltr">https://api.z.ai/api/coding/paas/v4</span>

نمونه‌های پرکاربرد:

- <span dir="ltr">zai/glm-5.1</span>
- <span dir="ltr">zai/glm-5-turbo</span>

مدل‌ها را در <span dir="ltr">Z.ai</span> مرور کنید.

### ۱۵. LM Studio

سرور محلی <span dir="ltr">LM Studio</span> را اجرا کنید و یک مدل را load کنید. در <span dir="ltr">Admin UI</span>، مقدار <span dir="ltr">LM_STUDIO_BASE_URL</span> را حفظ یا به‌روزرسانی کنید، سپس <span dir="ltr">MODEL</span> را روی شناسه مدلی تنظیم کنید که <span dir="ltr">LM Studio</span> نمایش می‌دهد؛ با پیشوند <span dir="ltr">lmstudio/</span>.

برای workflowهای مربوط به <span dir="ltr">Claude Code</span>، بهتر است مدل‌هایی را انتخاب کنید که از tool-use پشتیبانی می‌کنند.

### ۱۶. llama.cpp

سرور <span dir="ltr">llama-server</span> را با endpoint سازگار با <span dir="ltr">Anthropic</span> در مسیر <span dir="ltr">/v1/messages</span> و با context کافی برای درخواست‌های <span dir="ltr">Claude Code</span> اجرا کنید.

در <span dir="ltr">Admin UI</span>، مقدار <span dir="ltr">LLAMACPP_BASE_URL</span> را حفظ یا به‌روزرسانی کنید، سپس <span dir="ltr">MODEL</span> را روی شناسه مدل محلی تنظیم کنید؛ با پیشوند <span dir="ltr">llamacpp/</span>.

برای مدل‌های کدنویسی محلی، اندازه context مهم است. اگر <span dir="ltr">llama.cpp</span> برای درخواست‌های معمول <span dir="ltr">Claude Code</span> خطای HTTP 400 برگرداند، مقدار <span dir="ltr">--ctx-size</span> را افزایش دهید و مطمئن شوید که مدل یا build سرور از قابلیت‌های درخواستی پشتیبانی می‌کند.

### ۱۷. Ollama

<span dir="ltr">Ollama</span> را اجرا کنید و یک مدل را دریافت کنید:

</div>

<div dir="ltr" align="left">

```bash
ollama pull llama3.1
ollama serve
```

</div>

<div dir="rtl" align="right">

در <span dir="ltr">Admin UI</span>، مقدار <span dir="ltr">OLLAMA_BASE_URL</span> را حفظ یا به‌روزرسانی کنید، سپس <span dir="ltr">MODEL</span> را روی همان tag نمایش‌داده‌شده توسط <span dir="ltr">ollama list</span> تنظیم کنید؛ با پیشوند <span dir="ltr">ollama/</span>.

مقدار <span dir="ltr">OLLAMA_BASE_URL</span> ریشه سرور <span dir="ltr">Ollama</span> است؛ نباید <span dir="ltr">/v1</span> را به آن اضافه کنید. نمونه شناسه‌های مدل:

- <span dir="ltr">ollama/llama3.1</span>
- <span dir="ltr">ollama/llama3.1:8b</span>

### ۱۸. ترکیب ارائه‌دهندگان بر اساس سطح مدل

هر سطح مدل می‌تواند با تنظیم مقادیر زیر در <span dir="ltr">Admin UI</span> از یک ارائه‌دهنده متفاوت استفاده کند:

- <span dir="ltr">MODEL_OPUS</span>
- <span dir="ltr">MODEL_SONNET</span>
- <span dir="ltr">MODEL_HAIKU</span>

اگر مقدار یک سطح را خالی بگذارید، از مقدار <span dir="ltr">MODEL</span> ارث‌بری می‌کند.

برای مثال، می‌توانید <span dir="ltr">Opus</span> را به <span dir="ltr">nvidia_nim/moonshotai/kimi-k2.6</span>، <span dir="ltr">Sonnet</span> را به <span dir="ltr">open_router/openrouter/free</span>، <span dir="ltr">Haiku</span> را به <span dir="ltr">lmstudio/qwen3.5-coder</span> هدایت کنید و fallback یعنی <span dir="ltr">MODEL</span> را روی <span dir="ltr">zai/glm-5.1</span> نگه دارید.

---

## اتصال Claude Code

### ۱. Claude Code CLI

برای استفاده در ترمینال، بهتر است از launcher نصب‌شده استفاده کنید:

</div>

<div dir="ltr" align="left">

```bash
fcc-claude
```

</div>

<div dir="rtl" align="right">

هنگام کار، <span dir="ltr">fcc-server</span> را در حال اجرا نگه دارید. <span dir="ltr">Admin UI</span> پیکربندی پروکسی را مدیریت می‌کند، وقتی تنظیمات runtime تغییر کنند سرور را restart می‌کند، و <span dir="ltr">fcc-claude</span> در هر بار اجرا URL پروکسی محلی و توکن احراز هویت مدیریت‌شده توسط <span dir="ltr">Admin UI</span> را می‌خواند. همچنین مقدار <span dir="ltr">CLAUDE_CODE_AUTO_COMPACT_WINDOW</span> را برای فشرده‌سازی خودکار روی <span dir="ltr">190000</span> تنظیم می‌کند.

### ۲. افزونه VS Code

Settings را باز کنید، عبارت <span dir="ltr">claude-code.environmentVariables</span> را جست‌وجو کنید، گزینه <span dir="ltr">Edit in settings.json</span> را انتخاب کنید و موارد زیر را اضافه کنید:

</div>

<div dir="ltr" align="left">

```json
"claudeCode.environmentVariables": [
  { "name": "ANTHROPIC_BASE_URL", "value": "http://localhost:8082" },
  { "name": "ANTHROPIC_AUTH_TOKEN", "value": "freecc" },
  { "name": "CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY", "value": "1" },
  { "name": "CLAUDE_CODE_AUTO_COMPACT_WINDOW", "value": "190000" }
]
```

</div>

<div dir="rtl" align="right">

افزونه را reload کنید. اگر افزونه صفحه login نشان داد، یک‌بار مسیر <span dir="ltr">Anthropic Console</span> را انتخاب کنید؛ پس از فعال شدن متغیرهای محیطی، پروکسی محلی همچنان ترافیک مدل را مدیریت می‌کند.

### ۳. JetBrains ACP

فایل پیکربندی نصب‌شده <span dir="ltr">Claude ACP</span> را ویرایش کنید:

- Windows: <span dir="ltr">C:\Users\%USERNAME%\AppData\Roaming\JetBrains\acp-agents\installed.json</span>
- Linux/macOS: <span dir="ltr">~/.jetbrains/acp.json</span>

محیط مربوط به <span dir="ltr">acp.registry.claude-acp</span> را به شکل زیر تنظیم کنید:

</div>

<div dir="ltr" align="left">

```json
"env": {
  "ANTHROPIC_BASE_URL": "http://localhost:8082",
  "ANTHROPIC_AUTH_TOKEN": "freecc",
  "CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY": "1",
  "CLAUDE_CODE_AUTO_COMPACT_WINDOW": "190000"
}
```

</div>

<div dir="rtl" align="right">

بعد از تغییر فایل، IDE را restart کنید.

</div>
