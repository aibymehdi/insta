## 🚀 **دنبال یه راه حتی سریع‌تر و ساده‌تر برای اسکرپ در مقیاس بالا هستی، فقط با ۵ خط کد؟** نسخه بهتر و کامل‌تر ما رو توی [**ScrapeGraphAI.com**](https://scrapegraphai.com/?utm_source=github&utm_medium=readme&utm_campaign=oss_cta&ut#m_content=top_banner) ببین! 🚀

---

# 🕷️ ScrapeGraphAI: فقط یک بار اسکرپ کن

<p align="center">
  <a href="https://scrapegraphai.com">
    <img src="media/banner.png" alt="ScrapeGraphAI" style="width: 100%;">
  </a>
</p>

[English](README.md) | [中文](docs/chinese.md) | [日本語](docs/japanese.md)
| [한국어](docs/korean.md)
| [Русский](docs/russian.md) | [Türkçe](docs/turkish.md)
| [Deutsch](docs/german.md)
| [Español](docs/spanish.md)
| [français](docs/french.md)
| [Português](docs/portuguese.md)
| [Italiano](docs/italian.md)

[![PyPI Downloads](https://static.pepy.tech/personalized-badge/scrapegraphai?period=total&units=INTERNATIONAL_SYSTEM&left_color=BLACK&right_color=GREEN&left_text=downloads)](https://pepy.tech/projects/scrapegraphai)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![](https://dcbadge.vercel.app/api/server/gkxQDAjfeX)](https://discord.gg/gkxQDAjfeX)

<p align="center">
<a href="https://trendshift.io/repositories/15078" target="_blank"><img src="https://trendshift.io/api/badge/repositories/15078" alt="ScrapeGraphAI%2FScrapegraph-ai | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
<p align="center">

[ScrapeGraphAI](https://scrapegraphai.com) یه کتابخونه پایتونی برای *وب‌اسکرپینگ*ه که از LLM و منطق مستقیم گرافی استفاده می‌کنه تا برای سایت‌ها و فایل‌های محلی مثل XML، HTML، JSON، Markdown و چیزهای مشابه، پایپ‌لاین اسکرپینگ بسازه.

کافیه بگی چه اطلاعاتی رو می‌خوای استخراج کنی؛ بقیه‌اش رو خود کتابخونه برات انجام می‌ده.

## 🚀 یکپارچه‌سازی‌ها

ScrapeGraphAI خیلی راحت با فریم‌ورک‌ها و ابزارهای معروف وصل می‌شه تا توانایی اسکرپینگت رو بیشتر کنه. فرقی نداره با Python کار کنی یا Node.js، از فریم‌ورک‌های LLM استفاده کنی یا سراغ پلتفرم‌های no-code بری؛ اینجا برای همه‌شون گزینه‌های یکپارچه‌سازی آماده شده.

<p align="center">
  <a href="https://scrapegraphai.com">
    <img src="https://raw.githubusercontent.com/ScrapeGraphAI/.github/main/profile/assets/api_banner.png" alt="Web data extraction at scale? Try ScrapeGraphAI cloud" style="width: 100%;">
  </a>
</p>

اطلاعات بیشتر رو می‌تونی از این [لینک](https://scrapegraphai.com) ببینی.

**یکپارچه‌سازی‌ها**:
- **API**: [Documentation](https://docs.scrapegraphai.com/introduction)
- **SDKها**: [Python](https://docs.scrapegraphai.com/sdks/python)، [Node](https://docs.scrapegraphai.com/sdks/javascript)
- **فریم‌ورک‌های LLM**: [Langchain](https://docs.scrapegraphai.com/integrations/langchain)، [Llama Index](https://docs.scrapegraphai.com/integrations/llamaindex)، [Crew.ai](https://docs.scrapegraphai.com/integrations/crewai)، [Agno](https://docs.scrapegraphai.com/integrations/agno)، [CamelAI](https://github.com/camel-ai/camel)
- **فریم‌ورک‌های Low-code**: [Pipedream](https://pipedream.com/apps/scrapegraphai)، [Bubble](https://bubble.io/plugin/scrapegraphai-1745408893195x213542371433906180)، [Zapier](https://zapier.com/apps/scrapegraphai/integrations)، [n8n](http://localhost:5001/dashboard)، [Dify](https://dify.ai)، [Toolhouse](https://app.toolhouse.ai/mcp-servers/scrapegraph_smartscraper)
- **MCP server**:  [Link](https://smithery.ai/server/@ScrapeGraphAI/scrapegraph-mcp)

## 🚀 نصب سریع

صفحه مرجع Scrapegraph-ai توی صفحه رسمی PyPI موجوده: [pypi](https://pypi.org/project/scrapegraphai/).

```bash
pip install scrapegraphai

# IMPORTANT (for fetching websites content)
playwright install
```

**نکته**: بهتره این کتابخونه رو داخل یک virtual environment نصب کنی تا با کتابخونه‌های دیگه تداخل پیدا نکنه 🐱


## 💻 نحوه استفاده

چند پایپ‌لاین استاندارد برای اسکرپینگ وجود داره که می‌تونی باهاشون از یک سایت یا فایل محلی اطلاعات استخراج کنی.

رایج‌ترینش `SmartScraperGraph` هست؛ این پایپ‌لاین با گرفتن یک پرامپت از کاربر و یک URL منبع، اطلاعات رو از یک صفحه استخراج می‌کنه.


```python
from scrapegraphai.graphs import SmartScraperGraph

# Define the configuration for the scraping pipeline
graph_config = {
    "llm": {
        "model": "ollama/llama3.2",
        "model_tokens": 8192,
        "format": "json",
    },
    "verbose": True,
    "headless": False,
}

# Create the SmartScraperGraph instance
smart_scraper_graph = SmartScraperGraph(
    prompt="Extract useful information from the webpage, including a description of what the company does, founders and social media links",
    source="https://scrapegraphai.com/",
    config=graph_config
)

# Run the pipeline
result = smart_scraper_graph.run()

import json
print(json.dumps(result, indent=4))
```

> [!NOTE]
> برای OpenAI و مدل‌های دیگه، فقط کافیه تنظیمات llm رو عوض کنی!
> ```python
>graph_config = {
>    "llm": {
>        "api_key": "YOUR_OPENAI_API_KEY",
>        "model": "openai/gpt-4o-mini",
>    },
>    "verbose": True,
>    "headless": False,
>}
>```


خروجی چیزی شبیه یک دیکشنری مثل نمونه زیر می‌شه:

```python
{
    "description": "ScrapeGraphAI transforms websites into clean, organized data for AI agents and data analytics. It offers an AI-powered API for effortless and cost-effective data extraction.",
    "founders": [
        {
            "name": "",
            "role": "Founder & Technical Lead",
            "linkedin": "https://www.linkedin.com/in/perinim/"
        },
        {
            "name": "Marco Vinciguerra",
            "role": "Founder & Software Engineer",
            "linkedin": "https://www.linkedin.com/in/marco-vinciguerra-7ba365242/"
        },
        {
            "name": "Lorenzo Padoan",
            "role": "Founder & Product Engineer",
            "linkedin": "https://www.linkedin.com/in/lorenzo-padoan-4521a2154/"
        }
    ],
    "social_media_links": {
        "linkedin": "https://www.linkedin.com/company/101881123",
        "twitter": "https://x.com/scrapegraphai",
        "github": "https://github.com/ScrapeGraphAI/Scrapegraph-ai"
    }
}
```

پایپ‌لاین‌های دیگه‌ای هم هستن که می‌تونن از چند صفحه اطلاعات بگیرن، اسکریپت پایتون بسازن یا حتی فایل صوتی تولید کنن.

| Pipeline Name | توضیح |
|---|---|
| <span dir="ltr">SmartScraperGraph</span> | اسکرپر تک‌صفحه‌ای که فقط به پرامپت کاربر و یک منبع ورودی نیاز داره. |
| <span dir="ltr">SearchGraph</span> | اسکرپر چندصفحه‌ای که اطلاعات رو از n نتیجه اول یک موتور جست‌وجو استخراج می‌کنه. |
| <span dir="ltr">SpeechGraph</span> | اسکرپر تک‌صفحه‌ای که اطلاعات رو از یک سایت استخراج می‌کنه و یک فایل صوتی می‌سازه. |
| <span dir="ltr">ScriptCreatorGraph</span> | اسکرپر تک‌صفحه‌ای که اطلاعات رو از یک سایت استخراج می‌کنه و یک اسکریپت Python می‌سازه. |
| <span dir="ltr">SmartScraperMultiGraph</span> | اسکرپر چندصفحه‌ای که با یک پرامپت و یک لیست از منابع، از چند صفحه اطلاعات استخراج می‌کنه. |
| <span dir="ltr">ScriptCreatorMultiGraph</span> | ابزار چندصفحه‌ای که برای استخراج اطلاعات از چند صفحه و چند منبع، اسکریپت Python تولید می‌کنه. |

برای هرکدوم از این گراف‌ها، نسخه multi هم وجود داره. این نسخه اجازه می‌ده فراخوانی‌های LLM به‌صورت موازی انجام بشن.

می‌تونی از LLMهای مختلف از طریق API استفاده کنی؛ مثل **OpenAI**، **Groq**، **Azure**، **Gemini**، **MiniMax** و موارد دیگه. همین‌طور می‌تونی با **Ollama** از مدل‌های محلی هم استفاده کنی.

اگه می‌خوای از مدل‌های محلی استفاده کنی، یادت باشه [Ollama](https://ollama.com/) رو نصب داشته باشی و مدل‌ها رو با دستور **ollama pull** دانلود کنی.


## 📖 مستندات

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1sEZBonBMGP44CtO6GQTwAlL0BGJXjtfd?usp=sharing)

مستندات ScrapeGraphAI رو می‌تونی از [اینجا](https://docs.scrapegraphai.com/introduction) ببینی.
