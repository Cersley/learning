# процедуры

## MESSENGER_IN_GAME

connect_to_channel()

send_message(
  withSubject? -> create_post()
)

## FORUM

create_board()

create_subject(
  asChannel? -> create_channel()
)

create_post(
  withChannel? -> send_message()
)

like_post()
reply_post(
  withChannel? -> send_message()
)

### MESSENGER_SERVICE

on_new_massage(
  hasSubject? -> createPost()
  hasChannel? -> send_message()
)



## GAME

on_change_status(USER, STATUS) {
  / login, afk, logout /

}





