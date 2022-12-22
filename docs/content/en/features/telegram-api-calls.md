---
title: 'Telegram API calls'
menuTitle: 'Telegram API calls'
description: ''
category: 'Features'
fullscreen: false
position: 37
---

## answerInlineQuery

send back the results for an inline query

```php
 Telegraph::answerInlineQuery($inlineQuery->id(), [
    InlineQueryResultPhoto::make($logo->id."-light", "https://logofinder.dev/$logo->id/light.jpg", "https://logofinder.dev/$logo->id/light/thumb.jpg")
        ->caption('Light Logo'),
    InlineQueryResultPhoto::make($logo->id."-dark", "https://logofinder.dev/$logo->id/dark.jpg", "https://logofinder.dev/$logo->id/dark/thumb.jpg")
        ->caption('Dark Logo'),
])->cache(seconds: 600)->send();
```

## botInfo

retrieves Bot data from Telegram APIs

```php
Telegraph::botInfo()->send();

/*
id: xxxxx
is_bot: true
first_name: telegraph-test
username: my_test_bot
can_join_groups: true
can_read_all_group_messages: false
supports_inline_queries: false
*/
```

## botInfo

retrieves the bot data from Telegram APIs

```php
Telegraph::bot($telegraphBot)->botInfo()->send();
```

## botUpdates

retrieves the bot updates from Telegram APIs

```php
Telegraph::bot($telegraphBot)->botUpdates()->send();
```

<alert type="alert">Manual updates polling is not available if a webhook is set up for the bot. Webhook should be remove first using its [unregisterWebhook](webhooks/deleting-webhooks) method</alert>

## chatAction

Tells the chat users that something is happening on the bot's side. The status is set for up to 5 seconds or when a new message is received from the bot.

<img src="screenshots/chat-action.png" />

```php
Telegraph::chatAction(ChatActions::TYPING)->send();
```

## deleteMessage

deletes a message

```php
Telegraph::deleteMessage($messageId)->send();
```

## forwardMessage

forwards a message from another chat

```php
Telegraph::forwardMessage($fromChat, $messageId)->send();
```

## pinMessage

pins a message

```php
Telegraph::pinMessage($messageId)->send();
```

## unpinMessage

unpins a message

```php
Telegraph::unpinMessage($messageId)->send();
```

## unpinAllMessages

unpin al messages

```php
Telegraph::unpinAllMessages()->send();
```

## deleteKeyboard

removes a message keyboard (see [keyboards](features/keyboards) for details)

```php
Telegraph::deleteKeyboard($messageId)->send();
```

## document

sends a document

```php
Telegraph::document($documentPath)->send();
```

## edit

edits a message

```php
Telegraph::edit($messageId)->markdown('new message')->send();
```

## editCaption

edits an attachment caption

```php
Telegraph::editCaption($messageId)->markdownV2('new caption')->send();
```

## editMedia

edits a media messages with a new media content

```php
Telegraph::editMedia($messageId)->photo($path)->send();
Telegraph::editMedia($messageId)->document($path)->send();
Telegraph::editMedia($messageId)->animation($path)->send();
```

## getWebhookDebugInfo

retrieves webhook debug data for the active bot

```php
$response = Telegraph::getWebhookDebugInfo()->send();
```

## location

sends a location attachment

```php
Telegraph::location(12.345, -54.321)->send();
```

## markdown

compose a new telegram message (parsed as markdown)

```php
Telegraph::markdown('*hello* world')->send();
```

## markdownV2

compose a new telegram message (parsed as markdownV2)

```php
Telegraph::markdownV2('*hello* world')->send();
```

## message

compose a new telegram message (will use the default parse mode set up in `config/telegraph.php`)

```php
Telegraph::message('hello')->send();
```

## html

compose a new telegram message (parsed as html)

```php
Telegraph::html('<b>hello</b> world')->send();
```

## photo

sends a photo

```php
Telegraph::photo($pathToPhotoFile)->send();
```

## registerBotCommands

register commands in Telegram Bot in order to display them to the user when the "/" key is pressed

```php
Telegraph::registerBotCommands([
    'command1' => 'command 1 description',
    'command2' => 'command 2 description'
])->send();
```

## registerWebhook

register a webhook for the active bot

```php
Telegraph::registerWebhook()->send();
```

## replaceKeyboard

replace a message keyboard (see [keyboards](features/keyboards) for details)

```php
Telegraph::replaceKeyboard(
    $messageId, 
    Keyboard::make()->buttons([
        Button::make('open')->url('https://test.dev')
    ])
)->send();
```

## replyWebhook

replies to a webhook callback

```php
Telegraph::replyWebhook($callbackQueryId, 'message received', $showAlert)->send();
```

## store

Downloads a media file and stores it in the given path

```php
/** @var DefStudio\Telegraph\DTO\Photo $photo */

Telegraph::store($photo, Storage::path('bot/images'), 'The Photo.jpg');
```

## unregisterBotCommands

resets Telegram Bot registered commands

```php
Telegraph::unregisterBotCommands()->send();
```

## unregisterWebhook

unregister a webhook for the active bot

```php
Telegraph::registerWebhook()->send();
```

## voice

sends a vocal message

```php
Telegraph::voice($pathToVoiceFile)->send();
```

## when

allows to execute a closure when the given condition is verified

```php
Telegraph::when(true, fn(Telegraph $telegraph) => $telegraph->message('conditional message')->send());
```

