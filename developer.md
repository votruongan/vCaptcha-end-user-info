# vCaptcha Usage Documentation

## 1. Load script to webpage

```html
<script src="https://aiclub.uit.edu.vn/vcaptcha/build/bundle.js" async defer></script>
```

## 2. Render vCaptcha element to webpage

### 2.1. Implicit way of rendering

By default, vCaptcha will render onto element with `id` of `"vcaptcha-body"`. So you can just put an empty div with that `id` in your webpage and vCaptcha should be rendered fine:

```html
<div id="vcaptcha-body"></div>
```

### 2.2. Explicit way of rendering

You can also explicictly tell vCaptcha to render element onto specific element by passing its `id` to `vCaptcha.render` like this:

```html
<script type="text/javascript">
  vCaptcha.render('vcaptcha-content')
</script>
```

**_Caveat: calling vCaptcha.render in async script may not work._**

## 3. Retrieve vCaptcha session id in server-side

Each time user interact with vCaptcha, there will be a `session_id` for that interaction.

**_There are 2 ways to get the session id from frontend side:_**

### **_3.1. Extract session id from cookie_**

Whenever user successfully answer the challenge, the `vcaptcha_session_id` will be automatically added to their `cookie` and send to your backend along with their request. Use this `vcaptcha_session_id` to send to vCaptcha backend to verify whether a user have answered correctly or not.

### **_3.2. Get sessionId from frontend-side_**

Get `session_id` of vCaptcha by refer to variable `vCaptcha.sessionId` in frontend-side.

You can now manually send this `session_id` to your server

## 4. Verify vCaptcha session id

Use the retrieved session id from above and send to following url:

`https://aiclub.uit.edu.vn/captcha/demo/validate_captcha`

Method: `POST`

Body:

```json
{
  "session_id": "USER'S RESPONSE SESSION ID",
  "secret": "YOUR SITE'S SECRET",
  "private_key": "",
  "hostname": "YOUR SITE'S HOSTNAME"
}
```
