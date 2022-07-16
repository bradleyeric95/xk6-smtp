# xk6-smtp
[k6](https://github.com/grafana/k6) extension to k6 extension to use smtp protocol (sending emails). Implemented using the [xk6](https://github.com/grafana/xk6) system.

## Build
```shell
xk6 build v0.38.3 --with github.com/gpiechnik2/xk6-smtp@latest
```

## function structure
```javascript
sendMail(
    host,
    port,
    senderMail,
    passwordOrToken,
    [UDW, UDW2 ...],
    emailData
)
```

## Example

```javascript
import smtp from 'k6/x/smtp';


export default function () {

    // simple mail
    smtp.sendMail(
        "smtp.gmail.com", 
        "587", 
        "sender@example.com", 
        "passwordOrToken", 
        ["udwUser@example.pl"], 
        "Simple message"
    )

    // send an email with a defined subject, recipient and message
    smtp.sendMail(
        "smtp.gmail.com", 
        "587", 
        "sender@example.com", 
        "passwordOrToken", 
        ["udwUser@example.pl"], 
        "To: mainRecipient@example.com\r\n" + "Subject: Test mail\r\n\r\n" + "Email body\r\n"
    )

    // send message with html message
    const mime = "MIME-version: 1.0;\nContent-Type: text/html; charset=\"UTF-8\";\n\n"
    const body = "<html><body><h1>Hello World!</h1></body></html>"

    smtp.sendMail(
        "smtp.gmail.com", 
        "587", 
        "sender@example.com", 
        "passwordOrToken", 
        ["udwUser@example.pl"], 
        mime + body
    )
}
```


