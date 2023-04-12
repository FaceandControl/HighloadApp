# HighloadApp

# 1) Діаграма Архітектури 
![Untitled Diagram drawio (1)](https://user-images.githubusercontent.com/116028370/231503712-104c4f98-ace7-4a70-8ef2-548975e8bdfa.png)

# 2) Опис Архітектури 
   Була обрана Безсерверна арітектура на платформі Micrososft Azure  для легкої маштабованості, простоти деплою проекту та лекгості додавання нової логіки (функцій,      трігерів, сервісів).Також дана платформа  включає в себе засоби для роботи з різноманітним функціоналом таким як: створення і моніторинг черг, підключення та менеджмент сховищ даних, змога підключити статистичний моніторинг (Логери, App Insights), взаємодія з кешованими даними(Redis Cash).
   
# 3)  Перелік та короткий опис функцій  
    a) Video Metadata Function
    b) User Profile Function
    c) Video Recommendations Function
    d) Video Statistics Function
    e) Video Search Function
    f) Video Upload Status Function
    g) Video Like Function
    h) Video Comment Function
    i) User Subscription Function
    j) Video Playback Function
    K) Populate Video Recommendations Cache Function
    L) Populate Video Statistics Cache Function
    M) Index Videos/Users Function
    
# 4)  Перелік та короткий опис сервісів  
    a) Video Upload Service
    b) Video Encode Service
    
# 5)  Перелік та короткий опис трігерів  
    a) CRUD Profile Trigger
    b) CRUD Subscripton Trigger
    c) CRUD Comments Trigger
    d) CRUD Likes Trigger
    
Детальний опис вище переліченого функціоналу детальніше буде описаний в презентації 
