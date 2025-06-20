# 26 научно обоснованных принципов промпт-инжиниринга

*Основано на исследовании "Principled Instructions Are All You Need for Questioning LLaMA-1/2, GPT-3.5/4" (2024)*

## Введение

Данные принципы были научно протестированы на моделях LLaMA-1/2 (7B, 13B, 70B) и GPT-3.5/4 с использованием бенчмарка ATLAS. Исследование показало средние улучшения на **57.7%** в качестве и **67.3%** в точности ответов при применении этих принципов.

---

## Категория 1: Структура и ясность промптов

### Принцип 1: Прямолинейность в коммуникации
**Описание**: Избегайте излишне вежливых фраз типа "пожалуйста", "если вас не затруднит", "спасибо", "я бы хотел".

**Обоснование**: Эти фразы не влияют на качество ответа LLM, но увеличивают длину промпта без добавленной ценности.

**Применение**:
- ❌ Неэффективно: "Пожалуйста, не могли бы вы помочь мне с анализом данных, если вас не затруднит?"
- ✅ Эффективно: "Проанализируйте следующие данные и выделите ключевые тренды."

### Принцип 2: Интеграция целевой аудитории
**Описание**: Включайте информацию о целевой аудитории в промпт.

**Варианты формулировок**:
- "Аудитория - эксперты в области [область]"
- "Объясните как для детей 10 лет"
- "Создайте контент для начинающих в [область]"

**Применение**:
```
Объясните принципы машинного обучения.
Аудитория: студенты первого курса технического вуза без предварительных знаний в программировании.
```

### Принцип 3: Разделение сложных задач
**Описание**: Разбивайте комплексные задачи на последовательность простых промптов в интерактивном диалоге.

**Применение**:
Вместо одного сложного запроса:
1. Первый промпт: "Определите основные компоненты системы"
2. Второй промпт: "Опишите взаимодействие между компонентами"
3. Третий промпт: "Предложите план оптимизации"

### Принцип 4: Утвердительные директивы
**Описание**: Используйте утвердительные инструкции ("сделайте") вместо отрицательных ("не делайте").

**Метрики**: Показал стабильные улучшения во всех тестируемых моделях.

**Применение**:
- ❌ "Не используйте сложную терминологию"
- ✅ "Используйте простой и понятный язык"

### Принцип 5: Запрос разъяснений
**Описание**: Когда нужно более глубокое понимание, используйте специальные формулировки:
- "Объясните [тема] простыми словами"
- "Объясните мне как 11-летнему ребенку"
- "Объясните как новичку в [область]"
- "Напишите [текст] простым языком, как будто объясняете 5-летнему"

---

## Категория 2: Специфичность и информация

### Принцип 6: Использование обязательных конструкций
**Описание**: Включайте фразы "Ваша задача" и "Вы ДОЛЖНЫ".

**Применение**:
```
Ваша задача - создать техническую документацию для API.
Вы ДОЛЖНЫ включить примеры кода для каждого эндпоинта.
```

### Принцип 7: Применение штрафов
**Описание**: Включайте фразу "Вас накажут" для повышения точности выполнения инструкций.

**Применение**:
```
Переведите текст, сохранив точный смысл оригинала.
Вас накажут за неточный перевод или добавление информации, которой нет в оригинале.
```

### Принцип 8: Естественный ответ на вопросы
**Описание**: Формулируйте запросы естественным образом: "Какой твой [вопрос]?"

**Применение**:
- "Какой твой подход к решению этой проблемы?"
- "Какое твое мнение о данной стратегии?"

### Принцип 9: Внедрение ведущих слов
**Описание**: Используйте направляющие фразы для активации пошагового мышления.

**Варианты**:
- "Думайте пошагово"
- "Сделайте глубокий вдох и решайте проблему поэтапно"
- "Убедитесь, что ваш ответ точен"

### Принцип 10: Добавление мотивационных элементов
**Описание**: Включайте фразы, повышающие важность задачи.

**Применение**:
```
Это очень важно для моей карьеры.
Проанализируйте данные с максимальной точностью.
```

### Принцип 11: Использование примеров (Few-shot prompting)
**Описание**: Предоставляйте несколько примеров желаемого формата ответа.

**Структура**:
```
Задача: [описание]

Пример 1:
Вход: [входные данные]
Выход: [желаемый результат]

Пример 2:
Вход: [входные данные]
Выход: [желаемый результат]

Теперь обработайте:
Вход: [новые данные]
Выход:
```

### Принцип 12: Форматирование с разделителями
**Описание**: Используйте разделители для структурирования различных частей промпта.

**Варианты разделителей**:
- Тройные кавычки: """текст"""
- XML-теги: `<инструкция>текст</инструкция>`
- Специальные символы: ### Секция ###

---

## Категория 3: Взаимодействие с пользователем и роли

### Принцип 13: Назначение экспертной роли
**Описание**: Назначайте модели специфическую экспертную роль.

**Шаблоны**:
- "Вы - эксперт в области [область]"
- "Действуйте как опытный [профессия]"
- "Ваша роль - [конкретная экспертиза]"

**Применение**:
```
Вы - опытный data scientist с 10-летним стажем.
Проанализируйте этот датасет и предложите модель машинного обучения.
```

### Принцип 14: Использование разделителей для контекста
**Описание**: Четко отделяйте контекст от инструкций.

