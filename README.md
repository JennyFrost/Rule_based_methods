# Text_Processing
Project with RoBERTa based text classification, project with sentence analyzing python scripts


Text Classification:
Дипломная работа в магистратуре ОТИПЛ МГУ по теме "Автоматическое извлечение информации из текстов профилей на портале LinkedIn".

Целью данной работы является создание и обучение нейросетевой модели, извлекающей различного рода информацию из англоязычных текстов профилей людей и компаний на портале LinkedIn, а также анализ результатов ее работы. Реализация разбивается на несколько подзадач:

•	разметка данных;
•	обучение модели на обучающей выборке;
•	тестирование на тестовой выборке;
•	анализ ошибок, выявление закономерностей в работе модели.

Извлечение информации из текста проводится путём разметки последовательности, т. е. каждому токену в предложении присваивается одна из предварительно определенных меток. Эти метки включают в себя: role (роль/позиция), responsibilities (обязанности), experience (опыт), achievements (достижения), skills (навыки и способности), specialties (области и направления специализации), personal (информация о личности автора), company (информация о компании), useless (бесполезная информация).

Для решения этой задачи сначала были загружены предобученные векторные представления токенов из модели RoBERTa, а затем к ним применялась многоклассовая классификация, в результате которой каждый токен был отнесен к одному из классов — меток, перечисленных выше. Классификация была реализована добавлением линейного (feed forward) слоя, на вход которому поступали предобученные эмбеддинги для каждого слова. В результате происходит разметка последовательности, где каждому токену присваивается один из заданных классов.

Данные для обучения и тестирования модели были получены путем парсинга веб-сайта LinkedIn. Далее тексты были разбиты на предложения при помощи специального python скрипта, основанного на регулярных выражениях, учитывающих различные специальные символы, которые люди используют при перечислении навыков, клиентов, обязанностей, черт характера и т.д. В виде отдельных предложений данные уже поступали как на разметку, так и на вход модели. Перед обучением модели была проведена ручная разметка около четырёх тысяч предложений. Разметка проводилась в специальной программе Label Studio, предоставляющей удобный графический интерфейс для разметки и позволяющей быстро выделать сегменты текста и присваивать им необходимую метку. При этом метка присваивалась каждому слову отдельно.

