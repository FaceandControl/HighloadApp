# HighloadApp

# 1) Діаграма Архітектури 
![Untitled Diagram drawio (1)](https://user-images.githubusercontent.com/116028370/231503712-104c4f98-ace7-4a70-8ef2-548975e8bdfa.png)

# 2) Опис Архітектури 
   Була обрана Безсерверна арітектура на платформі Micrososft Azure  для легкої маштабованості, простоти деплою проекту та лекгості додавання нової логіки (функцій,      трігерів, сервісів).Також дана платформа  включає в себе засоби для роботи з різноманітним функціоналом таким як: створення і моніторинг черг, підключення та менеджмент сховищ даних, змога підключити статистичний моніторинг (Логери, App Insights), взаємодія з кешованими даними(Redis Cash).
   
# 3)  Перелік та короткий опис функцій  

    a) Video Metadata Function - Функція що вератає повну інформацію про певне відео , шляхом витягування даних з сховища данихпо айді відео. Зберігає дані в кеші щоб        зменшити час повторного запиту для цього відео.
    
    b) User Profile Function  - Функція що обробляє круд операції над юзером. Запит на перегляд інформації про юзера витягує потрібні дані каналу зі сховища даних а          також зберігає їх в кеші. Запити на створення/редагування юзера відправляють пейлоад ріквесту до спецальної черги (Profile CUD Queue), де ці дані обробляє              спеціальний  трігер - Crud Profile Triger. Також завдяки цій функції з бази даних + кеш , можна витягнути перелік відео поточного каналу.
    
    c) Video Recommendations Function - Функція посилає ріквест до спеціальної моделі рекомендацій (Recommendation Ai Model), ця модель звертається до статистичних            даних ( кількість переглядів, кількість лайків, найпопулярніші відео та юзери), які зберігаються в Databricks (в свою чергу Databricks черпають дані з бази            даних), на виході модель формує список рекомендація і повертає функції. Рекомендації також кешуються.
    
    d) Video Statistics Function - Функція яка через ріквест до Databricks витягає статистині дані ( лайки, перегляди, дізлайки) до вказаного відео. Статистика                кешується.
    
    e) Video Search Function - Функція яка відправляє ріквест з переліком фільтрів до  Elasctic Search , який ,за домогою цих фільтрів та індексуванню по юзерам та            відео ,повертає список  відповідних до запиту відео 
    
    f) Video Upload Status Function
    
    g) Video Like Function - Функція що при натисканні на кавішу лайк редагує кількість лайків на відео. Після натискання на клавішу відправляється ріквест з даними до 
       Video CD Likes Queue, звідки CD Likes Trigger грабає дані і насонові них апдейтить сховище даних.
       
    h) Video Comment Function - Функція що допомагає провести круд операції над коментарями/сабкоментарями під відео, аналогічна обробка запиту як в  функції для              лайків.
  
    i) User Subscription Function  - Функція що допомагає підписатися на певний канал, аналогічна обробка запиту як в  функції для лайків.
    
    j) Video Playback Function
    
    K) Populate Video Recommendations Cache Function
    
    L) Populate Video Statistics Cache Function
    
    M) Index Videos/Users Function
    
    
# 4)  Перелік та короткий опис сервісів  

    a) Video Upload Service  - Функція що дозволє загрузити відео з повною його інформацією на канал , шляхом його кодування і збереження метаданих в 
       сховище даних/блоб 
    
    b) Video Encode Service  - Функція яка кодує відео і зберігає інформацію в блоб сторейдж.
    
    
# 5)  Перелік та короткий опис трігерів  

    a) CRUD Profile Trigger
    
    b) CRUD Subscripton Trigger
    
    c) CRUD Comments Trigger
    
    d) CRUD Likes Trigger
    
    
Детальний опис вище переліченого функціоналу детальніше буде описаний в презентації 


# 6) Структура Бази Даних 
![image](https://user-images.githubusercontent.com/116028370/231772653-588f6b23-0f1d-40cd-97fb-e81f7005cbf7.png)
 
