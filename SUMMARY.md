---
title: Содержание
order: 1
---



[html]

<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Структура справки Flow</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Golos+Text:wght@400;500;600&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Golos Text', system-ui, sans-serif;
    background: #F7FAFD;
    color: #1A1A2E;
    padding: 2rem 1.5rem 3rem;
    min-height: 100vh;
  }

  /* ── Header ── */
  .header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 0.35rem;
  }
  .logo {
    width: 36px; height: 36px;
    background: #1A6FD4;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .header-title {
    font-size: 18px;
    font-weight: 600;
    color: #1A1A2E;
    letter-spacing: -0.3px;
  }
  .header-sub {
    font-size: 13px;
    color: #6B7A8D;
    margin-bottom: 1.25rem;
    padding-left: 48px;
  }

  /* ── Legend ── */
  .legend {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    margin-bottom: 1.25rem;
    padding: 9px 14px;
    background: #fff;
    border: 1px solid #D8E4F0;
    border-radius: 8px;
  }
  .leg { display: flex; align-items: center; gap: 5px; font-size: 11.5px; color: #6B7A8D; }
  .leg-dot { width: 8px; height: 8px; border-radius: 50%; }

  /* ── Flow path label ── */
  .flow-label {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.8px;
    color: #6B7A8D;
    margin-bottom: 0.75rem;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .flow-label::before, .flow-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #D8E4F0;
  }

  /* ── Grid ── */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
    gap: 10px;
  }

  /* ── Card ── */
  .card {
    background: #fff;
    border: 1px solid #D8E4F0;
    border-radius: 12px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    cursor: pointer;
    transition: box-shadow 0.18s, transform 0.18s, border-color 0.18s;
    position: relative;
  }
  .card:hover {
    box-shadow: 0 4px 18px rgba(26,111,212,0.11);
    transform: translateY(-2px);
  }
  .card:active { transform: translateY(0); }

  /* Весь верх карточки — кликабельная ссылка */
  .card-link {
    display: block;
    text-decoration: none;
    color: inherit;
  }

  /* ── Accent stripe ── */
  .card-accent { height: 3px; width: 100%; display: block; }

  /* ── Card head ── */
  .card-head {
    padding: 12px 14px 10px;
    display: flex;
    align-items: flex-start;
    gap: 10px;
  }
  .card-icon {
    width: 32px; height: 32px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 15px;
    font-weight: 600;
    flex-shrink: 0;
    margin-top: 1px;
  }
  .card-meta { flex: 1; min-width: 0; }
  .card-title {
    font-size: 13px;
    font-weight: 600;
    color: #1A1A2E;
    line-height: 1.35;
    transition: color 0.15s;
  }
  .card-desc { font-size: 11px; color: #6B7A8D; margin-top: 2px; line-height: 1.4; }

  /* ── Pages list ── */
  .card-pages {
    list-style: none;
    border-top: 1px solid #E8EFF7;
    padding: 8px 14px 12px;
    flex: 1;
  }
  .page-item {
    display: flex;
    align-items: flex-start;
    gap: 6px;
    padding: 3px 0;
    font-size: 11.5px;
    color: #6B7A8D;
    line-height: 1.4;
  }
  .page-item a {
    color: #6B7A8D;
    text-decoration: none;
    transition: color 0.15s;
  }
  .page-item a:hover { color: #1A6FD4; text-decoration: underline; }
  .page-dot {
    width: 4px; height: 4px;
    border-radius: 50%;
    background: #C8D8E8;
    flex-shrink: 0;
    margin-top: 5px;
  }
  /* Текст без ссылки в строке */
  .page-text { color: #6B7A8D; }

  /* ── Tags ── */
  .tag {
    font-size: 9.5px;
    font-weight: 600;
    padding: 1px 5px;
    border-radius: 3px;
    white-space: nowrap;
    line-height: 1.7;
    flex-shrink: 0;
    display: inline-block;
  }
  .tag-new   { background: #E2F4EE; color: #0A6B50; }
  .tag-inter { background: #E4EFFC; color: #1558A8; }
  .tag-move  { background: #FDF0D8; color: #9C5F08; }
  .tag-del   { background: #FDEAEA; color: #992424; }

  /* ── Color themes ── */
  [data-color="blue"]   .card-accent { background: #1A6FD4; }
  [data-color="blue"]   .card-icon   { background: #E4EFFC; color: #1558A8; }
  [data-color="blue"]:hover           { border-color: #4A90D9; }
  [data-color="blue"]:hover .card-title { color: #1A6FD4; }

  [data-color="teal"]   .card-accent { background: #0F8A6A; }
  [data-color="teal"]   .card-icon   { background: #E0F4EE; color: #0A6B50; }
  [data-color="teal"]:hover           { border-color: #2AAE88; }
  [data-color="teal"]:hover .card-title { color: #0F8A6A; }

  [data-color="purple"] .card-accent { background: #5A47C0; }
  [data-color="purple"] .card-icon   { background: #EDEAFC; color: #4435A0; }
  [data-color="purple"]:hover         { border-color: #7B6BD6; }
  [data-color="purple"]:hover .card-title { color: #5A47C0; }

  [data-color="amber"]  .card-accent { background: #C47A12; }
  [data-color="amber"]  .card-icon   { background: #FDF0D8; color: #9C5F08; }
  [data-color="amber"]:hover          { border-color: #E09930; }
  [data-color="amber"]:hover .card-title { color: #C47A12; }

  [data-color="gray"]   .card-accent { background: #5C6B7A; }
  [data-color="gray"]   .card-icon   { background: #EEF0F3; color: #4A5868; }
  [data-color="gray"]:hover           { border-color: #8A9AAA; }
  [data-color="gray"]:hover .card-title { color: #4A5868; }

  /* ── Hint ── */
  .hint {
    margin-top: 1.25rem;
    font-size: 12px;
    color: #6B7A8D;
    background: #fff;
    border: 1px solid #D8E4F0;
    border-radius: 8px;
    padding: 10px 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .hint-icon {
    width: 18px; height: 18px;
    border-radius: 50%;
    background: #E4EFFC;
    color: #1A6FD4;
    display: flex; align-items: center; justify-content: center;
    font-size: 10px;
    font-weight: 700;
    flex-shrink: 0;
  }
</style>
</head>
<body>

<div class="header">
  <div class="logo">
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
      <path d="M4 6h16M4 12h10M4 18h13" stroke="white" stroke-width="2.2" stroke-linecap="round"/>
    </svg>
  </div>
  <div class="header-title">Структура справки Flow</div>
</div>
<div class="header-sub">Справка для образовательных партнёров (ОП) — 9 разделов</div>

<div class="legend">
  <div class="leg"><div class="leg-dot" style="background:#0F8A6A"></div>Новый раздел</div>
  <div class="leg"><div class="leg-dot" style="background:#1A6FD4"></div>Добавить интерактив</div>
  <div class="leg"><div class="leg-dot" style="background:#C47A12"></div>Перенести / переименовать</div>
  <div class="leg"><div class="leg-dot" style="background:#992424"></div>Удалить из меню</div>
</div>

<div class="flow-label">Путь пользователя</div>

<div class="grid">

  <!-- 1 -->
  <div class="card" data-color="blue">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/README" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">①</div>
        <div class="card-meta">
          <div class="card-title">Начало работы</div>
          <div class="card-desc">Вход, роли, глоссарий</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><span class="tag tag-inter">интерактив</span>&nbsp;<span class="page-text">Схема ролей ОП / ФО / ЦЗН</span></li>
      <li class="page-item"><span class="tag tag-inter">интерактив</span>&nbsp;<span class="page-text">Путь пользователя по шагам</span></li>
      <li class="page-item"><span class="tag tag-new">новый</span>&nbsp;<span class="page-text">Глоссарий</span></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/kak-voiti-s-yandeks.klyuch" target="_blank" rel="noopener">Вход через Яндекс ID</a></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/dvukhfaktornaya-autentifikaciya" target="_blank" rel="noopener">Вход через 2FA</a></li>
    </ul>
  </div>

  <!-- 2 -->
  <div class="card" data-color="teal">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/spravochniki" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">②</div>
        <div class="card-meta">
          <div class="card-title">Справочники</div>
          <div class="card-desc">Организация, договор, стоимость</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/spravochniki/kartochka-organizacii" target="_blank" rel="noopener">Карточка организации</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/spravochniki/README" target="_blank" rel="noopener">Договор на обучение</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/spravochniki/README/dopolnitelnoe-soglashenie" target="_blank" rel="noopener">Доп. соглашение</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/spravochniki/predlozhenie-o-stoimosti-dlya-programmy" target="_blank" rel="noopener">Предложение о стоимости</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/spravochniki/srednyaya-stoimost-za-programmu" target="_blank" rel="noopener">Средняя стоимость</a></li>
    </ul>
  </div>

  <!-- 3 -->
  <div class="card" data-color="teal">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/programmy" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">③</div>
        <div class="card-meta">
          <div class="card-title">Программы</div>
          <div class="card-desc">Создание и публикация</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/programmy/rabota-s-programmoi" target="_blank" rel="noopener">Работа с программой</a></li>
      <li class="page-item"><span class="tag tag-inter">интерактив</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/programmy/statusy-programm" target="_blank" rel="noopener">Статусы программ</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/programmy/publikaciya-programmy-na-portale-rabota-rossii" target="_blank" rel="noopener">Публикация на РР</a></li>
    </ul>
  </div>

  <!-- 4 -->
  <div class="card" data-color="blue">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">④</div>
        <div class="card-meta">
          <div class="card-title">Потоки</div>
          <div class="card-desc">Потоки и отчётные документы</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/potok" target="_blank" rel="noopener">Поток</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/gruppa" target="_blank" rel="noopener">Группа</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/zadanie" target="_blank" rel="noopener">Задание</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/zhurnal-i-skrinshoty" target="_blank" rel="noopener">Журнал и скриншоты</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/akt" target="_blank" rel="noopener">Акт</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/otchyot" target="_blank" rel="noopener">Отчёт</a></li>
    </ul>
  </div>

  <!-- 5 -->
  <div class="card" data-color="blue">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/zayavki" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">⑤</div>
        <div class="card-meta">
          <div class="card-title">Заявки</div>
          <div class="card-desc">Обработка заявок граждан</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/zayavki/kak-rabotat-so-stranicey-zayavok" target="_blank" rel="noopener">Страница заявок</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/zayavki/kartochka-zayavki" target="_blank" rel="noopener">Карточка заявки</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/zayavki/README" target="_blank" rel="noopener">Проверка документов</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/zayavki/zamena-dokumentov" target="_blank" rel="noopener">Замена документов</a></li>
      <li class="page-item"><span class="tag tag-inter">интерактив</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/zayavki/statusy-zayavok" target="_blank" rel="noopener">Статусы заявок</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/zayavki/dogovor-podpisannyi-vsemi-storonami" target="_blank" rel="noopener">Договор всех сторон</a></li>
    </ul>
  </div>

  <!-- 6 -->
  <div class="card" data-color="purple">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">⑥</div>
        <div class="card-meta">
          <div class="card-title">Приказы</div>
          <div class="card-desc">Зачисление и отчисление</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README/avtomaticheskii-vypusk-prikazov" target="_blank" rel="noopener">Автоматический выпуск</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README/ruchnoi-vypusk-prikazov" target="_blank" rel="noopener">Ручной выпуск</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README/vnesenie-dannykh-o-prikazakh-na-portal-rr" target="_blank" rel="noopener">Внесение данных на РР</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/uspevaemost-poseshaemost" target="_blank" rel="noopener">Успеваемость / посещаемость</a></li>
    </ul>
  </div>

  <!-- 7 -->
  <div class="card" data-color="purple">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README-2" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">⑦</div>
        <div class="card-meta">
          <div class="card-title">Документы о квалификации</div>
          <div class="card-desc">Выпуск и массовый импорт</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README-2" target="_blank" rel="noopener">Выпуск документов</a></li>
      <li class="page-item"><div class="page-dot"></div><a href="https://www.flow-crm.study/flowtsuhelpop/prikazy-dokumenty-o-kvalifikacii/README-2/massovyi-import" target="_blank" rel="noopener">Массовый импорт</a></li>
      <li class="page-item"><span class="tag tag-new">новый</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/potoki-otchyotnye-dokumenty/eksport-dlya-fis-frdo" target="_blank" rel="noopener">Экспорт для ФИС ФРДО</a></li>
    </ul>
  </div>

  <!-- 8 -->
  <div class="card" data-color="gray">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/scenarii" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">⑧</div>
        <div class="card-meta">
          <div class="card-title">Технические инструкции</div>
          <div class="card-desc">Раньше — часть «Сценариев»</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/digital_signature" target="_blank" rel="noopener">Электронная подпись</a></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/vipnet-instrukciya-po-podklyucheniyu" target="_blank" rel="noopener">ViPNet</a></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/kak-sdelat-rassylku" target="_blank" rel="noopener">Рассылка</a></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/obshee/sinkhronizaciya-dannykh-po-programme-potoku-iz-odin-vo-flow" target="_blank" rel="noopener">Синхронизация с Odin</a></li>
    </ul>
  </div>

  <!-- 9 -->
  <div class="card" data-color="amber">
    <a class="card-link" href="https://www.flow-crm.study/flowtsuhelpop/scenarii/obshee" target="_blank" rel="noopener">
      <span class="card-accent"></span>
      <div class="card-head">
        <div class="card-icon">⑨</div>
        <div class="card-meta">
          <div class="card-title">Частые вопросы</div>
          <div class="card-desc">FAQ — новый раздел</div>
        </div>
      </div>
    </a>
    <ul class="card-pages">
      <li class="page-item"><span class="tag tag-new">новый</span>&nbsp;<span class="page-text">Когда гражданин займёт квоту?</span></li>
      <li class="page-item"><span class="tag tag-new">новый</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/obshee/kak-spiskom-posmotret-kolichestvo-zayavok-na-potok" target="_blank" rel="noopener">Кол-во заявок на поток</a></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/obshee/roli-v-sisteme-flow" target="_blank" rel="noopener">Роли в системе</a></li>
      <li class="page-item"><span class="tag tag-move">перенос</span>&nbsp;<a href="https://www.flow-crm.study/flowtsuhelpop/scenarii/lichnyy-kabinet-grazhdanina" target="_blank" rel="noopener">ЛК гражданина</a></li>
      <li class="page-item"><span class="tag tag-del">удалить</span>&nbsp;<span class="page-text">Ошибки и опечатки</span></li>
      <li class="page-item"><span class="tag tag-del">удалить</span>&nbsp;<span class="page-text">Помощь (внешняя ссылка)</span></li>
    </ul>
  </div>

</div>

<div class="hint">
  <div class="hint-icon">i</div>
  Шапка карточки открывает раздел целиком. Ссылки внутри — конкретные страницы. Всё открывается в новой вкладке.
</div>

</body>
</html>

[/html]

## Справочники

-  [Карточка организации](./spravochniki/kartochka-organizacii)

-  [Договор на организацию обучения](./spravochniki/README/_index)

   -  [Дополнительное соглашение](./spravochniki/README/dopolnitelnoe-soglashenie)

-  [Предложение о стоимости для программы](./spravochniki/predlozhenie-o-stoimosti-dlya-programmy)

-  [Средняя стоимость за программу](./spravochniki/srednyaya-stoimost-za-programmu)

## Программы

-  [Публикация программы на портале Работа России](./programmy/publikaciya-programmy-na-portale-rabota-rossii)

-  [Работа с программой](./programmy/rabota-s-programmoi)

-  [Статусы программ](./programmy/statusy-programm)

## Потоки/Отчётные документы

-  [Поток](./potoki-otchyotnye-dokumenty/potok)

-  [Группа](./potoki-otchyotnye-dokumenty/gruppa)

-  [Задание](./potoki-otchyotnye-dokumenty/zadanie)

-  [Журнал и скриншоты](./potoki-otchyotnye-dokumenty/zhurnal-i-skrinshoty)

-  [Акт](./potoki-otchyotnye-dokumenty/akt)

-  [Отчёт](./potoki-otchyotnye-dokumenty/otchyot)

-  [Экспорт для ФИС ФРДО](./potoki-otchyotnye-dokumenty/eksport-dlya-fis-frdo)

## Заявки

-  [Карточка заявки](./zayavki/kartochka-zayavki)

-  [Проверка документов](./zayavki/README/_index)

   -  [Сроки загрузки и проверки документов](./zayavki/README/sroki-zagruzki-i-proverki-dokumentov)

   -  [Подписание Договора о намерениях](./zayavki/README/podpisanie-dogovora-o-namereniyakh)

-  [Замена документов](./zayavki/zamena-dokumentov/_index)

-  [Статусы заявок](./zayavki/statusy-zayavok)

-  [Договор, подписанный всеми сторонами](./zayavki/dogovor-podpisannyi-vsemi-storonami)

## Приказы/Документы о квалификации

-  [Приказы](./prikazy-dokumenty-o-kvalifikacii/README/_index)

   -  [Автоматический выпуск приказов](./prikazy-dokumenty-o-kvalifikacii/README/avtomaticheskii-vypusk-prikazov)

   -  [Ручной выпуск приказов](./prikazy-dokumenty-o-kvalifikacii/README/ruchnoi-vypusk-prikazov)

   -  [Внесение данных о приказах на портал РР](./prikazy-dokumenty-o-kvalifikacii/README/vnesenie-dannykh-o-prikazakh-na-portal-rr)

-  [Успеваемость/посещаемость](./prikazy-dokumenty-o-kvalifikacii/uspevaemost-poseshaemost)

-  [Документы о квалификации](./prikazy-dokumenty-o-kvalifikacii/README-2/_index)

   -  [Массовый импорт](./prikazy-dokumenty-o-kvalifikacii/README-2/massovyi-import)

## Сценарии

-  [Как подписать электронной подписью?](./scenarii/digital_signature/_index)

   -  [КриптоПРО](./scenarii/digital_signature/kriptopro)

   -  [КриптоАРМ](./scenarii/digital_signature/kriptoarm)

   -  [Сертификат ГУЦ](./scenarii/digital_signature/sertifikat-guc)

   -  [Как проверить корректность открепленной подписи](./scenarii/digital_signature/kak-proverit-korrektnost-otkreplennoi-podpisi)

-  [ViPNet: инструкция по подключению](./scenarii/vipnet-instrukciya-po-podklyucheniyu)

-  [Как войти с Яндекс ID](https://www.flow-crm.study/flowtsuhelpop/scenarii/kak-voiti-s-yandeks.klyuch)

-  [Как сделать рассылку?](./scenarii/kak-sdelat-rassylku)

---

-  [Личный кабинет гражданина](./scenarii/lichnyy-kabinet-grazhdanina)

-  [Общее](./scenarii/obshee/_index)

   -  [Роли в системе Flow](./scenarii/obshee/roli-v-sisteme-flow)

   -  [Синхронизация данных по программе/потоку из Odin во Flow](./scenarii/obshee/sinkhronizaciya-dannykh-po-programme-potoku-iz-odin-vo-flow)

   -  [Как списком посмотреть количество заявок на поток?](./scenarii/obshee/kak-spiskom-posmotret-kolichestvo-zayavok-na-potok)

   -  [Когда гражданин займёт квоту в договоре на организацию обучения?](./scenarii/obshee/kogda-grazhdanin-zaimyot-kvotu-v-dogovore-na-organizaciyu-obucheniya)

-  [Помощь](https://www.tgu-dpo.ru/form/)

-  [Инструкции Работа России](./scenarii/instrukcii-rabota-rossii)