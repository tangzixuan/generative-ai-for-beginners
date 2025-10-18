<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "578a2d20d79cbe5a33eac32d4eabb9b0",
  "translation_date": "2025-10-17T22:17:06+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "bg"
}
-->
# Започване на курса

Много сме развълнувани, че започвате този курс и нямаме търпение да видим какво ще създадете с Генеративния AI!

За да гарантираме вашия успех, тази страница описва стъпките за настройка, техническите изисквания и къде да потърсите помощ, ако е необходимо.

## Стъпки за настройка

За да започнете курса, трябва да изпълните следните стъпки.

### 1. Форкнете това хранилище

[Форкнете цялото хранилище](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) във вашия собствен GitHub акаунт, за да можете да променяте кода и да изпълнявате предизвикателствата. Можете също така да [звездите (🌟) това хранилище](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst), за да го намирате и свързаните с него хранилища по-лесно.

### 2. Създайте Codespace

За да избегнете проблеми с зависимостите при изпълнение на кода, препоръчваме да стартирате курса в [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst).

Във вашия форк: **Code -> Codespaces -> New on main**

![Диалогов прозорец с бутони за създаване на Codespace](../../../00-course-setup/images/who-will-pay.webp)

#### 2.1 Добавете секрет

1. ⚙️ Икона на зъбно колело -> Command Pallete -> Codespaces : Manage user secret -> Add a new secret.
2. Име OPENAI_API_KEY, поставете вашия ключ, Запазете.

### 3. Какво следва?

| Искам да…           | Отиди на…                                                              |
|---------------------|-------------------------------------------------------------------------|
| Започна урок 1      | [`01-introduction-to-genai`](../01-introduction-to-genai/README.md)     |
| Работя офлайн       | [`setup-local.md`](02-setup-local.md)                                   |
| Настроя доставчик на LLM | [`providers.md`](03-providers.md)                                        |
| Срещна други обучаващи се | [Присъединете се към нашия Discord](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)   |

## Отстраняване на проблеми

| Симптом                                   | Решение                                                         |
|-------------------------------------------|-----------------------------------------------------------------|
| Изграждането на контейнера е блокирано > 10 минути | **Codespaces ➜ “Rebuild Container”**                            |
| `python: command not found`               | Терминалът не се е свързал; кликнете **+** ➜ *bash*             |
| `401 Unauthorized` от OpenAI              | Грешен / изтекъл `OPENAI_API_KEY`                               |
| VS Code показва “Dev container mounting…” | Обновете раздела на браузъра—Codespaces понякога губи връзка    |
| Липсва ядро на Notebook                   | Меню на Notebook ➜ **Kernel ▸ Select Kernel ▸ Python 3**        |

   Unix-базирани системи:

   ```bash
   touch .env
   ```

   Windows:

   ```cmd
   echo . > .env
   ```

3. **Редактирайте файла `.env`**: Отворете файла `.env` в текстов редактор (например VS Code, Notepad++ или друг редактор). Добавете следния ред във файла, заменяйки `your_github_token_here` с вашия действителен GitHub токен:

   ```env
   GITHUB_TOKEN=your_github_token_here
   ```

4. **Запазете файла**: Запазете промените и затворете текстовия редактор.

5. **Инсталирайте `python-dotenv`**: Ако все още не сте го направили, ще трябва да инсталирате пакета `python-dotenv`, за да заредите променливите на средата от файла `.env` във вашето Python приложение. Можете да го инсталирате с `pip`:

   ```bash
   pip install python-dotenv
   ```

6. **Заредете променливите на средата във вашия Python скрипт**: Във вашия Python скрипт използвайте пакета `python-dotenv`, за да заредите променливите на средата от файла `.env`:

   ```python
   from dotenv import load_dotenv
   import os

   # Load environment variables from .env file
   load_dotenv()

   # Access the GITHUB_TOKEN variable
   github_token = os.getenv("GITHUB_TOKEN")

   print(github_token)
   ```

Това е всичко! Успешно създадохте файл `.env`, добавихте вашия GitHub токен и го заредихте във вашето Python приложение.

## Как да стартирате локално на вашия компютър

За да стартирате кода локално на вашия компютър, ще трябва да имате инсталирана някаква версия на [Python](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst).

След това, за да използвате хранилището, трябва да го клонирате:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

След като всичко е изтеглено, можете да започнете!

## Допълнителни стъпки

