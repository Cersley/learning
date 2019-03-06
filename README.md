# System

## Preview

Игра и форум имеют общие данные о юзерах и игроках
Аккаунт, созданный на форуме - это аккаунт в игре

<details>
  
  ![database uml picture](/out/view/view-1.png)
</details>

## Data
<details>

  ![database uml picture](/out/data/data-2.png)
</details>

# Procedures

## MESSENGER
### > crubs
<!-- <details>
<summary>

</summary>

```

```
</details> -->

<details>
<summary>
connect_to_channel()
</summary>

```
isNew? -> create_channel()
```
> Подключить юзера к выбранному каналу
</details>

<details>
<summary>
disconnect_from_channel()
</summary>

> Отключиться от канала/закрыть канал, не получать сообщения с него
</details>

<details>
<summary>
send_message()
</summary>

```
emit_message()
```
> Отправка сообщения в мессенджере(на форум)
</details>

<details>
<summary>
emit_message()
</summary>

> Расшарить всем сообщение на id юзера или в канал
</details>


### > subs

<details>
<summary>
on_new_massage()
</summary>

```
emit_message()
```
</details>

<details>
<summary>
on_forum_event()
</summary>

```

newSubjectID? -> create_channel()

choose_channel_for_send()

add_message_event()
```

> системные сообщения, которые оповещают выбранные каналы(клан), что пользователь получил ачивку и т.п.
</details>

## FORUM
### > crubs

<details>
<summary>
create_board()
</summary>

> Создание раздела на форуме
</details>

<details>
<summary>
create_subject()
</summary>

```
send_event_to_messenger(newSubjectID)
```
> Создание темы на форуме и привязка его к каналу
</details>

<details>
<summary>
create_post()
</summary>

```
withChannel? -> send_message()
```
</details>

<details>
<summary>
like_post()
</summary>

```

```
</details>

<details>
<summary>
reply_post()
</summary>

```
withChannel? -> send_message()
```
</details>

<details>
<summary>
send_event_to_messenger()
</summary>

> Отправить event в мессенджер
</details>

<details>
<summary>
notify_community()
</summary>

```
notify_friends()
notify_clan()
```

> Отправить нотификацию связанным юзерам и сообществам
</details>

### > subs

<details>
<summary>
on_message()
</summary>

```

```
</details>

<details>
<summary>
on_signal()
</summary>

```
parse_signal_data()

needToNotify? -> send_event_to_messenger()

isGeneralEvent? -> notify_community()

update_user()
```

> Из `signal_layer` получаем сигнал. Парсим и определяем что нужно делать. Если нужно, отправляем в messanger, если нужно, то оповещаем людей на форме(соклановцы, друзья)
</details>


## GAME
### > crubs
<details>
<summary>
send_signal()
</summary>

>Отправляется сигнал в `signal_layer`. сигналом может являться любое событие, которое происходит в игре, кроме сообщений
</details>