**Применение**:
```
КОНТЕКСТ:
"""
[Фоновая информация]
"""

ЗАДАЧА:
Основываясь на предоставленном контексте, выполните анализ.
```

### Принцип 15: Запрос конкретного формата
**Описание**: Четко указывайте желаемый формат выходных данных.

**Применение**:
```
Предоставьте ответ в следующем формате:
1. Краткое резюме (2-3 предложения)
2. Ключевые пункты (маркированный список)
3. Рекомендации (нумерованный список)
4. Заключение (1 абзац)
```

---

## Категория 4: Стиль контента и языка

### Принцип 16: Контроль сложности языка
**Описание**: Адаптируйте сложность языка под целевую аудиторию.

**Градации**:
- Академический уровень: "Проведите детальный анализ"
- Популярный уровень: "Объясните простыми словами"
- Детский уровень: "Расскажите как сказку"

### Принцип 17: Использование повторений для важности
**Описание**: Повторяйте ключевые инструкции для их усиления.

**Применение**:
```
Будьте максимально точны в расчетах.
Важно: все числа должны быть проверены дважды.
Помните: точность критически важна для этой задачи.
```

### Принцип 18: Комбинирование Chain-of-Thought с Few-shot
**Описание**: Сочетайте пошаговое мышление с примерами.

**Применение**:
```
Решите математическую задачу пошагово:

Пример:
Задача: У Анны было 15 яблок. Она дала 4 яблока Борису и 3 яблока Вере. Сколько яблок у неё осталось?
Решение:
Шаг 1: Начальное количество = 15 яблок
Шаг 2: Дала Борису = 4 яблока
Шаг 3: Дала Вере = 3 яблока
Шаг 4: Общий расход = 4 + 3 = 7 яблок
Шаг 5: Осталось = 15 - 7 = 8 яблок
Ответ: 8 яблок

Теперь решите: [новая задача]
```

---

## Категория 5: Сложные задачи и программирование

### Принцип 19: Тестирование кода
**Описание**: Для программных задач требуйте тестирования и отладки.

**Применение**:
```
Напишите функцию для сортировки массива.
Требования:
- Убедитесь, что код работает без ошибок
- Включите обработку граничных случаев
- Добавьте примеры использования
- Протестируйте на различных входных данных
```

### Принцип 20: Постепенное повышение сложности
**Описание**: Начинайте с простых задач и постепенно усложняйте.

**Применение**:
```
Начните с базового алгоритма сортировки пузырьком.
Затем оптимизируйте его до quicksort.
Наконец, реализуйте гибридный подход для лучшей производительности.
```

### Принцип 21: Явное указание ограничений
**Описание**: Четко формулируйте ограничения и требования.

**Применение**:
```
Ограничения:
- Используйте только стандартную библиотеку Python
- Время выполнения не должно превышать O(n log n)
- Код должен быть читаемым и содержать комментарии
- Обязательно обработайте исключения
```

---

## Дополнительные принципы (22-26)

### Принцип 22: Использование примеров для извлечения знаний
**Описание**: При работе с фактической информацией предоставляйте примеры запрашиваемого формата знаний.

### Принцип 23: Запрос обоснований
**Описание**: Просите модель обосновать свои ответы и решения.

**Применение**:
```
Предоставьте рекомендацию и объясните логику вашего решения.
Укажите факторы, которые повлияли на ваш выбор.
```

### Принцип 24: Мультиступенчатые инструкции
**Описание**: Структурируйте сложные задачи как последовательность четких шагов.

### Принцип 25: Использование контрольных вопросов
**Описание**: Включайте вопросы для самопроверки модели.

**Применение**:
```
После завершения анализа ответьте на следующие вопросы:
1. Все ли требования выполнены?
2. Логичны ли выводы?
3. Нет ли противоречий в рассуждениях?
```

### Принцип 26: Адаптация под модель
**Описание**: Учитывайте специфические особенности и сильные стороны конкретной языковой модели.

---

## Метрики эффективности

### Результаты тестирования на различных моделях:

**GPT-4**: Наибольшие улучшения, до 80% по некоторым метрикам
**GPT-3.5**: Стабильные улучшения 40-60%
**LLaMA-70B**: Значительные улучшения в сложных задачах
**Меньшие модели (7B-13B)**: Умеренные, но заметные улучшения

### Двухкомпонентная система оценки:
1. **Boosting**: Качественное улучшение ответа (субъективная оценка)
2. **Correctness**: Точность, релевантность, отсутствие ошибок (объективная оценка)

---

## Рекомендации по применению

### Приоритизация принципов:
1. **Высокий приоритет**: Принципы 1, 4, 6, 11, 13, 17 - применяйте всегда
2. **Средний приоритет**: Принципы 2, 7, 9, 12, 15 - используйте для специфических задач
3. **Специальный приоритет**: Принципы 19-26 - для сложных и технических задач

### Комбинирование принципов:
- Никогда не применяйте все 26 принципов одновременно
- Оптимально: 5-10 принципов за раз
- Тестируйте комбинации и измеряйте результативность

### Итеративный подход:
1. Начните с базового промпта
2. Примените 3-5 ключевых принципов
3. Протестируйте результат
4. Добавьте дополнительные принципы при необходимости
5. Оптимизируйте на основе результатов