### Инсталиране на Miniconda

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst) е лек инсталатор за инсталиране на [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, както и няколко пакета.
Conda сама по себе си е мениджър на пакети, който улеснява настройката и превключването между различни Python [**виртуални среди**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst) и пакети. Тя също е полезна за инсталиране на пакети, които не са налични чрез `pip`.

Можете да следвате [ръководството за инсталиране на MiniConda](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst), за да я настроите.

С инсталиран Miniconda, трябва да клонирате [хранилището](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst) (ако все още не сте го направили).

След това трябва да създадете виртуална среда. За да направите това с Conda, създайте нов файл за среда (_environment.yml_). Ако следвате курса в Codespaces, създайте този файл в директорията `.devcontainer`, тоест `.devcontainer/environment.yml`.

Попълнете файла за среда със следния код:

```yml
name: <environment-name>
channels:
  - defaults
  - microsoft
dependencies:
  - python=<python-version>
  - openai
  - python-dotenv
  - pip
  - pip:
      - azure-ai-ml
```

Ако срещнете грешки при използването на conda, можете ръчно да инсталирате библиотеките на Microsoft AI, използвайки следната команда в терминала.

```
conda install -c microsoft azure-ai-ml
```

Файлът за среда определя необходимите зависимости. `<environment-name>` се отнася до името, което искате да използвате за вашата Conda среда, а `<python-version>` е версията на Python, която искате да използвате, например `3` е последната основна версия на Python.

След като това е направено, можете да създадете вашата Conda среда, като изпълните командите по-долу в командния ред/терминала:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

Прегледайте [ръководството за Conda среди](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst), ако срещнете някакви проблеми.

### Използване на Visual Studio Code с разширението за Python

Препоръчваме използването на редактора [Visual Studio Code (VS Code)](https://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) с инсталирано [разширение за Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) за този курс. Това обаче е препоръка, а не задължително изискване.

> **Забележка**: Когато отворите хранилището на курса в VS Code, имате възможност да настроите проекта в контейнер. Това е възможно благодарение на [специалната директория `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst), намираща се в хранилището на курса. Повече за това по-късно.

> **Забележка**: След като клонирате и отворите директорията в VS Code, автоматично ще ви предложи да инсталирате разширение за Python.

> **Забележка**: Ако VS Code ви предложи да отворите хранилището в контейнер, откажете тази заявка, за да използвате локално инсталираната версия на Python.

### Използване на Jupyter в браузъра

Можете също така да работите по проекта, използвайки [Jupyter среда](https://jupyter.org?WT.mc_id=academic-105485-koreyst) директно в браузъра. Както класическият Jupyter, така и [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) предоставят приятна среда за разработка с функции като автоматично довършване, подчертаване на код и др.

За да стартирате Jupyter локално, отидете до терминала/командния ред, навигирайте до директорията на курса и изпълнете:

```bash
jupyter notebook
```

или

```bash
jupyterhub
```

Това ще стартира Jupyter инстанция и URL за достъп ще бъде показан в прозореца на командния ред.

След като достъпите URL, трябва да видите структурата на курса и да можете да навигирате до всеки файл `*.ipynb`. Например, `08-building-search-applications/python/oai-solution.ipynb`.

### Стартиране в контейнер

Алтернатива на настройката на всичко на вашия компютър или Codespace е използването на [контейнер](../../../00-course-setup/<https:/en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst>). Специалната папка `.devcontainer` в хранилището на курса прави възможно VS Code да настрои проекта в контейнер. Извън Codespaces, това ще изисква инсталиране на Docker и, честно казано, включва малко повече работа, така че препоръчваме това само на тези с опит в работата с контейнери.

Един от най-добрите начини да запазите вашите API ключове сигурни при използване на GitHub Codespaces е чрез използване на Codespace Secrets. Моля, следвайте [ръководството за управление на тайни в Codespaces](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst), за да научите повече за това.

## Уроци и технически изисквания

Курсът включва 6 концептуални урока и 6 урока с код.

За уроците с код използваме Azure OpenAI Service. Ще ви е необходим достъп до Azure OpenAI Service и API ключ, за да изпълните този код. Можете да кандидатствате за достъп, като [попълните тази заявка](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst).

Докато чакате вашата заявка да бъде обработена, всеки урок с код включва и файл `README.md`, където можете да видите кода и резултатите.

## Използване на Azure OpenAI Service за първи път

Ако за първи път работите с Azure OpenAI Service, моля, следвайте това ръководство за [създаване и разполагане на ресурс за Azure OpenAI Service.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)

## Използване на OpenAI API за първи път

Ако за първи път работите с OpenAI API, моля, следвайте ръководството за [създаване и използване на интерфейса.](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)

## Срещнете други обучаващи се

Създадохме канали в нашия официален [AI Community Discord сървър](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst), за да се срещнете с други обучаващи се. Това е чудесен начин да се свържете с други предприемачи, създатели, студенти и всеки, който иска да се развива в Генеративния AI.

[![Присъединете се към Discord канала](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

Екипът на проекта също ще бъде на този Discord сървър, за да помага на обучаващите се.

## Допринасяне

Този курс е инициатива с отворен код. Ако видите области за подобрение или проблеми, моля, създайте [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst) или регистрирайте [GitHub проблем](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst).

Екипът на проекта ще следи всички приноси. Допринасянето към отворен код е невероятен начин да изградите кариера в Генеративния AI.

Повечето приноси изискват да се съгласите с Лицензионно споразумение за приносител (CLA), което декларира, че имате право и действително предоставяте права за използване на вашия принос. За подробности посетете [уебсайта за CLA, Лицензионно споразумение за приносител](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst).

Важно: когато превеждате текст в това хранилище, моля, уверете се, че не използвате машинен превод. Ще проверим преводите чрез общността, така че моля, доброволствайте за преводи само на езици, на които сте компетентни.

Когато изпратите pull request, CLA-бот автоматично ще определи дали трябва да предоставите CLA и ще украси PR съответно (например, етикет, коментар). Просто следвайте инструкциите, предоставени от бота. Ще трябва да направите това само веднъж за всички хранилища, използващи нашия CLA.

Този проект е приел [Кодекса за поведение на Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst). За повече информация прочетете FAQ за Кодекса за поведение или се свържете с [Email opencode](opencode@microsoft.com) за допълнителни въпроси или коментари.

## Да започваме!
Сега, след като сте изпълнили необходимите стъпки за завършване на този курс, нека започнем с [въведение в Генеративния AI и LLMs](../01-introduction-to-genai/README.md?WT.mc_id=academic-105485-koreyst).

---

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI услуга за превод [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи може да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Не носим отговорност за недоразумения или погрешни интерпретации, произтичащи от използването на този превод.