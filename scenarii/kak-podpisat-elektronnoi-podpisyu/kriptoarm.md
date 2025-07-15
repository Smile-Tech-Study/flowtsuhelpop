---
description: >-
  После установки КриптоПро и Сертификата ГУЦ необходимо установить КриптоАРМ,
  именно в этом модуле проходит подписание документов.
---

# КриптоАРМ

Перейдите на сайт [https://cryptoarm.ru/cryptoarm-5/](https://cryptoarm.ru/cryptoarm-5/)  и приобретите модуль КриптоАРМ.

## Установка КриптоАРМ 6

{% file src="../../.gitbook/assets/КриптоАРМ 6.pdf" %}

## Установка КриптоАРМ ГОСТ 3

{% file src="../../.gitbook/assets/КриптоАРМ ГОСТ 3.pdf" %}

## Установка КриптоАРМ 5

1. После запуска  выбрать "Настраиваемая установка", затем "Далее".

<figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

2. Выбрать для "КриптоАРМ" вариант «Этот компонент и его подкомпоненты будут установлены на локальный жесткий диск» и нажать "Далее".

<figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

3. Ознакомиться и принять "Лицензионное соглашение".

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

&#x20;4\. После установки нажать "Готово".

<figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

:::info

**После завершения установки необходимо перезагрузить компьютер.**&#x20;

:::

## Настройка КриптоАРМ _(10 шагов и вы у цели!)_

1. Открыть КриптоАРМ (Для КриптоАРМ на рабочем столе будет создан ярлык, необходимо кликнуть по нему).

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

2. &#x20; В пункте меню "Помощь" установить лицензию.

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

3. Прописать лицензионные ключи и нажать "Ок".&#x20;
4. Выбрать в меню КриптоАРМ "Профили" - "Управление профилями" -"Создать".

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

5\. В пункте «Общие» прописать имя профиля и указать сертификат пользователя с помощью кнопки «Выбрать».

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

6. В пункте "Подпись" установить формат подписи на "Усовершенствованная".&#x20;

:::danger

**Для создания открепленной подписи установить галочку "Сохранять подпись в отдельном файле" (без установленной галочки будет создаваться прикрепленная подпись).**

:::

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

7. В пункте "TSP" в поле "Адрес службы штампов времени" указать адрес службы штампов времени (например, [http://tax4.tensor.ru/tsp/tsp.srf](http://tax4.tensor.ru/tsp/tsp.srf)).

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

8. В пункте "OCSP" в поле "Адрес сервера" необходимо указать адрес OCSP сервера, указанный указан в свойствах сертификата пользователя.

-Открыть Certificates через меню Пуск.

-Выбрать пункт "Доступ к информации о центрах сертификации"/Authority Information Access.

-Скопировать URL.&#x20;

<figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

-Вставить полученный URL&#x20;

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

9. Выбрать в пункте "Профили" созданный профиль "По умолчанию".

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

10. Выполнить настройку в пункте "Режимы" (по желанию - необязательное условие).

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

**Настройка завершена. Поздравляем!**\


## Подробнее о подписании документа

:::danger

Во время подписания на компьютере должен быть доступ к электронной подписи. То есть, если она на USB-накопителе, то он должен быть вставлен в компьютер.

:::

1. Открыть установленный КриптоАРМ (ярлык на рабочем столе).
2. Нажать "Подписать".
3. Выбрать файл для подписи.

<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

4. Ввести пин-код вашей Электронной подписи и нажмите "ОК".

<figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

В каталоге на компьютере будет 2 файла:&#x20;

* сам документ;
* файл с открепленной подписью в формате sig.

&#x20;Файл с открепленной подписью в формате SIG необходимо загрузить во Flow.

<figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

:::info

Итоговый документ - бланк документа и два файла в формате SIG

:::
