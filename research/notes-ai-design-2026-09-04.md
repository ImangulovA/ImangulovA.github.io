# Ресерч: различия дизайна у разных ИИ + open source схемы дизайна
Дата: 2026-09-04. Всё ниже — пересказ чужих публикаций, без моего собственного анализа.

## 1. Есть ли у моделей узнаваемый «почерк» в дизайне

### Да, но только у Claude это описано детально
Самый заметный источник — Kyle Chayka, The New Yorker («The A.I.-Design Aesthetic That's Taking Over the Internet»), краткая версия у него в Substack.
Приметы «клодовского» стиля, которые он перечисляет:
- бежевые/кремовые фоны, ржаво-оранжевые (терракота) акценты;
- крупные засечные шрифты, курсив для выделения;
- подзаголовки с разряженным трекингом (letter-spacing);
- бегущие строки / тикер-бары как у кабельных новостей;
- дашборд-элементы: много скруглённых прямоугольных обводок с неоновым свечением (наблюдение дизайнера David McGillivray);
- «слегка перекошенные» приглушённые mid-century цвета (Celine Nguyen).
Важная деталь: сам Anthropic в своей документации пишет, что у модели «сильные дизайнерские инстинкты и устойчивый дефолтный house style», и этот дефолт совпадает с брендом Anthropic.
Числа, которые ходят по статьям: фон #faf9f5, акцент-коралл #cc785c, шрифт Copernicus (slab serif), тёмный #141413.

### Codex / GPT
Отдельного исследовательского разбора «стиля Codex» нет, есть сравнительные обзоры (Builder.io, XDA, Composio, MindStudio). Повторяющиеся утверждения:
- Codex по умолчанию «не имеет вкуса»: фронт функциональный, но безликий, отношения паддингов и spacing требуют второго прохода;
- типичная претензия к Codex-дизайну — мягкие градиенты, парящие панели, огромные скругления, драматичные тени, «Inter-and-purple vibe that screams an AI made this»;
- Claude Code чаще даёт результат, который можно шипить с минимальными правками; Codex сильнее там, где дизайн уже зафиксирован (реализация, PR, тесты, CI);
- в Figma-to-code тестах Claude сохраняет больше структуры и ассетов, Codex тратит в ~4 раза меньше токенов, но теряет тему и layout.
Отдельно: Codex «начинает делать хороший дизайн», только если дать ему design system, constraints и конкретные референсы.

### Gemini
Упоминается «визуальная подпись»: остатки Material 3, инфлексии Google Sans, мягкая пастельная палитра.

### Академическая часть
Есть работы по fingerprinting LLM — они про текст, не про дизайн, но метод тот же:
- «Detecting Stylistic Fingerprints of Large Language Models» (arXiv 2503.01659) — классификаторы различают Claude / Gemini / Llama / OpenAI;
- «Your Large Language Models Are Leaving Fingerprints» (ACL GenAIDetect 2025);
- «Invisible Traces: Hybrid Fingerprinting» (arXiv 2501.18712);
- «Fingerprinting AI Coding Agents on GitHub» (arXiv 2601.17406) — уже про агентов: у Cursor bullet-heavy описания, у Claude Code плотные комментарии.
То есть строгих peer-reviewed работ именно про *визуальный* дизайн-фингерпринт я не нашёл — только журналистика, блоги дизайнеров и бенчмарки.

### Контраргумент (важно)
Thomas Wiegold («Best LLM for frontend design? It's mostly vibes now») прогнал 4 брифа через несколько моделей одинаковыми промптами:
- на нейтральных брифах результаты почти неразличимы — все сходятся к «медиане»: тёмная тема, sans-serif, много воздуха, немного анимации;
- различия проявляются, когда бриф уводит от дефолта (например, «cute, bright and colourful»);
- разброс больше по надёжности (баги вёрстки), чем по стилю.
Т.е. «почерк» есть, но он слабее общего сходства.

### Инструменты-детекторы
impeccable.style/slop — детектор «AI slop» в вёрстке: 66 паттернов в 9 категориях (типографика, цвет, layout, motion, копирайт). Между моделями не различает. Их список примет: фиолетово-синие градиенты, cyan-on-dark, шрифты Inter/Geist/Space Grotesk/Instrument Serif, курсивный serif в герое, градиентный текст, цветная полоска-акцент слева на карточке («самый узнаваемый tell»), карточки внутри карточек, одинаковые сетки из трёх фича-карточек, big-number метрики, bounce-easing, marquee, обилие тире, «streamline / empower / enterprise-grade».

### Каталог дефолтов Claude Design
Репозиторий rohitg00/awesome-claude-design ведёт список того, что Claude Design штампует по умолчанию и что советуют выключать: тиловый акцент #16d5e6 везде, мигающие зелёные статус-точки, вложенные контейнеры, дженерик-serif заголовки (Tiempos-adjacent), декоративные левые полоски 4px, трёхколоночные сетки фич.

## 2. Open source схемы дизайна (аналоги нео-брутализма)

### Нео-брутализм: состояние
- neobrutalism.dev — исходный проект на shadcn/ui, по сообщениям больше не поддерживается.
- ekmas/neobrutalism-components — компоненты поверх shadcn/ui (~5.2k звёзд).
- RetroUI (retroui.dev) — сейчас позиционируется как основная замена: 50+ компонентов, 158+ блоков, React + Tailwind + Radix/Base UI, 7 тем через переменные shadcn.
- Порты: neobrutalism-vue, neobrutalism-svelte (на shadcn-svelte), ng-brutalism (Angular, signals, zoneless, Tailwind v4).

### Другие «схемы» с open source реализацией
- Пиксель / 8-бит: 8bitcn/ui (TheOrcDev, ~1.9k звёзд), pixelact-ui — оба поверх shadcn/ui.
- Glassmorphism: glasscn-ui (itsjavi), artyhoo/shadcn-glass-ui-library (59 компонентов, 3 темы).
- Ретро-ОС и терминал: 98.css, XP.css, 7.css, NES.css, PSone.css, TuiCss (MS-DOS), terminal.css. Сводный список — matt-auckland/retro-css.
- Вейпорвейв: torch2424/aesthetic-css.
- Общий каталог: troxler/awesome-css-frameworks.

### Готовые «эстетические семейства» как промпт-схемы
awesome-claude-design группирует 9 визуальных семейств с референсами — это фактически готовый список стилевых направлений на замену нео-брутализму:
1. Editorial Minimalism (Linear, Stripe, Vercel)
2. Terminal-Core (моноширинный, фосфорные цвета на тёмном; Ollama, Warp)
3. Warm Editorial (терракота, крем, глина; Anthropic, Notion)
4. Data-Dense Pro (графики, плотный spacing; ClickHouse, PostHog)
5. Cinematic Dark (RunwayML, NVIDIA)
6. Playful Color (Figma, Duolingo)
7. Glass / Soft-Futurism (Apple, Arc)
8. Neon Brutalist (The Verge, Pitchfork)
9. Cult/Indie (Criterion, A24)

voltagent/awesome-design-md — 73+ готовых DESIGN.md, снятых с реальных брендовых сайтов (Linear, Stripe, Notion, Supabase, Nike, Tesla, ретро-веб вроде Dell 1996 и Nintendo 2001). Кладётся в проект как контекст для агента. Модель-агностично, отдельных папок под Claude/GPT/Gemini нет.

## 3. Бенчмарки, если нужны цифры
- Design Arena (designarena.ai) — слепое парное голосование по одинаковому промпту, Elo-лидерборды по категориям: сайты, UI-компоненты, геймдев, дата-виз, 3D.
- WebDev Arena — то же для фронтенд-задач.

## Источники
- https://kylechayka.substack.com/p/the-generic-style-of-ai-web-design
- https://www.925studios.co/blog/ai-slop-design-tells
- https://impeccable.style/slop/
- https://www.builder.io/blog/codex-vs-claude-code
- https://www.xda-developers.com/codex-technically-better-than-claude-code-stopped-using-it-for-one-specific-reason/
- https://open-design.ai/agents/codex-design/
- https://thomas-wiegold.com/blog/best-llm-frontend-design/
- https://arxiv.org/html/2503.01659v1
- https://aclanthology.org/2025.genaidetect-1.6.pdf
- https://arxiv.org/html/2601.17406v1
- https://github.com/rohitg00/awesome-claude-design
- https://github.com/voltagent/awesome-design-md
- https://retroui.dev/blog/neobrutalism-dev-alternative
- https://www.neobrutalism.dev/docs
- https://github.com/TheOrcDev/8bitcn-ui
- https://github.com/pixelact-ui/pixelact-ui
- https://github.com/artyhoo/shadcn-glass-ui-library
- https://github.com/matt-auckland/retro-css
- https://github.com/torch2424/aesthetic-css
- https://github.com/nostalgic-css/NES.css
- https://github.com/troxler/awesome-css-frameworks
- https://www.designarena.ai/leaderboard/code
