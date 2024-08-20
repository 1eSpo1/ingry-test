# ingry-test

## Архитектура: 
Так как это тестовое задание, то я решил не усложнять и выбрал  модульную архитектуру.
Маштабировать данное приложение не требуется => основная задача архитектуры это упросить
и ускорить процесс ревью, с чем обычные модули хорошо справляются. Также у нас моковые данные
=> нет надобности в выстраивании архитектуры по типу FSD, где мы должны соблюдать Low Coupling
High Cohesion или других архитектурных принципов работы с модулями/сущностями.

## Библиотеки и технологии

Постарался по минимуму добавлять технологий. 
- Vue
- TypeScript. Не там много опыта Vue + TypeScript => чем больше практики тем лучше
- Vue-charts + Charts.js. Популярное и относительно легкое решение для графиков
- ~~Vue Router~~ Нет страниц => не нужна навигация
- ~~Pinia~~ Данные моковые + нет флоу по работе с данными

## Задачи и оценки

- Вертска Хедера. Оценка ~1 час. Фактически ~1 час.
- Верстка Сайдбара. Оценка ~1 час. Фактически ~1 час.
- Верстка незначительных элементов страницы (футер, хлебные крошки, рефреш + тайтл). Оценка 1 час. Фактически 1 час.
- Разработка компонента меню (с графиками). Оценка ~5 часов. Фактически ~6 часов.
  1) Разработка карточки с категорией ошибки. Оценка ~1 час. Фактически ~1 час.
  2) Разработка карточки графика. Оценка ~4 часа. Фактически ~5 часов.
- Разработка компонента таблицы с кнопками фильтрации. Оценка ~6 часов. Фактически ~6 часов.
  1) Разработка таблицы на основе моковых данных. Оценка ~4 часа. Фактически ~4 часа.
  2) Разработка кнопок фильтрации и реализация логики. Оценка ~2 часа. Фактически ~2 часа.

## Комментарии
- Я не стал выделять базовые компоненты т.к. в рамках тестового задания это скорее тормозит, 
потому что не так много переиспользуемых элементов. 
- Также оставил некоторые моменты неидеально
повторяющими макет, например сайдбар. Просто ради экономии времени. Навыки верстки можно оценить
по другим элементам, а элементы сайдбара смысловой нагрузки не несут. 
- Также неидальная работа с данными. Это обусловленно моками. Да, данные для графиков можно было построить на основе моков, но
тогда непонятно откуда брать данные для первого графика. Поэтому создал отдельные объекты под меню.
- Рефакторинг. Не довел компонеты (в том чилсе App) до идеально чистых, т.к. уже поджимало время.
Не хотел тратить больше выделенного времени (относительно рабочих часов).
- Доработки: 
  1) Пагинация/Виртуализация таблицы
  2) useDebounce на инпут
  3) Оживление фильтра таблицы

