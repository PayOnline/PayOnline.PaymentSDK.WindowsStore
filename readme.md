Общее описание
================================
Payment SDK PayOnline позволяет разработчикам приложений Windows Store и Windows Phone 8 принимать платежи по банковским картам.
Payment SDK PayOnline позволяет принимать платежи по банковским картам VISA, MasterCard, Maestro в приложении, без перехода в браузер.
Размер комиссии составляет 4%. Выплаты производятся на существующий расчетный счет владельца в течение 5 рабочих дней с момента совершения платежа.
Платежным сервис-провайдером Payment SDK является международный процессинговый центр PayOnline, сертифицированный PCI DSS Level 1.
Все операции проводятся на веб-сайте secure.payonlinesystem.com
Payment SDK поддерживает 3DS  (Verified by Visa и MasterCard SecureCode), что позволяет обеспечить высокий уровень безопасности платежей.
Payment SDK представляет собой библиотеку кода, которая инкапсулирует работы с API на сетевом уровне и предоставляет программные интерфейсы.
Разработчикам приложений предоставляется подробное руководство по работе с Payment SDK [ссылка на страницу с руководством].
Библиотеки реализованы для Windows Store и Windows Phone 8 приложений (на данный момент для C#\XAML).

Требования
-------------------------
* Visual Studio 2012 или выше
* Windows 8 или Windows Server 2012 или выше
* .NET for Windows Store apps 4.5 или выше

Пространство имен PayOnline.PaymentSDK
-------------------------
### Перечисления ###
-------------------------
<table>
 <tr>
  <td>
Currency
  </td>
  <td>
Список поддерживаемых валют
  </td>
 </tr>
 <tr>
  <td>
Result
  </td>
  <td>
Результат выполнения запроса к процессингову центру
  </td>
 </tr>
 <tr>
  <td>
  Status
  </td>
  <td>
  Статус трансакции в платежной системе PayOnline
  </td>
 </tr>
</table>

### Классы ###
-------------------------
<table>
 <tr>
  <td>
  Error
  </td>
  <td>
  Информация об ошибке, возникшей в процессе обработки запроса
  </td>
 </tr>
 <tr>
  <td>GetRequest
  </td>
  <td>Запрос на получение информации о транзакции
  </td>
 </tr>
 <tr>
  <td>PayRequest
  </td>
  <td>Запрос на авторизацию средств на карте плательщика
  </td>
 </tr>
 <tr>
  <td>PayResponse
  </td>
  <td>Результат выполнения авторизации денежных средств на банковской карте
  </td>
 </tr>
 <tr>
  <td>Processing
  </td>
  <td>Представляет реализацию интерфейс процессингового центра PayOnline
  </td>
 </tr>
 <tr>
  <td>ThreeDsCompletedEventArgs
  </td>
  <td>Предоставляет данные для события ThreeDsCompleted</p>
  </td>
 </tr>
 <tr>
  <td>ThreeDsData
  </td>
  <td>Информация, возвращаемая платежной системой, для прохождения проверки
  на стороне банка-эмитента
  </td>
 </tr>
 <tr>
  <td>TransactionInfo
  </td>
  <td>Информация о трансакции
  </td>
 </tr>
 <tr>
  <td>WebViewExtentions
  </td>
  <td>Класс-расширение для элемента управления WebView.
  </td>
 </tr>
</table>

### Интерфесы ###
-------------------------
<table>
 <tr>
  <td>IConfiguration
  </td>
  <td>Предоставляет интерфейс для настройки среды выполнения
  </td>
 </tr>
 <tr><td>IProcessing
  </td>
  <td>Интерфейс процессингового центра PayOnline
  </td>
 </tr>
</table>

## Перечисления ##
-------------------------

### Currency ###
-------------------------

Список поддерживаемых валют

<table>
 <tr>
  <td>Unknown
  </td>
  <td>Неизвестная валюта. Возвращается при вызове метода PayOnline.PaymentSDK.IProcessing.Get если трансакция не найдена.
  Нельзя использовать в методеPayOnline.PaymentSDK.IProcessing.Pay
  </td>
 </tr>
 <tr>
  <td>Usd
  </td>
  <td>Доллар США
  </td>
 </tr>
 <tr>
  <td>Rub
  </td>
  <td>Российский рубль
  </td>
 </tr>
 <tr>
  <td>Eur
  </td>
  <td>Евро
  </td>
 </tr>
</table>

### Result ###
-------------------------
Результат выполнения запроса к процессингову центру PayOnline

<table>
 <tr>
  <td>Success
  </td>
  <td>Авторизация прошла успешно, либо трансакция найдена
  </td>
 </tr>
 <tr>
  <td>Error
  </td>
  <td>В процессе выполнения запроса, произошли ошибки
  </td>
 </tr>
 <tr>
  <td>Declined
  </td>
  <td>Запрос на авторизацию средств отклонен
  </td>
 </tr>
 <tr>
  <td>CompleteValidation
  </td>
  <td>Необходимо пройти дополнительную проверку на стороне банка-эмитента
  </td>
 </tr>
 <tr>
  <td>NotFound
  </td>
  <td>Трансакция не найдена
  </td>
 </tr>
</table>

### Status ###
--------------

Статус трансакции в платежной системе PayOnline

<table>
 <tr>
  <td>Unknown
  </td>
  <td>Неизместный статус, возвращается, если трансакция не найдена</p>
  </td>
 </tr>
 <tr>
  <td>Pending
  </td>
  <td>Успешная трансакция, деньги на карте авторизованы, но могут быть разблокированы
  </td>
 </tr>
 <tr>
  <td>Settled
  </td>
  <td>Успешная трансакция, операция по переводу денежных средств завершена
  </td>
 </tr>
 <tr>
  <td>Voided
  </td>
  <td>Трансакция отменена
  </td>
 </tr>
 <tr>
  <td>PreAuthorized
  </td>
  <td>Успешная трансакция, деньги авторизованы, однако необходимо подтверждение мерчанта
  </td>
 </tr>
 <tr>
  <td>Declined
  </td>
  <td>Отклоненная трансакция
  </td>
 </tr>
</table>

## Классы ##
--------------

### Error ###

Информация об ошибке, возникшей в процессе обработки запроса

#### Свойства ####

<table>
 <tr>
  <td>Code
  </td>
  <td>int
  </td>
  <td>Код ошибки
  </td>
 </tr>
 <tr>
  <td>Message
  </td>
  <td>string
  </td>
  <td>Краткая информация об ошибке
  </td>
 </tr>
</table>

* Примечание: * Для получения дополнительной информации необходимо связаться со службой поддержки

### GetRequest ###

Запрос на получение информации о транзакции

#### Свойства ####

<table>
 <tr>
  <td>TransactionId
  </td>
  <td>long
  </td>
  <td>ID трансакции в системе процессингового центра PayOnline
  </td>
 </tr>
</table>

### PayRequest ####

Запрос на авторизацию средств на карте плательщика

#### Свойства ####

<table>
 <tr>
  <td>OrderId
  </td>
  <td>string
  </td>
  <td>ID заказа в вашей системе
  </td>
 </tr>
 <tr>
  <td>Amount
  </td>
  <td>decimal
  </td>
  <td>Сумма платежа
  </td>
 </tr>
 <tr>
  <td>Currency
  </td>
  <td>Currency
  </td>
  <td>Валюта платежа
  </td>
 </tr>
 <tr>
  <td>Email
  </td>
  <td>string
  </td>
  <td>Электронная почта плательщика
  </td>
 </tr>
 <tr>
  <td>CardHolderName
  </td>
  <td>string
  </td>
  <td>Имя держателя карты, указанное на банковской карте
  </td>
 </tr>
 <tr>
  <td>CardNumber
  </td>
  <td>string
  </td>
  <td>Номер банковской карты, указанный на банковской карте
  </td>
 </tr>
 <tr>
  <td>CardExpMonth
  </td>
  <td>int
  </td>
  <td>Месяц окончания действия банковской карты
  </td>
 </tr>
 <tr>
  <td>CardExpYear
  </td>
  <td>int
  </td>
  <td>Год окончания действия банковской карты
  </td>
 </tr>
 <tr>
  <td>CardCvv
  </td>
  <td>int
  </td>
  <td>Секретный код, указанный на обратной стороне банковской карты
  </td>
 </tr>
</table>

### PayResponse ###

Результат выполнения авторизации денежных средств на банковской карте

#### Свойства ####

<table>
 <tr>
  <td>TransactionId
  </td>
  <td>long
  </td>
  <td>ID трансакции в системе PayOnline
  </td>
 </tr>
 <tr>
  <td>Result
  </td>
  <td>Result
  </td>
  <td>Результат выполнения операции
  </td>
 </tr>
 <tr>
  <td>Code
  </td>
  <td>int
  </td>
  <td>Код ответа
  </td>
 </tr>
 <tr>
  <td>Status
  </td>
  <td>Status
  </td>
  <td>Статус трансакции
  </td>
 </tr>
 <tr>
  <td>ThreeDs
  </td>
  <td>ThreeDsData
  </td>
  <td>Информация, возвращаемая платежной системой, для прохождения проверки  на стороне банка эмитента
  </td>
 </tr>
 <tr>
  <td>ErrorInfo
  </td>
  <td>Error
  </td>
  <td>Информация об ошибке, если она произошла в момент обработки запроса
  </td>
 </tr>
</table>

### Processing ###

Представляет реализацию интерфейса процессингового центра PayOnline

#### Конструкторы ####

<table>
 <tr>
  <td>Processing(IConfiguration configuration)</p>
  </td>
  <td>Инициализирует класс Processing объектом конфигурации среды выполнения
  </td>
 </tr>
</table>

 #### Методы ####

<table>
 <tr>
  <td>Task&lt;PayResponse&gt; Pay(PayRequest payRequest)
  </td>
  <td>Операция проведения платежа
  </td>
 </tr>
 <tr>
  <td>Task&lt;TransactionInfo&gt; Get(GetRequest findRequest)
  </td>
  <td>Получение информации о трансакции
  Возвращается информацию только об успешных трансакциях
  </td>
 </tr>
</table>

#### События ####

<table>
 <tr>
  <td>EventHandler&lt;ThreeDsCompletedEventArgs&gt; ThreeDsCompleted
  </td>
  <td>Событие возникает после завершения прохождения проверки 3D-S
  </td>
 </tr>
</table>

### ThreeDsCompletedEventArgs ###

Предоставляет данные для события ThreeDsCompleted

#### Свойства ####

<table>
 <tr>
  <td>Transaction
  </td>
  <td>PayResponse
  </td>
  <td>Информация о платеже
  </td>
 </tr>
</table>


### ThreeDsData ###

Информация, возвращаемая платежной системой, для прохождения
проверки на стороне банка-эмитента

#### Свойства ####

<table>
 <tr>
  <td>PaReq
  </td>
  <td>string
  </td>
  <td>Запрос на аутентификацию плательщика
  </td>
 </tr>
 <tr>
  <td>AcsUrl
  </td>
  <td>string
  </td>
  <td>Страница сайта банка-эмитента
  </td>
 </tr>
 <tr>
  <td>MD
  </td>
  <td>string
  </td>
  <td>Информация о мерчанте
  </td>
 </tr>
</table>

### TransactionInfo ###

Информация о трансакции

#### Свойства ####

<table>
 <tr>
  <td>
  TransactionId
  </td>
  <td>long
  </td>
  <td>ID трансакции в системе PayOnline
  </td>
 </tr>
 <tr>
  <td>Amount
  </td>
  <td>decimal
  </td>
  <td>Сумма трансакции
  </td>
 </tr>
 <tr>
  <td>Currency
  </td>
  <td>Currency
  </td>
  <td>Валюта трансакции
  </td>
 </tr>
 <tr>
  <td>OrderId
  </td>
  <td>string
  </td>
  <td>ID заказа
  </td>
 </tr>
 <tr>
  <td>DateTime
  </td>
  <td>DateTime
  </td>
  <td>Дата и время создания трансакции по UTC (Всемирное координированное
  время)
  </td>
 </tr>
 <tr>
  <td>Result
  </td>
  <td>Result
  </td>
  <td>Результат выполнения операции
  </td>
 </tr>
 <tr>
  <td>Status
  </td>
  <td>Status
  </td>
  <td>Статус трансакции
  </td>
 </tr>
 <tr>
  <td>ErrorInfo
  </td>
  <td>Error
  </td>
  <td>Информация об ошибке, если она произошла в момент обработки запроса
  </td>
 </tr>
</table>

### WebViewExtentions ### 

Класс-расширение для элемента управления WebView

#### Методы ####

<table>
 <tr>
  <td>static void NavigateToAcsUrl(this WebView webView, PayResponse payResponse, IProcessing processing)
  </td>
  <td>Метод расширение для элемента управления WebView. Происходит переход на страницу банка эмитента для прохождения проверки
  </td>
 </tr>
</table>


