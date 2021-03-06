# Button

To display a button on your page you use [`New-PodeWebButton`](../../../Functions/Elements/New-PodeWebButton); a button can either be dynamic and run custom logic via a `-ScriptBlock`, or it can redirect a user to a `-Url`.

## Dynamic

A dynamic button is one that takes a custom `-ScriptBlock`, and when clicked will invoke that logic. You can run whatever you like, including output actions for Pode.Web to action against.

When using a dynamic button you can also supply a `-DataValue`, which is a way of supplying a special value/identity when the button is clicked. If supplied, this value is available in your scriptblock via `$WebEvent.Data['Value']`.

For example, the below button, when clicked, will display a toast message on the page:

```powershell
New-PodeWebCard -Content @(
    New-PodeWebButton -Name 'Click Me' -DataValue 'Random' -ScriptBlock {
        Show-PodeWebToast -Message "This came from a button, with a data value of '$($WebEvent.Data['Value'])'!"
    }
)
```

Which looks like below:

![button_dynamic](../../../images/button_dynamic.png)

## URL

To have a button that simply redirects to another URL, all you have to do is supply `-Url`:

```powershell
New-PodeWebCard -Content @(
    New-PodeWebButton -Name 'Repository' -Icon Link -Url 'https://github.com/Badgerati/Pode.Web'
)
```
