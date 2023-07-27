# hotel_chain
**ПРОГНОЗИРОВАНИЕ ОТТОКА КЛИЕНТОВ В СЕТИ ОТЕЛЕЙ "КАК В ГОСТЯХ"**<br>
Яндекс.Практикум, Модуль №2, Сборный проект №2

ОПИСАНИЕ ПРОЕКТА

***Заказчик этого исследования*** — сеть отелей «Как в гостях».<br>
Чтобы привлечь клиентов, эта сеть отелей добавила на свой сайт возможность забронировать номер без предоплаты. Однако если клиент отменял бронирование, 
то компания терпела убытки. Сотрудники отеля могли, например, закупить продукты к приезду гостя или просто не успеть найти другого клиента.<br>

***Задача:*** Чтобы решить эту проблему, нужно разработать систему, которая предсказывает отказ от брони. Если модель покажет, что бронь будет отменена, 
то клиенту предлагается внести депозит. Размер депозита — 80% от стоимости номера за одни сутки и затрат на разовую уборку. Деньги будут списаны со счёта клиента, 
если он всё же отменит бронь.<br>

В отеле есть несколько типов номеров. В зависимости от типа номера назначается стоимость за одну ночь. Есть также затраты на уборку. Если клиент снял номер надолго,
то убираются каждые два дня.<br>
   
***Стоимость номеров отеля:***
- категория A: за ночь — 1 000, разовое обслуживание — 400;
- категория B: за ночь — 800, разовое обслуживание — 350;
- категория C: за ночь — 600, разовое обслуживание — 350;
- категория D: за ночь — 550, разовое обслуживание — 150;
- категория E: за ночь — 500, разовое обслуживание — 150;
- категория F: за ночь — 450, разовое обслуживание — 150;
- категория G: за ночь — 350, разовое обслуживание — 150.<br>
   
В ценовой политике отеля используются сезонные коэффициенты: весной и осенью цены повышаются на 20%, летом — на 40%.
Убытки отеля в случае отмены брони номера — это стоимость одной уборки и одной ночи с учётом сезонного коэффициента.<br>
На разработку системы прогнозирования заложен бюджет — ***400 000***. При этом необходимо учесть, что внедрение модели должно окупиться за тестовый период. 
Затраты на разработку должны быть меньше той выручки, которую система принесёт компании.<br>

МОДЕЛИ И МЕТРИКИ

В проекте были обучены три модели: решающее дерево, логистическая регрессия, случайный лес. Для каждой подобрали гиперпараметры, оценивали качество модели кросс-валидацией.<br>

Для оценки качества модели использовали F1-меру, т.к. она объединяет в себе показатели precision и recall. 
С одной стороны, для нас важно минимизировать количество ложноотрицательных ответов модели: клиентов, которые отменят бронирование, но модель решила, что они заселятся,
т.к. в этом случае отель несёт больше всего убытков, а с другой стороны, нужно попытаться  минимизировать количество ложноположительных ответов - клиентов, 
которые не собирались отменять бронирование, а модель решила, что они все-таки отменят, т.к. в этом случае взятие депозита может отпугнуть потенциальных клиентов.<br>

РЕЗУЛЬТАТЫ

Для предсказания отмены брони была выбрана и обучена модель случайного дерева. На тестовой выборке она показывает наилучшее значение F1-меры - 0.65.<br>
В результате оценке прибыли, которую принесёт модель, получили, что за тестовый период чистая прибыль составит 8 млн.<br>
    
***Рекомендации для бизнеса:***
- внедрить модель предсказания отказа от брони и депозиты
- вести периодический обзвон клиентов, которые сильно заранее бронируют номера, чтобы иметь возможность раньше узнать об отмене
- уладить сбои с подтверждением брони более, чем через один день. Возможно, наладить подвтерждение брони и на выходных тоже.
