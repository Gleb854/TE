\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}
\usepackage{hyperref}

\title{Решение тестового задания}
\author{Глеб Стрижнев}
\date{\today}

\begin{document}

\maketitle

\section{Введение}
В данном отчете представлен процесс решения тестового задания, включавшего в себя 3 задачи:
1.
2.
3. анализа данных о погоде для выбора лучших городов для жизни с использованием различных моделей машинного обучения и инструментов для обработки данных. 
Для последнего я использовал такие модели, как \texttt{sentence-transformers/all-MiniLM-L6-v2} и \texttt{microsoft/phi-2}, а также сервис Pinecone для поиска ближайших соседей. Основная цель заключалась в определении городов с умеренной температурой, низким количеством жарких и холодных периодов, а также низкой скоростью ветра.

\section{Используемые модели}

\subsection{\texttt{sentence-transformers/all-MiniLM-L6-v2}}
\textbf{Преимущества:}
\begin{itemize}
    \item Высокая производительность при создании векторных представлений текста.
    \item Хорошо подходит для задач поиска и сравнения текстов.
    \item Компактная модель, которая быстро обрабатывает запросы.
\end{itemize}

\textbf{Недостатки:}
\begin{itemize}
    \item Ограниченная контекстная информация по сравнению с более крупными моделями.
    \item Может не учитывать всю семантическую глубину сложных текстов.
\end{itemize}

\subsection{\texttt{microsoft/phi-2}}
\textbf{Преимущества:}
\begin{itemие}
    \item Высокая точность генерации текста.
    \item Способна генерировать текст на основе сложных запросов и контекста.
\end{itemize}

\textbf{Недостатки:}
\begin{itemize}
    \item Большой размер модели требует значительных вычислительных ресурсов.
    \item Модель может иногда генерировать тексты с некорректной информацией.
\end{itemize}

\subsection{\texttt{google/tapas-large-finetuned-wtq}}
\textbf{Преимущества:}
\begin{itemize}
    \item Способна отвечать на вопросы, основываясь на табличных данных.
    \item Высокая точность ответов на вопросы, связанные с табличной информацией.
\end{itemize}

\textbf{Недостатки:}
\begin{itemize}
    \item Требует значительных вычислительных ресурсов.
    \item Ограниченная длина входных данных может потребовать разделения больших таблиц на части.
\end{itemize}

\section{Используемые подходы}

\subsection{Векторизация данных и поиск ближайших соседей}
Я использовал модель \texttt{sentence-transformers/all-MiniLM-L6-v2} для создания векторных представлений описаний городов. С помощью Pinecone я выполнял поиск ближайших соседей для определения схожести текстов.

\subsection{Генерация текста на основе описаний}
Для генерации описаний и ответа на запросы я использовал модель \texttt{microsoft/phi-2}. Сгенерированные тексты затем переводились на русский язык с использованием библиотеки \texttt{googletrans}.

\subsection{Ответы на вопросы на основе табличных данных}
Для получения ответов на вопросы, связанные с табличными данными, я использовал модель \texttt{google/tapas-large-finetuned-wtq}.

\section{Процесс работы}

\subsection{Подготовка данных}
\begin{itemize}
    \item Загрузка и предварительная обработка данных о погоде из CSV-файла .
\end{itemize}

\subsection{Задание 1}
\begin{itemize}
    \item Решение задания 1 заняло около 10 минут.
\end{itemize}

\subsection{Задание 2}
\begin{itemize}
    \item Решение задания 2 заняло около 3 минут.
\end{itemize}

\subsection{Задание 3}
\begin{itemize}
    \item Решение задания 3 заняло 5 часов, из которых 2 часа анализ моделей и возможности их применения, 3 часа тестирование и разработка алгоритмов.

\subsection{Подготовка данных}
\begin{itemize}
    \item Загрузка и предварительная обработка данных о погоде из CSV-файла.
    \item Группировка данных по городам и расчет средних значений температуры и скорости ветра.
    \item Классификация температур и скорости ветра по категориям (холодная, комфортная, жаркая; слабый, умеренный, сильный, ураганный ветер).
    \item Создание описаний для каждого города на основе рассчитанных значений.
\end{itemize}

\subsection{Векторизация и загрузка данных в Pinecone}
\begin{itemize}
    \item Преобразование описаний городов в векторные представления с помощью \texttt{sentence-transformers/all-MiniLM-L6-v2}.
    \item Загрузка векторных представлений в индекс Pinecone для последующего поиска.
\end{itemize}

\subsection{Генерация текстов и поиск лучших городов (5 часов, из которых 2 часа анализ моделей и возможности их применения, 3 часа тестирование и разработка алгоритмов)}
\begin{itemize}
    \item Формирование запросов на основе описаний городов и генерация текстов с использованием модели \texttt{microsoft/phi-2}.
    \item Поиск ближайших соседей в Pinecone для определения наиболее подходящих городов.
    \item Перевод сгенерированных текстов на русский язык с использованием библиотеки \texttt{googletrans}.
\end{itemize}

\subsection{Подготовка кода и оформление на GitHub (30 минут)}
\begin{itemize}
    \item Подготовка кода для загрузки на GitHub.
    \item Оформление репозитория и загрузка кода.
\end{itemize}


\section{Краткие выводы}
Модель \texttt{google/tapas-large-finetuned-wtq} хорошо подходит для работы с табличными данными, но не позволяет генерировать развернутые ответы. Использование векторной разметки с Pinecone не улучшило результаты и до сих пор присутствуют галлюцинации. Модель \texttt{microsoft/phi-2} показала неплохие результаты, при условии, что я отбираю признаки для анализа. Реализация также возможна через API OpenAI с использованием Langchain, однако я не стал использовать этот подход, так как он не является обучением LLM, а лишь адресует вопрос модели.

\end{document}
