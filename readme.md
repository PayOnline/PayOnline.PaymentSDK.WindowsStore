﻿Общее описание
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
Visual Studio 2012 или выше
Windows 8 или Windows Server 2012 или выше
.NET for Windows Store apps 4.5 или выше

Пространство имен PayOnline.PaymentSDK
================================
Перечисления
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