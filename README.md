# Database
# Структура БД


## Пользователь
```json
{
  "_id": ObjectId,  // Автогенерируемый id внутри MongoDB
  "username" : String,
  "photos": {
    "logo": photoId, // id фотографии
    "carousel": [photoId, photoId]
  },
  "bio": String,
  "tags": {
    "tag": [tagId], # id тега
    "person_params": {
      "date_of_birth": ISODate,
      "gender": Enum,  // Optional enum
      "weight": NumberInt,
      "height": NumberInt,
      "hair_color": String,
      "zodiac_sign": String 
    }
  }
}
```

## Тег
```json
{
  "_id": ObjectId,
  "tag_text": String,
  "is_special": Enum, // Добавленный нами\пользователем\теневой (например, для предпочитаемого пола)
  "description": String
}
```

## Match
```json
{
  "_id": ObjectId,
  "user1_id": NumberInt,
  "user2_id": NumberInt,
  "createdAt": ISODate,
  "isActive": Enum // Например, для ЧС
}
```

## Liked 
Связь 1-1. Вопрос в целесообразности.
```json
{
  "_id": ObjectId,
  "user_id": NumberInt,
  "liked_ids": NumberInt
}
```

## Результаты теста
```json
{
    "_id": ObjectId, // Результат тестирования пользователя
    "result": String // TODO: Понять, как хранить тесты и связь с RecSys

}
```


Вопросы

1. Почему против `_id = UserID`?
2. Может быть, теги разделить на 3 типа?
   - Теневые
   - Добавленные нами
   - Добавленные пользователями (будет ли такой функционал)
3. Для чатов отдельная бд?
