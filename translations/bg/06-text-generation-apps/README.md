<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df027997f1448323d6159b78a1b669bf",
  "translation_date": "2025-10-17T22:14:07+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "bg"
}
-->
# Създаване на приложения за генериране на текст

[![Създаване на приложения за генериране на текст](../../../translated_images/06-lesson-banner.a5c629f990a636c852353c5533f1a6a218ece579005e91f96339d508d9cf8f47.bg.png)](https://youtu.be/0Y5Luf5sRQA?si=t_xVg0clnAI4oUFZ)

> _(Кликнете върху изображението по-горе, за да гледате видеото на този урок)_

Досега в тази учебна програма сте видели основни концепции като подсказки и дори цяла дисциплина, наречена "инженеринг на подсказки". Много инструменти, с които можете да взаимодействате, като ChatGPT, Office 365, Microsoft Power Platform и други, ви позволяват да използвате подсказки, за да постигнете нещо.

За да добавите такова преживяване към приложение, трябва да разберете концепции като подсказки, завършвания и да изберете библиотека, с която да работите. Точно това ще научите в тази глава.

## Въведение

В тази глава ще:

- Научите за библиотеката openai и нейните основни концепции.
- Създадете приложение за генериране на текст, използвайки openai.
- Разберете как да използвате концепции като подсказка, температура и токени, за да създадете приложение за генериране на текст.

## Цели на обучението

В края на този урок ще можете:

- Да обясните какво представлява приложение за генериране на текст.
- Да създадете приложение за генериране на текст, използвайки openai.
- Да конфигурирате приложението си да използва повече или по-малко токени и да променяте температурата за разнообразен изход.

## Какво представлява приложение за генериране на текст?

Обикновено, когато създавате приложение, то има някакъв интерфейс като следните:

- Базирано на команди. Конзолните приложения са типични приложения, където въвеждате команда и тя изпълнява задача. Например, `git` е приложение, базирано на команди.
- Потребителски интерфейс (UI). Някои приложения имат графични потребителски интерфейси (GUIs), където кликате върху бутони, въвеждате текст, избирате опции и други.

### Ограничения на конзолните и UI приложения

Сравнете го с приложение, базирано на команди, където въвеждате команда:

- **Ограничено е**. Не можете просто да въведете всяка команда, само тези, които приложението поддържа.
- **Специфично за език**. Някои приложения поддържат много езици, но по подразбиране приложението е създадено за конкретен език, дори ако можете да добавите поддръжка за повече езици.

### Предимства на приложенията за генериране на текст

Как тогава приложението за генериране на текст е различно?

В приложение за генериране на текст имате повече гъвкавост, не сте ограничени до набор от команди или конкретен входен език. Вместо това можете да използвате естествен език, за да взаимодействате с приложението. Друго предимство е, че вече взаимодействате с източник на данни, който е обучен върху огромен корпус от информация, докато традиционното приложение може да бъде ограничено до това, което е в база данни.

### Какво мога да създам с приложение за генериране на текст?

Има много неща, които можете да създадете. Например:

- **Чатбот**. Чатбот, който отговаря на въпроси за теми като вашата компания и нейните продукти, може да бъде добро решение.
- **Помощник**. LLMs са отлични за задачи като обобщаване на текст, извличане на прозрения от текст, създаване на текст като автобиографии и други.
- **Асистент за код**. В зависимост от езиковия модел, който използвате, можете да създадете асистент за код, който ви помага да пишете код. Например, можете да използвате продукт като GitHub Copilot, както и ChatGPT, за да ви помогне да пишете код.

## Как да започна?

Трябва да намерите начин да се интегрирате с LLM, което обикновено включва следните два подхода:

- Използване на API. Тук създавате уеб заявки с вашата подсказка и получавате генериран текст обратно.
- Използване на библиотека. Библиотеките помагат да се капсулират API заявките и ги правят по-лесни за използване.

## Библиотеки/SDKs

Има няколко добре познати библиотеки за работа с LLMs като:

- **openai**, тази библиотека улеснява свързването с вашия модел и изпращането на подсказки.

След това има библиотеки, които работят на по-високо ниво като:

- **Langchain**. Langchain е добре позната и поддържа Python.
- **Semantic Kernel**. Semantic Kernel е библиотека от Microsoft, която поддържа езиците C#, Python и Java.

## Първо приложение с openai

Нека видим как можем да създадем първото си приложение, какви библиотеки са ни необходими, колко усилия са нужни и т.н.

### Инсталиране на openai

Има много библиотеки за взаимодействие с OpenAI или Azure OpenAI. Възможно е да се използват множество програмни езици като C#, Python, JavaScript, Java и други. Избрахме да използваме Python библиотеката `openai`, така че ще използваме `pip`, за да я инсталираме.

```bash
pip install openai
```

### Създаване на ресурс

Трябва да изпълните следните стъпки:

- Създайте акаунт в Azure [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst).
- Получете достъп до Azure OpenAI. Отидете на [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) и поискайте достъп.

  > [!NOTE]
  > Към момента на писане трябва да кандидатствате за достъп до Azure OpenAI.

- Инсталирайте Python <https://www.python.org/>
- Създайте ресурс за Azure OpenAI Service. Вижте това ръководство за [създаване на ресурс](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst).

### Намерете API ключ и крайна точка

На този етап трябва да кажете на библиотеката `openai` кой API ключ да използва. За да намерите вашия API ключ, отидете в секцията "Keys and Endpoint" на вашия Azure OpenAI ресурс и копирайте стойността "Key 1".

![Keys and Endpoint ресурс в Azure Portal](https://learn.microsoft.com/azure/ai-services/openai/media/quickstarts/endpoint.png?WT.mc_id=academic-105485-koreyst)

Сега, когато сте копирали тази информация, нека инструктираме библиотеките да я използват.

> [!NOTE]
> Струва си да отделите вашия API ключ от кода си. Можете да направите това, като използвате променливи на средата.
>
> - Задайте променливата на средата `OPENAI_API_KEY` на вашия API ключ.
>   `export OPENAI_API_KEY='sk-...'`

### Конфигурация за Azure

Ако използвате Azure OpenAI, ето как да настроите конфигурацията:

```python
openai.api_type = 'azure'
openai.api_key = os.environ["OPENAI_API_KEY"]
openai.api_version = '2023-05-15'
openai.api_base = os.getenv("API_BASE")
```

Горе задаваме следното:

- `api_type` на `azure`. Това казва на библиотеката да използва Azure OpenAI, а не OpenAI.
- `api_key`, това е вашият API ключ, намерен в Azure Portal.
- `api_version`, това е версията на API, която искате да използвате. Към момента на писане, последната версия е `2023-05-15`.
- `api_base`, това е крайната точка на API. Можете да я намерите в Azure Portal до вашия API ключ.

> [!NOTE] > `os.getenv` е функция, която чете променливи на средата. Можете да я използвате, за да четете променливи на средата като `OPENAI_API_KEY` и `API_BASE`. Задайте тези променливи на средата във вашия терминал или като използвате библиотека като `dotenv`.

## Генериране на текст

Начинът за генериране на текст е чрез използване на класа `Completion`. Ето пример:

```python
prompt = "Complete the following: Once upon a time there was a"

completion = openai.Completion.create(model="davinci-002", prompt=prompt)
print(completion.choices[0].text)
```

В горния код създаваме обект за завършване и подаваме модела, който искаме да използваме, и подсказката. След това отпечатваме генерирания текст.

### Завършвания за чат

Досега сте видели как използваме `Completion` за генериране на текст. Но има друг клас, наречен `ChatCompletion`, който е по-подходящ за чатботове. Ето пример за използването му:

```python
import openai

openai.api_key = "sk-..."

completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
print(completion.choices[0].message.content)
```

Повече за тази функционалност в предстоящата глава.

## Упражнение - вашето първо приложение за генериране на текст

Сега, когато научихме как да настроим и конфигурираме openai, е време да създадем вашето първо приложение за генериране на текст. За да създадете вашето приложение, следвайте тези стъпки:

1. Създайте виртуална среда и инсталирайте openai:

   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install openai
   ```

   > [!NOTE]
   > Ако използвате Windows, въведете `venv\Scripts\activate` вместо `source venv/bin/activate`.

   > [!NOTE]
   > Намерете вашия Azure OpenAI ключ, като отидете на [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst), потърсите `Open AI`, изберете ресурса `Open AI` и след това изберете `Keys and Endpoint` и копирате стойността `Key 1`.

1. Създайте файл _app.py_ и въведете следния код:

   ```python
   import openai

   openai.api_key = "<replace this value with your open ai key or Azure OpenAI key>"

   openai.api_type = 'azure'
   openai.api_version = '2023-05-15'
   openai.api_base = "<endpoint found in Azure Portal where your API key is>"
   deployment_name = "<deployment name>"

   # add your completion code
   prompt = "Complete the following: Once upon a time there was a"
   messages = [{"role": "user", "content": prompt}]

   # make completion
   completion = openai.chat.completions.create(model=deployment_name, messages=messages)

   # print response
   print(completion.choices[0].message.content)
   ```

   > [!NOTE]
   > Ако използвате Azure OpenAI, трябва да зададете `api_type` на `azure` и да зададете `api_key` на вашия Azure OpenAI ключ.

   Трябва да видите изход, подобен на следния:

   ```output
    very unhappy _____.

   Once upon a time there was a very unhappy mermaid.
   ```

## Различни видове подсказки за различни задачи

Сега видяхте как да генерирате текст, използвайки подсказка. Вече имате програма, която работи и можете да я модифицирате и променяте, за да генерирате различни видове текст.

Подсказките могат да се използват за всякакви задачи. Например:

- **Генериране на вид текст**. Например, можете да генерирате поема, въпроси за тест и др.
- **Търсене на информация**. Можете да използвате подсказки, за да търсите информация, като например следния пример: "Какво означава CORS в уеб разработката?".
- **Генериране на код**. Можете да използвате подсказки, за да генерирате код, например разработване на регулярни изрази за валидиране на имейли или защо не генерирате цяла програма, като уеб приложение?

## По-практичен случай: генератор на рецепти

Представете си, че имате съставки у дома и искате да сготвите нещо. За това ви е необходима рецепта. Един начин да намерите рецепти е да използвате търсачка или можете да използвате LLM за това.

Можете да напишете подсказка като:

> "Покажи ми 5 рецепти за ястие с следните съставки: пилешко, картофи и моркови. За всяка рецепта, изброи всички използвани съставки."

С оглед на горната подсказка, може да получите отговор, подобен на:

```output
1. Roasted Chicken and Vegetables:
Ingredients:
- 4 chicken thighs
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 2 tablespoons olive oil
- 2 cloves garlic, minced
- 1 teaspoon dried thyme
- 1 teaspoon dried oregano
- Salt and pepper, to taste

2. Chicken and Potato Stew:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 cloves garlic, minced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

3. Chicken and Potato Bake:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 2 cloves garlic, minced
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

4. Chicken and Potato Soup:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 cloves garlic, minced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 4 cups chicken broth
- Salt and pepper, to taste

5. Chicken and Potato Hash:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 2 cloves garlic, minced
- 1 teaspoon dried oregano
```

Този резултат е страхотен, знам какво да готвя. На този етап полезни подобрения биха могли да бъдат:

- Филтриране на съставки, които не харесвам или към които съм алергичен.
- Създаване на списък за пазаруване, в случай че нямам всички съставки у дома.

За горните случаи, нека добавим допълнителна подсказка:

> "Моля, премахнете рецепти с чесън, тъй като съм алергичен, и го заменете с нещо друго. Също така, моля, създайте списък за пазаруване за рецептите, като се има предвид, че вече имам пилешко, картофи и моркови у дома."

Сега имате нов резултат, а именно:

```output
1. Roasted Chicken and Vegetables:
Ingredients:
- 4 chicken thighs
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 2 tablespoons olive oil
- 1 teaspoon dried thyme
- 1 teaspoon dried oregano
- Salt and pepper, to taste

2. Chicken and Potato Stew:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

3. Chicken and Potato Bake:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 1 cup chicken broth
- Salt and pepper, to taste

4. Chicken and Potato Soup:
Ingredients:
- 2 tablespoons olive oil
- 1 onion, diced
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 teaspoon dried oregano
- 1 teaspoon dried thyme
- 4 cups chicken broth
- Salt and pepper, to taste

5. Chicken and Potato Hash:
Ingredients:
- 2 tablespoons olive oil
- 2 chicken breasts, cut into cubes
- 2 potatoes, cut into cubes
- 2 carrots, cut into cubes
- 1 onion, diced
- 1 teaspoon dried oregano

Shopping List:
- Olive oil
- Onion
- Thyme
- Oregano
- Salt
- Pepper
```

Това са вашите пет рецепти, без чесън, и също така имате списък за пазаруване, като се взема предвид това, което вече имате у дома.

## Упражнение - създаване на генератор на рецепти

Сега, когато разгледахме сценарий, нека напишем код, който съответства на демонстрирания сценарий. За да направите това, следвайте тези стъпки:

1. Използвайте съществуващия файл _app.py_ като отправна точка.
1. Намерете променливата `prompt` и променете нейния код на следното:

   ```python
   prompt = "Show me 5 recipes for a dish with the following ingredients: chicken, potatoes, and carrots. Per recipe, list all the ingredients used"
   ```

   Ако сега изпълните кода, трябва да видите изход, подобен на:

   ```output
   -Chicken Stew with Potatoes and Carrots: 3 tablespoons oil, 1 onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 1/2 cups chicken broth, 1/2 cup dry white wine, 2 tablespoons chopped fresh parsley, 2 tablespoons unsalted butter, 1 1/2 pounds boneless, skinless chicken thighs, cut into 1-inch pieces
   -Oven-Roasted Chicken with Potatoes and Carrots: 3 tablespoons extra-virgin olive oil, 1 tablespoon Dijon mustard, 1 tablespoon chopped fresh rosemary, 1 tablespoon chopped fresh thyme, 4 cloves garlic, minced, 1 1/2 pounds small red potatoes, quartered, 1 1/2 pounds carrots, quartered lengthwise, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 (4-pound) whole chicken
   -Chicken, Potato, and Carrot Casserole: cooking spray, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and shredded, 1 potato, peeled and shredded, 1/2 teaspoon dried thyme leaves, 1/4 teaspoon salt, 1/4 teaspoon black pepper, 2 cups fat-free, low-sodium chicken broth, 1 cup frozen peas, 1/4 cup all-purpose flour, 1 cup 2% reduced-fat milk, 1/4 cup grated Parmesan cheese

   -One Pot Chicken and Potato Dinner: 2 tablespoons olive oil, 1 pound boneless, skinless chicken thighs, cut into 1-inch pieces, 1 large onion, chopped, 3 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 bay leaf, 1 thyme sprig, 1/2 teaspoon salt, 1/4 teaspoon black pepper, 2 cups chicken broth, 1/2 cup dry white wine

   -Chicken, Potato, and Carrot Curry: 1 tablespoon vegetable oil, 1 large onion, chopped, 2 cloves garlic, minced, 1 carrot, peeled and chopped, 1 potato, peeled and chopped, 1 teaspoon ground coriander, 1 teaspoon ground cumin, 1/2 teaspoon ground turmeric, 1/2 teaspoon ground ginger, 1/4 teaspoon cayenne pepper, 2 cups chicken broth, 1/2 cup dry white wine, 1 (15-ounce) can chickpeas, drained and rinsed, 1/2 cup raisins, 1/2 cup chopped fresh cilantro
   ```

   > ЗАБЕЛЕЖКА, вашият LLM е недетерминиран, така че може да получите различни резултати всеки път, когато изпълните програмата.

   Страхотно, нека видим как можем да подобрим нещата. За да подобрим нещата, искаме да се уверим, че кодът е гъвкав, така че съставките и броят на рецептите да могат да бъдат подобрени и променени.

1. Нека променим кода по следния начин:

   ```python
   no_recipes = input("No of recipes (for example, 5): ")

   ingredients = input("List of ingredients (for example, chicken, potatoes, and carrots): ")

   # interpolate the number of recipes into the prompt an ingredients
   prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used"
   ```

   Тестването на кода може да изглежда така:

   ```output
   No of recipes (for example, 5): 3
   List of ingredients (for example, chicken, potatoes, and carrots): milk,strawberries

   -Strawberry milk shake: milk, strawberries, sugar, vanilla extract, ice cubes
   -Strawberry shortcake: milk, flour, baking powder, sugar, salt, unsalted butter, strawberries, whipped cream
   -Strawberry milk: milk, strawberries, sugar, vanilla extract
   ```

### Подобрение чрез добавяне на филтър и списък за пазаруване

Сега имаме работещо приложение, способно да създава рецепти, и то е гъвкаво, тъй като разчита на входни данни от потребителя, както за броя на рецептите, така и за използваните съставки.

За да го подобрим допълнително, искаме да добавим следното:

- **Филтриране на съставки**. Искаме да можем да филтрираме съставки, които не харесваме или към които сме алергични. За да постигнем тази промяна, можем да редактираме съществуващата подсказка и да добавим условие за филтър в края й, както следва:

  ```python
  filter = input("Filter (for example, vegetarian, vegan, or gluten-free): ")

  prompt = f"Show me {no_recipes} recipes for a dish with the following ingredients: {ingredients}. Per recipe, list all the ingredients used, no {filter}"
  ```

  Горе добавяме `{filter}` в края на подсказката и също така улавяме стойността на филтъра от потребителя.

  Примерен вход при изпълнение на програмата може да изглежда така:

  ```output
  No of recipes (for example, 5): 3
  List of ingredients (for example, chicken, potatoes, and carrots): onion,milk
  Filter (for example, vegetarian, vegan, or gluten-free): no milk

  1. French Onion Soup

  Ingredients:

  -1 large onion, sliced
  -3 cups beef broth
  -1 cup milk
  -6 slices french bread
  -1/4 cup shredded Parmesan cheese
  -1 tablespoon butter
  -1 teaspoon dried thyme
  -1/4 teaspoon salt
  -1/4 teaspoon black pepper

  Instructions:

  1. In a large pot, sauté onions in butter until golden brown.
  2. Add beef broth, milk, thyme, salt, and pepper. Bring to a boil.
  3. Reduce heat and simmer for 10 minutes.
  4. Place french bread slices on soup bowls.
  5. Ladle soup over bread.
  6. Sprinkle with Parmesan cheese.

  2. Onion and Potato Soup

  Ingredients:

  -1 large onion, chopped
  -2 cups potatoes, diced
  -3 cups vegetable broth
  -1 cup milk
  -1/4 teaspoon black pepper

  Instructions:

  1. In a large pot, sauté onions in butter until golden brown.
  2. Add potatoes, vegetable broth, milk, and pepper. Bring to a boil.
  3. Reduce heat and simmer for 10 minutes.
  4. Serve hot.

  3. Creamy Onion Soup

  Ingredients:

  -1 large onion, chopped
  -3 cups vegetable broth
  -1 cup milk
  -1/4 teaspoon black pepper
  -1/4 cup all-purpose flour
  -1/2 cup shredded Parmesan cheese

  Instructions:

  1. In a large pot, sauté onions in butter until golden brown.
  2. Add vegetable broth, milk, and pepper. Bring to a boil.
  3. Reduce heat and simmer for 10 minutes.
  4. In a small bowl, whisk together flour and Parmesan cheese until smooth.
  5. Add to soup and simmer for an additional 5 minutes, or until soup has thickened.
  ```

  Както виждате, всички рецепти с мляко са филтрирани. Но ако сте непоносимост към лактоза, може да искате да филтрирате и рецепти със сирене, така че е важно да бъдете ясни.

- **Създаване на списък за пазаруване**. Искаме да създадем списък за пазаруване, като се взема предвид това, което вече имаме у дома.

  За тази функционалност можем или да се опитаме да решим всичко в една подсказка, или да я разделим на две подсказки. Нека опитаме втория подход. Тук предлагаме да добавим допълнителна подсказка, но за да работи това, трябва да добавим резултата от първата подсказка като контекст към втората подсказка.

  Намерете частта в кода, която отпечатва резултата от първата подсказка, и добавете следния код отдолу:
  ```python
  old_prompt_result = completion.choices[0].message.content
  prompt = "Produce a shopping list for the generated recipes and please don't include ingredients that I already have."

  new_prompt = f"{old_prompt_result} {prompt}"
  messages = [{"role": "user", "content": new_prompt}]
  completion = openai.Completion.create(engine=deployment_name, messages=messages, max_tokens=1200)

  # print response
  print("Shopping list:")
  print(completion.choices[0].message.content)
  ```

  Обърнете внимание на следното:

  1. Конструираме ново подканване, като добавяме резултата от първото подканване към новото подканване:

     ```python
     new_prompt = f"{old_prompt_result} {prompt}"
     ```

  1. Правим нова заявка, но също така вземаме предвид броя на токените, които поискахме в първото подканване, така че този път задаваме `max_tokens` на 1200.

     ```python
     completion = openai.Completion.create(engine=deployment_name, prompt=new_prompt, max_tokens=1200)
     ```

     Изпробвайки този код, стигаме до следния резултат:

     ```output
     No of recipes (for example, 5): 2
     List of ingredients (for example, chicken, potatoes, and carrots): apple,flour
     Filter (for example, vegetarian, vegan, or gluten-free): sugar


     -Apple and flour pancakes: 1 cup flour, 1/2 tsp baking powder, 1/2 tsp baking soda, 1/4 tsp salt, 1 tbsp sugar, 1 egg, 1 cup buttermilk or sour milk, 1/4 cup melted butter, 1 Granny Smith apple, peeled and grated
     -Apple fritters: 1-1/2 cups flour, 1 tsp baking powder, 1/4 tsp salt, 1/4 tsp baking soda, 1/4 tsp nutmeg, 1/4 tsp cinnamon, 1/4 tsp allspice, 1/4 cup sugar, 1/4 cup vegetable shortening, 1/4 cup milk, 1 egg, 2 cups shredded, peeled apples
     Shopping list:
     -Flour, baking powder, baking soda, salt, sugar, egg, buttermilk, butter, apple, nutmeg, cinnamon, allspice
     ```

## Подобрете вашата настройка

Това, което имаме досега, е код, който работи, но има някои корекции, които трябва да направим, за да подобрим нещата още повече. Някои от нещата, които трябва да направим, са:

- **Отделете тайните от кода**, като например API ключа. Тайните не принадлежат на кода и трябва да се съхраняват на сигурно място. За да отделим тайните от кода, можем да използваме променливи на средата и библиотеки като `python-dotenv`, за да ги заредим от файл. Ето как би изглеждало това в кода:

  1. Създайте `.env` файл със следното съдържание:

     ```bash
     OPENAI_API_KEY=sk-...
     ```

     > Забележка, за Azure трябва да зададете следните променливи на средата:

     ```bash
     OPENAI_API_TYPE=azure
     OPENAI_API_VERSION=2023-05-15
     OPENAI_API_BASE=<replace>
     ```

     В кода бихте заредили променливите на средата по следния начин:

     ```python
     from dotenv import load_dotenv

     load_dotenv()

     openai.api_key = os.environ["OPENAI_API_KEY"]
     ```

- **Думата за дължината на токените**. Трябва да обмислим колко токени са ни необходими, за да генерираме текста, който искаме. Токените струват пари, така че, където е възможно, трябва да се опитаме да бъдем икономични с броя на използваните токени. Например, можем ли да формулираме подканването така, че да използваме по-малко токени?

  За да промените използваните токени, можете да използвате параметъра `max_tokens`. Например, ако искате да използвате 100 токена, бихте направили:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, max_tokens=100)
  ```

- **Експериментиране с температурата**. Температурата е нещо, което досега не сме споменавали, но е важен контекст за това как работи нашата програма. Колкото по-висока е стойността на температурата, толкова по-случаен ще бъде резултатът. Обратно, колкото по-ниска е стойността на температурата, толкова по-предсказуем ще бъде резултатът. Помислете дали искате вариация в резултата или не.

  За да промените температурата, можете да използвате параметъра `temperature`. Например, ако искате да използвате температура от 0.5, бихте направили:

  ```python
  completion = client.chat.completions.create(model=deployment, messages=messages, temperature=0.5)
  ```

  > Забележка, колкото по-близо до 1.0, толкова по-разнообразен е резултатът.

## Задача

За тази задача можете да изберете какво да създадете.

Ето някои предложения:

- Подобрете приложението за генериране на рецепти. Експериментирайте със стойностите на температурата и подканванията, за да видите какво можете да постигнете.
- Създайте "учебен помощник". Това приложение трябва да може да отговаря на въпроси за дадена тема, например Python. Можете да имате подканвания като "Какво представлява определена тема в Python?" или подканване, което казва "Покажи ми код за определена тема" и т.н.
- Исторически бот, направете историята жива, инструктирайте бота да играе определен исторически персонаж и му задавайте въпроси за живота и времето му.

## Решение

### Учебен помощник

По-долу е начално подканване, вижте как можете да го използвате и да го адаптирате според вашите предпочитания.

```text
- "You're an expert on the Python language

    Suggest a beginner lesson for Python in the following format:

    Format:
    - concepts:
    - brief explanation of the lesson:
    - exercise in code with solutions"
```

### Исторически бот

Ето някои подканвания, които можете да използвате:

```text
- "You are Abe Lincoln, tell me about yourself in 3 sentences, and respond using grammar and words like Abe would have used"
- "You are Abe Lincoln, respond using grammar and words like Abe would have used:

   Tell me about your greatest accomplishments, in 300 words"
```

## Проверка на знанията

Какво прави концепцията за температура?

1. Контролира колко случаен е резултатът.
1. Контролира колко голям е отговорът.
1. Контролира колко токени се използват.

## 🚀 Предизвикателство

Докато работите върху задачата, опитайте да променяте температурата, опитайте да я зададете на 0, 0.5 и 1. Запомнете, че 0 е най-малко разнообразно, а 1 е най-разнообразно. Коя стойност работи най-добре за вашето приложение?

## Отлична работа! Продължете да учите

След като завършите този урок, разгледайте нашата [колекция за обучение по Генеративен AI](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst), за да продължите да развивате знанията си за Генеративен AI!

Преминете към Урок 7, където ще разгледаме как да [създаваме чат приложения](../07-building-chat-applications/README.md?WT.mc_id=academic-105485-koreyst)!

---

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI услуга за превод [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи може да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или погрешни интерпретации, произтичащи от използването на този превод.