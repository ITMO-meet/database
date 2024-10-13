# Структура БД

## Пользователь

```json
{
  "_id": ObjectId,  // Автогенерируемый id внутри MongoDB
  "username" : String,
  "photos": {
    "logo": photoId,
    "carousel": [photoId, photoId]
  },
  "bio": String,
  "tags": {
    "tag": [tagId], # id тега
    "person_params": {
      "date_of_birth": ISODate,
      "gender": Enum,
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
  "is_special": Enum, // Добавленный нами\пользователем\теневой
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
