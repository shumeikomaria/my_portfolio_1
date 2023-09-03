### Легенда:
Существует интернет магазин, продающий самые разные товары для повседневной жизни и электронику. Одними из основных KPI магазина руководство обозначило выручку и аудиторию. Менеджер, ответственный за проект, направляет значительные средства на рекламу интернет магазина на различных каналах и привлечение как можно большего числа пользователей.
Две недели назад оказалось, что несмотря на постоянно растущую аудиторию магазина (MAU), суммарная выручка упала. Менеджер объясняет это началом отпускного сезона. 

### Задача:
Руководство магазино поручило вам проверить теорию менеджера и дать более точный отчет по причинам падения выручки, а также сформулировать рекомендации по ее увеличению, если такие возможности существуют.

### Данные, доступные для анализа: 
Агрегированные логи действий пользователей на сайте в json формате (считаем, что все поля в логе посчитаны корректно)<br>
{'date':'%Y-%m-%d %H-%M-%S %Z',<br>
 'action': [тип действия пользователя на сайте],<br>
 'cid': кука пользователя,<br>
 'browser': тип браузера пользователя,<br>
 'browser_version': версия браузера пользователя,<br>
 'platform': тип устройства пользователя[desktop, android, ios, unknown],<br>
 'channel': канал привлечения пользователя,<br>
 'sum': сумма покупки, если тип действия == 'make_order'}<p>
 
 Типы действий пользователя:<br>
 open - просмотр главной страницы сайта. Все сессии работы сайта начинаются с просмотра главной страницы<br>
 search - поиск товаров через внутреннюю поисковую систему<br>
 product_view - просмотр карточки товара<br>
	Дополнительные поля: product_id: - id продукта, product_priсe - стоимость продукта<br>
 add_to_cart - добавление товара в корзину<br>
	Дополнительные поля: product_id - id продукта, product_priсe- стоимость продукта, items_count - кол-во продуктов<br>
 make_order - совершение заказа<br>

Алгоритм рассчета KPI: MAU - кол-во уникальных посетителей в логах (по cid) за последние 30 дней,<br>
						выручка - сумма всех значений cost в событии make_order за последние 30 дней

### Содержание исследования:
1. Описание динамики KPI: выручка и аудитория + связанные метрики
2. Проверка гипотезы менеджера: падение выручки на фоне растущей
аудитории связано с сезонным фактором (сезон отпусков)
3. Проверка альтернативных гипотез:<br>
    a. Возможная причина: нерелевантная маркетинговая стратегия<br>
    b. Возможная причина: низкая лояльность аудитории<br>
4. Рекомендации по увеличению выручки
5. Варианты дальнейшего исследования

### Выводы: (более подробно представлены в файле со слайдами "Revenue Drop Analysis Slides with Conclusions")
● Снижение KPI - структурная проблема, не связана с сезонным фактором<br>
● Низкая лояльность аудитории (более 80% пользователей - новые; низкий retention) -> скорее всего, LTV низкий, а CAC не окупается<br>
● От новых партнеров приходят клиенты с очень низким чеком -> маркетинг приводит нецелевой трафик, который, скорее всего, не окупается<br>


### Рекомендации по увеличению выручки и дальнейшее исследование:
Для увеличения ключевых показателей предлагаю рассмотреть следующие варианты действий:<br>
● Оценить окупаемость затрат на маркетинг (ROMI)<br>
● Составить и протестировать новые варианты маркетинговой стратегии, например<br>
    ○ отказаться от сотрудничества с некоторыми партнерами<br>
    ○ поменять или усилить позиционирование и УТП; проверить совпадение ЦА партнеров и магазина<br>
● Разработать стратегию формирования лояльной аудитории, которую затем возможно масштабировать<br>
    ○ добавить возможности повторного взаимодействия с клиентом для увеличения retention<br>

Также, необходимо разобраться в причинах изменения динамики показателей в июне-июле 2017.<br>
Для этого:<br>
● Провести анализ конкурентов, и иных факторов внешней среды<br>
● Провести анализ внутренних изменений в интернет-магазине (ценообразование, удобство платежей, иные
барьеры к покупке (“платная” доставка), формирование поисковой выдачи)<br>
