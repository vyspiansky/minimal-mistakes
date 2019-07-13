---
title: At least one checkbox must be selected (checked)
categories: [JavaScript]
tags: [checkbox, setCustomValidity]
---

There is a form with multiple checkboxes and we're going to make sure that at least one is checked using pure JavaScript. To set a custom validation error message, we will use `setCustomValidity()` method.

Here's how the error message will look in the Google Chrome browser when trying to send a form without selecting a checkbox:

![Select at least one item form](/assets/images/js-select-at-least-one-item.png)

HTML code:

```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>At least one checkbox must be selected</title>
    <meta charset="utf-8">
  </head>
  <body>
    <form id="sectionForm" method="post">
        <h3>Please select at least one item</h3>

        <p><input type="checkbox" name="section" value="sports">Sports</p>
        <p><input type="checkbox" name="section" value="business">Business</p>
        <p><input type="checkbox" name="section" value="health">Health</p>
        <p><input type="checkbox" name="section" value="society">Society</p>
        
        <p><input type="submit" value="Submit"></p>
    </form>

    <script src="script.js"></script>
  </body>
</html>
```

A content of the `script.js` file:

```javascript
(function() {
    const form = document.querySelector('#sectionForm');
    const checkboxes = form.querySelectorAll('input[type=checkbox]');
    const checkboxLength = checkboxes.length;
    const firstCheckbox = checkboxLength > 0 ? checkboxes[0] : null;

    function init() {
        if (firstCheckbox) {
            for (let i = 0; i < checkboxLength; i++) {
                checkboxes[i].addEventListener('change', checkValidity);
            }

            checkValidity();
        }
    }

    function isChecked() {
        for (let i = 0; i < checkboxLength; i++) {
            if (checkboxes[i].checked) return true;
        }

        return false;
    }

    function checkValidity() {
        const errorMessage = !isChecked() ? 'At least one checkbox must be selected.' : '';
        firstCheckbox.setCustomValidity(errorMessage);
    }

    init();
})();
```