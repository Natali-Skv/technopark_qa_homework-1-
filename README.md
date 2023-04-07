# [Наш проект (Delivery-club)](https://tavide.xyz/main)
---
# Тестовое окружение
* Операционная система: **Ubuntu 22.04.1 LTS**
* Браузер: **Google Chrome Version 105.0.5195.125 (Official Build) (64-bit)**
* Расширение экрана **1920 x 1024**
---
# Тестирование страницы оформления заказа */ordering*
## **Навигация**  
> :red_square: находясь на странице */ordering*, при нажатии :arrow_left: (кнопка навигации в браузере), происходит редирект на предыдущую страницу, посещенную пользователем.   
   **Описание бага:** если на страницу */ordering* пользователь перешел со страницы ресторана через кнопку "заказать" внизу корзины, то при нажатии :arrow_left:, находясь на */ordering* происходит открытие корзины.
![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/navigation_shopping_cart.png)   
>
> :red_square: при возврате на страницу /ordering с помощью :arrow_right: (кнопка навигации в браузере), происходит редирект на страницу оформления заказа, где верно указаны:
>  - блюда в корзине (соответствуют списку и количеству блюд, которые пользователь положил в корзину)
>  - общая стоимость (расчитана в соответствии с количеством блюд, ценой блюд, примененным промокодом)
>  - цена доставки (99Р, если итоговая стоимость < минимальной стоимости для бесплатной доставки данного ресторана; 0 Р, если  если итоговая стоимость >= минимальной стоимости для бесплатной доставки данного ресторана)
>  - суммарная скидка (вычислена как "итоговая стоимость без учета промокода" - "итоговая стоимость с учетом промокода", соответственно, если промокод не применен, суммарная скидка = 0Р)
>  - промокод (если применен, отображается название, если не применен — ничего не отображается)
>  - адрес доставки (тот, что был указан в хедере у пользователя перед переходом на страницу оформления заказа)
>  - телефон пользователя (тот, на который зарегистрирован аккаунт пользователя)  
>
> **Описание бага:** если итоговая стоимость блюд в корзине < минимальной стоимости для бесплатной доставки данного ресторана, то при возврате на страницу */ordering* с помощью :arrow_right:, доставка становится бесплатной.    
> 
>   **страница */ordering*, на которую пользователь перещел через кнопку "заказать" внизу корзины**  
> ![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/reload_page.png)   
> 
>   **страница */ordering*, на которую пользователь вернулся через :arrow_right:**  
> ![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/reload_page_before.png)   
> 
> :red_square: если при пустой корзине пользователя вписать в адресную строку "https://tavide.xyz/ordering", то происходит редирект на страницу оформления заказа, где 
> - кнопка "заказать" неактивна
> - вместо корзины отображается надпись *"Чтобы сделать заказ, положите блюда в корзину"*
> - промокод (если применен, отображается название, если не применен, то ничего не отображается)
> - адрес доставки (тот, что был указан у пользователя перед переходом на страницу оформления заказа)
> - телефон пользователя (тот, на который зарегистрирован аккаунт пользователя)    
> - общая стоимость 0Р
> - цена доставки 0Р
> - суммарная скидка  0Р
> 
>  **Описание бага:** если при пустой корзине пользователя вписать в адресную строку "https://tavide.xyz/ordering", то происходит редирект на абсолютно пустую страницу.  
> ![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/empty.png)   
> :red_square: если при не пустой корзине пользователя вписать в адресную строку "https://tavide.xyz/ordering", то происходит редирект на страницу оформления заказа, где верно указаны:
>  - блюда в корзине (соответствуют списку и количеству блюд, которые пользователь положил в корзину)
>  - общая стоимость (расчитана в соответствии с количеством блюд, ценой блюд, примененным промокодом)
>  - цена доставки (99Р, если итоговая стоимость < минимальной стоимости для бесплатной доставки данного ресторана; 0 Р, если  если итоговая стоимость >= минимальной стоимости для бесплатной доставки данного ресторана)
>  - суммарная скидка (вычислена как "итоговая стоимость без учета промокода" - "итоговая стоимость с учетом промокода", соответственно, если промокод не применен, суммарная скидка — 0Р)
>  - промокод (если применен, отображается название, если не применен, то ничего не отображается)
>  - адрес доставки (тот, что был указан у пользователя перед переходом на страницу оформления заказа)
>  - телефон пользователя (тот, на который зарегистрирован аккаунт пользователя)  
>    
>  **Описание бага:** если при не пустой корзине пользователя с итоговой стоимостью < минимальной стоимости для бесплатной доставки данного ресторана,  вписать в адресную строку "https://tavide.xyz/ordering", то отображается, что доставка бесплатная.  
> ![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/reload_page_before.png)   
>      
> :green_square: если неавторизованный пользователь вписывает в адресную строку "https://tavide.xyz/ordering", то происходит редирект на страницу авторизации */login*
## **Форма оформления заказа**
![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/order_form.png)
### инпут телефона:  
> :green_square: телефон пользователя отображается корректно, указан верно  
>    критерии:   
>  - формат отображения : ***+7(xxx)xxx-xx-xx***, пример: **+7(901)502-04-56**
>  - указан телефон, на который зарегистрирован аккаунт пользователя   
>  
> :green_square: изменить телефон нельзя, инпут неактивен    
### инпут адреса доставки:  
>:green_square: адрес доставки отображается корректно, указан верно  
>    критерии:   
>  - формат отображения : **"*Город, Улица, №дома*"** , пример: **"Москва, Измайловский Проезд, 16 к.2"**
>  - указан адрес, который отображался у пользователя в хедере перед переходом на страницу оформления заказа   
>  
>:green_square: изменить адрес нельзя, инпут неактивен    
### инпут подъезда:
>:green_square: можно ввести символы ascii    
>:green_square: можно ввести символы русского алфавита      
>:green_square: можно оставить инпут пустым  
>:green_square: невозможно ввести длинное значение (>4 символов)  
### инпут домофона:
>:green_square: можно ввести символы ascii    
>:green_square: можно ввести символы русского алфавита  
>:green_square: можно оставить инпут пустым  
>:green_square: невозможно ввести длинное значение (>10 символов)  
### инпут этажа:
>:green_square: можно ввести символы ascii    
>:green_square: можно ввести символы русского алфавита
>:green_square: можно оставить инпут пустым  
>:green_square: невозможно ввести длинное значение (>3 символов)  
### инпут квартиры:
>:green_square: можно ввести символы ascii    
>:green_square: можно ввести символы русского алфавита  
>:green_square: можно оставить инпут пустым  
>:green_square: невозможно ввести длинное значение (>4 символов)  
### radio button способа оплаты  
>:green_square: способ оплаты по-умолчанию: "онлайн оплата"  
>:red_square: можно сменить способ оплаты  
   **описание бага:** невозможно сменить способ оплаты, кнопки "Google Pay", "Sber Pay" неактивны, при наведении на них некорректно отображается курсор (text)   
   ![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/pay_way.png)  
   ![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/pay_way1.png)

