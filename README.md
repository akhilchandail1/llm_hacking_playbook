# The LLM Hacking Playbook

A curated roadmap of hands-on labs, readings and tools for learning to **attack and defend LLM applications**: prompt injection, indirect injection, data exfiltration, agent abuse and guardrails.

Work through it in order: understand the risks, practise on safe targets, learn the attack techniques, then automate testing and defend.

> **Use responsibly.** For education and authorised testing only. Attack the labs provided, your own systems, or systems where you have written permission.

## Contents
- [30-day plan](#30-day-plan)
- [Hands-on labs](#hands-on-labs)
- [Readings and videos](#readings-and-videos)
- [Tools](#tools)
- [Notes](#notes)

## 30-day plan

| When | Focus | What to do | Time |
|---|---|---|---|
| **Week 1** | Foundations and first wins | Read: Adversarial Prompting guide, OWASP Top 10 for LLM Apps, Simon Willison's article. Play: Gandalf (all levels) and Prompt Airlines. | ~ 6 hrs |
| **Week 2** | Structured practice | Work through PortSwigger's LLM attack labs, then Immersive Labs and GPT Prompt Attack. Keep the Prompt Injection Cheat Sheet open. | ~ 8 hrs |
| **Week 3** | Indirect injection, RAG and agents | Read the Greshake research and the Embrace The Red exfiltration post. Attack Pokébot (RAG). Optional: self-host Damn Vulnerable LLM Agent with the video walkthrough. | ~ 8 hrs |
| **Week 4** | Automate and defend | Run garak and promptmap against a test app. Add LLM Guard to it. Read NVIDIA's defence article and the AI Village threat-modeling post. Try your first Crucible challenge. | ~ 8 hrs |
| **Capstone** | Prove it | Write a one-page report: pick one lab, document the attack, why it worked and how you would fix it. Great portfolio or LinkedIn material. | ~ 3 hrs |

## Hands-on labs

Beginner browser games first, self-hosted and CTF-grade targets last. 🔑 = needs an OpenAI API key.

| Lab | Level | What you will practise | Priority |
|---|---|---|---|
| [Gandalf by Lakera](https://gandalf.lakera.ai/) ([Walkthrough (blog)](https://hacking-and-security.cc/llm-hacking-with-gandalf/))<br>*Browser game* | Beginner | Trick a guarded chatbot into revealing a secret password across progressively harder levels. The best first taste of prompt injection and filter bypass. | ⭐ Must try |
| [Prompt Airlines by Wiz](https://promptairlines.com/)<br>*Browser challenge* | Beginner | Manipulate an airline customer-service chatbot into doing what it shouldn't. Realistic business-bot scenario with a clear win condition. | ⭐ Must try |
| [PortSwigger Web Security Academy: LLM attacks](https://portswigger.net/web-security/llm-attacks)<br>*Guided labs* | Beginner | Structured learning path on LLM attacks: excessive agency, insecure output handling and indirect prompt injection, with hands-on labs from the makers of Burp Suite. | ⭐ Must try |
| [Immersive Labs: Prompt Injection](https://prompting.ai.immersivelabs.com/)<br>*Browser challenges* | Beginner | Progressive prompt-injection exercises against guarded AI models. Good for checking that your technique holds up as defences get stronger. | ⭐ Must try |
| [GPT Prompt Attack](https://gpa.43z.one/)<br>*Browser game* | Beginner | Practise attacking and defending system prompts. Particularly useful for understanding how system prompts get leaked and how to harden them. | Recommended |
| [DeepLearning.AI: Red Teaming LLM Applications](https://learn.deeplearning.ai/courses/red-teaming-llm-applications)<br>*Short course* | Beginner | Learn a repeatable red-teaming workflow for LLM apps: finding failure modes, building test cases and evaluating results. | Recommended |
| [Pokébot: Damn Vulnerable GenAI RAG App](https://huggingface.co/spaces/detoxioai/Pokebot)<br>*Hosted app (Hugging Face)* | Intermediate | Attack a retrieval-augmented (RAG) chatbot. The pick if you want to understand document poisoning and data-leak issues specific to RAG. | Recommended |
| [Damn Vulnerable LLM Agent (WithSecure)](https://github.com/WithSecureLabs/damn-vulnerable-llm-agent) 🔑 ([Walkthrough (YouTube)](https://www.youtube.com/watch?v=43qfHaKh0Xk))<br>*Self-hosted app* | Intermediate | Exploit a ReAct/LangChain-style agent via prompt injection and tool abuse. Shows what changes when an LLM can call tools. | Optional |
| [Damn Vulnerable LLM Project](https://github.com/harishsg993010/DamnVulnerableLLMProject) 🔑 ([Walkthrough (article)](https://infosecwriteups.com/art-of-hacking-llm-apps-a22cf60a523b))<br>*Self-hosted app* | Intermediate | Run your own deliberately vulnerable LLM app and practise common attacks in a safe sandbox. | Optional |
| [Crucible by Dreadnode](https://crucible.dreadnode.io/)<br>*CTF platform* | Intermediate to Advanced | AI red-teaming CTF challenges, including ones originating from DEF CON. Where you test yourself once the basics click. | ⭐ Must try |
| [DEF CON CTF 2023 Quals: AI challenge](https://github.com/Nautilus-Institute/quals-2023/tree/main/pawan_gupta)<br>*Self-hosted CTF* | Advanced | Source for a DEF CON qualifier challenge with an LLM component. For experienced CTF players who want a real competition-grade target. | Optional |

## Readings and videos


### 1 - Foundations

| Resource | Type | Level | What you will get |
|---|---|---|---|
| [Adversarial Prompting (Prompt Engineering Guide)](https://www.promptingguide.ai/risks/adversarial) | Guide | Beginner | Clear overview of prompt injection, prompt leaking and jailbreaking with examples. Read this before touching any lab. |
| [OWASP Top 10 for LLM Applications (v1.0)](https://llmtop10.com/) | Framework | Beginner | The original industry-standard list of the ten biggest LLM application risks. Gives you the vocabulary used in every security conversation. |
| [OWASP Top 10 for LLM Applications: latest edition](https://genai.owasp.org/llm-top-10/) | Framework | Beginner | The updated list from the OWASP GenAI Security Project. Read alongside v1.0 to see how the threat picture has shifted. |
| [Prompt injection: what's the worst that can happen?](https://simonwillison.net/2023/Apr/14/worst-that-can-happen/) | Article | Beginner | Simon Willison's plain-English explanation of why prompt injection is hard to fix and what real damage looks like once an LLM has tools. |
| [PIPE: Prompt Injection Primer for Engineers](https://github.com/jthack/PIPE) | Primer (GitHub) | Beginner | Engineer-friendly primer covering the mechanics of prompt injection and common mitigations. |
| [Attacking LLMs: Prompt Injection](https://www.youtube.com/watch?v=Sv5OLj2nVAQ) | Video | Beginner | Video walkthrough of prompt-injection attacks. A good watch if you learn better visually. |
| [Prompt Injection Cheat Sheet](https://blog.seclify.com/prompt-injection-cheat-sheet/) | Cheat sheet | Beginner | Quick reference of injection patterns and how each manipulates a model. Keep it open while doing the labs. |
| [Payloads for Attacking Large Language Models (PALLMs)](https://github.com/mik0w/pallms) | Payload list (GitHub) | Intermediate | Collection of payloads for testing LLM apps. Use it as a starting wordlist for your own tests. |
| [Adversarial Attacks on LLMs (Lilian Weng)](https://lilianweng.github.io/posts/2023-10-25-adv-attack-llm/) | Deep-dive article | Intermediate | Research-level survey of how adversarial attacks work on language models, including jailbreak techniques. Dense but worth it. |

### 2 - Attack deep-dives

| Resource | Type | Level | What you will get |
|---|---|---|---|
| [Indirect Prompt Injection Threats (Greshake et al.)](https://greshake.github.io/) | Research project | Intermediate | The research that defined indirect prompt injection: attackers hiding instructions in content an LLM later reads. |
| [How We Broke LLMs: Indirect Prompt Injection](https://kai-greshake.de/posts/llm-malware/) | Article | Intermediate | Companion write-up to the research above, showing practical attack scenarios against LLM-integrated apps. |
| [Invisible Indirect Injection: a puzzle for ChatGPT](https://kai-greshake.de/posts/puzzle-22745/) | Article / puzzle | Intermediate | A hands-on puzzle showing how instructions can be hidden in content so the user never sees them. |
| [Inject My PDF: prompt injection for your résumé](https://kai-greshake.de/posts/inject-my-pdf/) | Article | Intermediate | Demonstrates indirect injection through a document an AI screening tool reads. A memorable real-world example. |
| [Prompt Injection in LLM Agents (ReAct, LangChain)](https://www.youtube.com/watch?v=43qfHaKh0Xk) | Video | Intermediate | Video showing injection against tool-using agents. Pairs directly with the Damn Vulnerable LLM Agent lab. |
| [ChatGPT plugins: data exfiltration via images and cross-plugin request forgery](https://embracethered.com/blog/posts/2023/chatgpt-webpilot-data-exfil-via-markdown-injection/) | Article | Intermediate | How markdown image rendering can leak chat data, and how one plugin can be abused to trigger another. |
| [Prompt injection with control characters in ChatGPT (Dropbox)](https://dropbox.tech/machine-learning/prompt-injection-with-control-characters-openai-chatgpt-llm) | Article | Intermediate | Shows how unusual control characters can derail model behaviour and bypass assumptions in input handling. |
| [LLM causing self-XSS](https://hackstery.com/2023/07/10/llm-causing-self-xss/) | Article | Intermediate | What happens when model output is rendered unsafely in a web page. A classic insecure-output-handling case. |
| [Hacking Auto-GPT and escaping its Docker container](https://positive.security/blog/auto-gpt-rce) | Article | Advanced | Walks through chaining prompt injection into remote code execution against an autonomous agent. |
| [Jailbreaking GPT-4's code interpreter](https://www.lesswrong.com/posts/KSroBnxCHodGmPPJ8/jailbreaking-gpt-4-s-code-interpreter) | Article | Advanced | Explores what an LLM with a code sandbox can be pushed to do, and where the boundaries lie. |
| [PoisonGPT: hiding a tampered LLM on Hugging Face](https://blog.mithrilsecurity.io/poisongpt-how-we-hid-a-lobotomized-llm-on-hugging-face-to-spread-fake-news/) | Article | Intermediate | A supply-chain case study: how a modified model can spread misinformation while looking legitimate. |

### 3 - Defence & risk

| Resource | Type | Level | What you will get |
|---|---|---|---|
| [Securing LLM systems against prompt injection (NVIDIA)](https://developer.nvidia.com/blog/securing-llm-systems-against-prompt-injection/) | Article | Intermediate | Practical defensive design patterns for LLM applications from NVIDIA's security team. |
| [A framework to securely use LLMs in companies](https://boringappsec.substack.com/p/edition-21-a-framework-to-securely) | Article | Beginner | Boring AppSec's framework for rolling out LLMs inside an organisation without losing control of risk. |
| [Threat modeling LLM applications (AI Village)](https://aivillage.org/large%20language%20models/threat-modeling-llm/) | Article | Intermediate | How to apply threat modeling to an LLM app: trust boundaries, assets and likely attack paths. |
| [Understanding the risks of deploying LLMs in your enterprise](https://www.moveworks.com/us/en/resources/blog/risks-of-deploying-llms-in-your-enterprise) | Article | Beginner | Business-oriented overview of enterprise LLM risks. Useful for explaining the problem to non-security stakeholders. |
| [The AI Attack Surface Map v1.0 (Daniel Miessler)](https://danielmiessler.com/p/the-ai-attack-surface-map-v1-0/) | Article | Beginner | A map of where in an AI system things can go wrong: models, prompts, data, tools and users. |
| [OWASP Machine Learning Security Top 10](https://mltop10.info/) | Framework | Intermediate | Companion to the LLM list, covering classic ML risks such as data poisoning and model theft. |

### 4 - Keep following

| Resource | Type | Level | What you will get |
|---|---|---|---|
| [LLM Security (llmsecurity.net)](https://llmsecurity.net/) | News & paper tracker | All levels | Running feed of LLM security papers and news. Good for staying current. |
| [Awesome LLM Security](https://github.com/corca-ai/awesome-llm-security) | Curated list (GitHub) | All levels | Large community-maintained collection of papers, tools and write-ups. |
| [Embrace The Red](https://embracethered.com/blog/index.html) | Blog | All levels | Ongoing research on real-world attacks against AI products. Follow it for new techniques. |
| [OWASP AI Security Initiatives](https://owaspai.org/) | Community hub | All levels | OWASP's hub for AI security guidance, standards and projects. |

## Tools

Only run these against systems you own or have written permission to test.


### Test your app

| Tool | What it does | Best for |
|---|---|---|
| [garak (LLM vulnerability scanner)](https://github.com/leondz/garak/) | Probes a model for weaknesses (injection, leakage, toxicity and more) in an automated scan, like nmap for LLMs. | First automated scan of any model |
| [promptmap](https://github.com/utkusen/promptmap) | Sends a battery of prompt-injection attacks at your own system prompt to see which ones succeed. | Checking a custom chatbot's system prompt |
| [ps-fuzz (Prompt Security)](https://github.com/prompt-security/ps-fuzz) | Fuzzes your GenAI app's system prompt with attacks and rates how well it holds up. | Hardening a system prompt before launch |
| [HouYi](https://github.com/LLMSecurity/HouYi) | Automated prompt-injection attack framework from academic research on LLM-integrated applications. | Studying how automated injection works |
| [LLMFuzzer](https://github.com/mnns/LLMFuzzer) | Fuzzing framework aimed at testing LLMs through their APIs. | API-level robustness testing |
| [Plexiglass](https://github.com/safellama/plexiglass) | Toolkit for testing and monitoring LLMs against adversarial inputs. | Lightweight adversarial testing |

### Test and defend

| Tool | What it does | Best for |
|---|---|---|
| [Purple Llama (Meta)](https://github.com/facebookresearch/PurpleLlama) | Meta's umbrella project for LLM safety: includes benchmarks and safeguard models for evaluating and filtering model behaviour. | Evaluating model safety and cyber risk |

### Defend

| Tool | What it does | Best for |
|---|---|---|
| [LLM Guard (Protect AI)](https://github.com/protectai/llm-guard) | Open-source toolkit with input and output scanners to sanitise prompts and responses. | Adding guardrails to a live app |
| [Rebuff (Protect AI)](https://github.com/protectai/rebuff) | Prompt-injection detector using multiple layers of checks. Worth studying even if you use something else in production. | Learning layered detection |
| [Vigil](https://github.com/deadbits/vigil-llm) | Scanner that flags prompt injections, jailbreaks and risky inputs using several detection methods. | Detecting suspicious prompts |
| [Lakera Guard playground](https://platform.lakera.ai/playground) | Try a commercial prompt-injection guard in the browser to see how a production defence behaves. | Comparing defences against your own attacks |

### Research

| Tool | What it does | Best for |
|---|---|---|
| [BITE: textual backdoor attacks](https://github.com/INK-USC/BITE) | Research code for planting backdoors in text models through iterative trigger injection. | Understanding model backdoors |

## Notes
- All links go to third-party sites and may move or change over time. Open an issue or pull request if you find one that is broken.
- Many readings date from 2023. The core ideas still apply, but specific exploits may have been patched.

## Contributing
Suggestions are welcome. Open a pull request adding a resource with a one-line description of what a learner gets from it.

## Want the full version?
A formatted PDF edition and an Excel progress tracker are available on [Topmate](https://topmate.io/YOUR_USERNAME).
