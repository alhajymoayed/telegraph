---
title: 'Attachments' 
menuTitle: 'Attachments' 
description: ''
category: 'Features' 
fullscreen: false 
position: 36
---

Telegraph supports different types of attachments both from local files, remote urls and existing files on Telegram servers (using their file_id)

## Attachment types

### Photos

Photos can be sent through Telegraph `->photo()` method:

```php
Telegraph::photo(Storage::path('photo.jpg'))->send();
Telegraph::photo('https://my-repository/photo.jpg')->send();
Telegraph::photo($telegramFileId)->send();
```

<alert type="alert">Sent Photos can be edited with the [editMedia](features/telegram-api-calls#editMedia) call</alert>


### Animations

Animations can be sent through Telegraph `->animation()` method:

```php
Telegraph::animation(Storage::path('gif.gif'))->send();
Telegraph::animation('https://my-repository/gif.gif')->send();
Telegraph::animation($telegramFileId)->send();
```

<alert type="alert">Sent Animations can be edited with the [editMedia](features/telegram-api-calls#editMedia) call</alert>


### Vocal Messages

Vocals can be sent through Telegraph `->voice()` method:

```php
Telegraph::voice(Storage::path('voice.ogg'))->send();
Telegraph::voice('https://my-repository/voice.ogg')->send();
Telegraph::voice($telegramFileId)->send();
```


### Documents

Documents can be sent through Telegraph `->document()` method:

```php
Telegraph::document(Storage::path('my_document.pdf'))->send();
Telegraph::document('https://my-repository/my_document.pdf')->send();
Telegraph::document($telegramFileId)->send();
```

<alert type="alert">Sent Documents can be edited with the [editMedia](features/telegram-api-calls#editMedia) call</alert>


### Location

A location attachment can be sent through Telegraph `->location()` method:

```php
Telegraph::location(12.345, -54.321)->send();
```

### Dice

An animated emoji attachment that will display a random value can be sent through Telegraph `->dice()` method:

```php
Telegraph::dice()->send();
```

Different items can be used as "dice"

```php
Telegraph::dice(\DefStudio\Telegraph\Enums\Emojis::SLOT_MACHINE)->send();
```

### Invoice

An Invoice attachment can be sent through Telegraph `->invoice()` method:

```php
Telegraph::invoice()->send();
```

## Options

When sending files, some options are available:

### Html caption

```php
Telegraph::document(Storage::path('my_document.pdf'))
    ->html('<b>read this</b>')
    ->send();
```

<alert type="alert">Sent attachment captions can be edited with the [editCaption](features/telegram-api-calls#editCaption) call</alert>


### Markdown caption

```php
Telegraph::document(Storage::path('my_document.pdf'))
    ->markdown('read *this*')
    ->send();
```

<alert type="alert">Sent attachment captions can be edited with the [editCaption](features/telegram-api-calls#editCaption) call</alert>


### MarkdownV2 caption

```php
Telegraph::document(Storage::path('my_document.pdf'))
    ->markdownV2('read *this*')
    ->send();
```

<alert type="alert">Sent attachment captions can be edited with the [editCaption](features/telegram-api-calls#editCaption) call</alert>


### Without notification

```php
Telegraph::document(Storage::path('my_document.pdf'))
    ->silent()
    ->send();
```

### Prevent sharing

```php
Telegraph::document(Storage::path('my_document.pdf'))
    ->protected()
    ->send();
```

### Reply to a message

```php
Telegraph::document(Storage::path('my_document.pdf'))
    ->reply($messageId)
    ->send();
```

### Attach a keyboard

```php
Telegraph::document(Storage::path('brochure.pdf'))
      ->keyboard(fn (Keyboard $keyboard) => $keyboard->button('visit')->url('https://defstudio.it'))
    ->send();
```

### Add a thumbnail

```php
Telegraph::document(Storage::path('brochure.pdf'))
    ->thumbnail(Storage::path('brochure_thumbnail.jpg'))
    ->send();
```