## setBaseUrl

allows to override Telegram API url on a per-message basis:

```php
Telegraph::setBaseUrl('https://my-secret-server.dev')->message('secret message')->send();
```

## setTitle

sets chat title

```php
Telegraph::setTitle("my chat")->send();
```

## setDescription

sets chat description

```php
Telegraph::setDescription("a test chat with my bot")->send();
```

## setChatPhoto

sets chat profile photo

## chatInfo

retrieves Chat data from Telegram APIs

```php
Telegraph::chatInfo()->send();

/*
id: xxxxx
type: group
title: my telegram group
...
*/
```
## chatMenuButton

retrieves a bot current menu button info

```php
Telegraph::chatMenuButton()->send();
```

### getFileInfo

Retrieve file info from ID

```php
Telegraph::getFileInfo($fileId)->send();
```

## chatMemberCount

retrieves Chat member count

```php
Telegraph::chatMemberCount()->send();
```

## chatMember

retrieves a Chat member

```php
Telegraph::chatMember($userId)->send();
```

## userProfilePhotos

retrieves the User's profile photos

```php
Telegraph::userProfilePhotos($userId)->send();
```

## generateChatPrimaryInviteLink

generates a new primary invite link for a chat. Any previously generated primary link is revoked. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#exportchatinvitelink)

```php
Telegraph::generateChatPrimaryInviteLink()->send();
```

## createChatInviteLink

creates an additional invite link for a chat. For more info about options, see telegram [bot documentation](https://core.telegram.org/bots/api#createchatinvitelink)

```php
Telegraph::createChatInviteLink()
    ->name('September promotional link')    //optional
    ->expire(today()->addMonth())           //optional
    ->memberLimit(42)                       //optional
    ->withJoinRequest()                     //optional
    ->send();
```

## editChatInviteLink

edits an existing invite link for a chat. For more info about options, see telegram [bot documentation](https://core.telegram.org/bots/api#editchatinvitelink)

```php
Telegraph::editChatInviteLink('http://t.me/123456')
    ->name('new name')               //optional
    ->expire(today()->addYear())     //optional
    ->memberLimit(12)                //optional
    ->withJoinRequest(false)         //optional
    ->send();
```

## revokeChatInviteLink

revokes an existing invite link for a chat. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#revokechatinvitelink)

```php
Telegraph::revokeChatInviteLink('http://t.me/123456')->send();
```

## setChatPermissions

set users permissions for a chat. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#setchatpermissions)

```php
Telegraph::setChatPermissions([
    ChatPermissions::CAN_INVITE_USERS,
    ChatPermissions::CAN_CHANGE_INFO,
    ChatPermissions::CAN_ADD_WEB_PAGE_PREVIEWS => true,
    ChatPermissions::CAN_SEND_MESSAGES => false,
])->send();
```

## banChatMember

ban a user in a group, a supergroup or a channel. In the case of supergroups and channels, the user will not be able to return to the chat on their own using invite links. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#banchatmember)

```php
Telegraph::banChatMember($userid)
    ->until(now()->addDay());      //optional, only for supergroups and channels
    ->andRevokeMessages()          //optional, always true for supergroups and channels
    ->send();
```

## unbanChatMember

unban a user in a group, a supergroup or a channel. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#unbanchatmember)

```php
Telegraph::unbanChatMember($userid)->send();
```

## restrictChatMember

restrict a user in a group, a supergroup or a channel from taking the give actions. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#restrictchatmember)

```php
Telegraph::restrictChatMember($userid, [
       DefStudio\Telegraph\Enums\ChatPermissions::CAN_PIN_MESSAGES => false,
       DefStudio\Telegraph\Enums\ChatPermissions::CAN_INVITE_USERS => true,
       DefStudio\Telegraph\Enums\ChatPermissions::CAN_SEND_MESSAGES,
    ])
    ->until(now()->addDay())        //optional
    ->send();
```

## promoteChatMember

promotes a user in a group, a supergroup or a channel to administrator status. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#promotechatmember)

```php
Telegraph::promoteChatMember($userid, [
   DefStudio\Telegraph\Enums\ChatAdminPermissions::CAN_PIN_MESSAGES => false,
   DefStudio\Telegraph\Enums\ChatAdminPermissions::CAN_INVITE_USERS => true,
   DefStudio\Telegraph\Enums\ChatAdminPermissions::CAN_CHANGE_INFO,
])
->send();
```

## demoteChatMember

demote a user in a group, a supergroup or a channel from administrator status.

```php
Telegraph::demoteChatMember($userid)->send();
```

## poll

creates a native poll. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#sendpoll)

```php
Telegraph::poll("What's your favourite programming language?")
    ->option('php')
    ->option('typescript')
    ->option('rust')
    ->allowMultipeAnswers()
    ->validUntil(now()->addMinutes(5))
    ->send();
```

## quiz

creates a quiz. For more info, see telegram [bot documentation](https://core.telegram.org/bots/api#sendpoll)

```php
Telegraph::quiz("What's your favourite programming language?")
    ->option('php', correct: true)
    ->option('typescript')
    ->option('rust')
    ->explanation('We all love php, right?')
    ->validUntil(now()->addMinutes(5))
    ->send();
```

## dump

print a `dump()` of the current api call status for testing purposes

```php
Telegraph::message('test')->dump();
```

## dd

print a `dd()` of the current api call status for testing purposes

```php
Telegraph::message('test')->dd();
```
