# xk6-smtp

[k6](https://github.com/grafana/k6) extension to k6 extension to use smtp protocol (sending emails). Implemented using the [xk6](https://github.com/grafana/xk6) system.

## Build

```shell
xk6 build --with github.com/gpiechnik2/xk6-smtp@latest
```

## Example
An example of using the extension below. The options defined in the "mailOptions" variable are optional.

```javascript
import smtp from 'k6/x/smtp';

export default function () {
    const mailOptions = {
        subject: "Test subject",
        message: "Test message",
        udw: ["udwRecipient@gmail.com"]
    }

    smtp.sendMail(
        "smtp.gmail.com", 
        "587", 
        "sender@gmail.com", 
        "senderPassword", 
        "recipient@gmail.com",
        mailOptions
    )
}
```