### кнопка "Оплатить заказ" 
>:green_square: при наведении курсора на кнопку появляется тень  
>:green_square: при нажатии на кнопку, происходит переход на страницу истории  статусов заказов /orderHistory  
       
## **Блок с корзиной**
![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/basket_with_promo.png)
![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/basket_without_promo.png)
### название ресторана:
>:green_square: название ресторана отображается корректно и указано верно  
>    критерии:   
>  - формат отображения : **"Ваш заказ в ресторане: *Название_ресторана*"** , пример: **"Ваш заказ в ресторане: Black Star Burger"**
>  - указано название того ресторана, в котором пользователь делает заказ  
>  
### название промокода:
>:green_square: если промокод применен, то название промокода отображается корректно и указано верно  
>    критерии:   
>  - формат отображения : **"Промокод *Название_промокода* применен ✅"** , пример: **"Промокод SBW100 применен ✅"**
>  - указан тот промокод, который пользователь применил ранее, нажав на него на главной странице  
> 
>:green_square: блок с промокодом не отображается при отсутсвии промокода   
### контейнер с корзиной:
>:green_square: вертикальный скроллбар появляется при 3х и более блюдах в корзине  
### карточка продукта в корзине:  
>:green_square: картинка соответствует этому блюду   
>:green_square: название блюда соответствует этому блюду     
>:green_square: цена блюда соответствует этому блюду  
>:green_square: если промокод не применен, цена блюда с учетом скидки не отображается  
>:green_square: дополнительная информация о блюде (масса, ккал) соответствует этому блюду   
>:green_square: количество порций конкретного блюда = количеству порций, которое добавил пользователь  
>:green_square: количество порций блюда можно увеличить с помощью кнопки ":heavy_plus_sign:"  
>:green_square: количество порций блюда можно уменьшить с помощью кнопки ":heavy_minus_sign:"  
>:green_square: при уменьшении с помощью кнопки ":heavy_minus_sign:" количества блюда до 0, при условии, что это единственное блюдо в корзине, происходит редирект на страницу ресторана, в котором был заказ  
>:green_square: при уменьшении с помощью кнопки ":heavy_minus_sign:" количества блюда до 0, при условии, что это не единственное блюдо в корзине, карточка данного блюда удаляется  
### "Итого":
>:green_square: итоговая стоимость расчитана в соответствии с количеством блюд, ценой блюд, примененным промокодом  
>:green_square: итоговая стоимость соответствующе изменяется при увеличении количества блюд в корзине  
>:green_square: итоговая стоимость соответствующе изменяется при уменьшении количества блюд в корзине  
>:green_square: итоговая стоимость соответствующе изменяется при удалении блюда из корзины  
### "Доставка":
>:green_square: при итоговой стоимости товара < минимальной стоимости для бесплатной доставки данного ресторана, цена доставки = 99Р  
>:red_square: при итоговой стоимости товара >= минимальной стоимости для бесплатной доставки данного ресторана, цена доставки = 0Р 
   **описание бага:** при итоговой стоимости товара = минимальной стоимости для бесплатной доставки данного ресторана, отображается, что цена доставки = 99 Р  
![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/basket.png)
### "Суммарная скидка":
>:green_square: суммарная скидка = (цена без скидки) - (цена со скидкой)  
>:green_square: если промокод не применен, суммарная скидка = 0Р  
### блок с информацией о цене доставки:
>:green_square: при итоговой стоимости товара < минимальной стоимости для бесплатной доставки данного ресторана, отображается, на сколько еще необходимо заказать, чтобы доставка была бесплатна  
>:red_square: при итоговой стоимости товара >= минимальной стоимости для бесплатной доставки данного ресторана, отображается, что доставка будет бесплатна  
   **описание бага:** при итоговой стоимости товара = минимальной стоимости для бесплатной доставки данного ресторана, отображается, что необходимо заказать еще на 0 рублей.  
![](https://github.com/Natali-Skv/technopark_qa_homework-1-/blob/VVT-i/screens/basket.png)
       
