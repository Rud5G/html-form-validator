---
title: API form elements
type: project
layout: page
project: html-form-validator
version: v1
---

The form validator detects HTML5 form elements and adds default validators depending on the used attributes.
Standard validation rules are added for you so you don't need to repeat those over and over again. And then
there are the special attributes with trigger standard validation:
- [[max|API Attributes#max]]
- [[min|API Attributes#min]]
- [[step|API Attributes#step]]
- [[maxlength|API Attributes#maxlength]]
- [[minlength|API Attributes#minlength]]
- [[multiple|API Attributes#multiple]]
- [[pattern|API Attributes#pattern]]
- [[required|API Attributes#required]], [[aria-required|API Attributes#aria-required]]

And if you need more validation or specific filters there is a [[data-filters|API Attributes#data-filters]] and
[[data-validators|API Attributes#data-validators]] attribute.

A full blown text input might look like:

```html
<input type="text" id="username" name="username" required
       placeholder="Your username" class="form-control"
       pattern="[a-z]{2,}" minlength="2" maxlength="16"
       data-reuse-submitted-value="true"
       data-filters="striptags|stringtrim"
       data-validators="" />
```

## The input element

### Hidden state (type=hidden)

*Attributes:*
[[value|API Attributes#value]].

```html
<input type="hidden" name="name" value="" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#hidden-state-(type=hidden))

### Text state (type=text) and Search state (type=search)

The difference between the Text state and the Search state is primarily stylistic.

*Attributes:*
[[list|API Attributes#list]],
[[maxlength|API Attributes#maxlength]],
[[minlength|API Attributes#minlength]],
[[pattern|API Attributes#pattern]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

*Filters:* Strip line breaks from the value.

```html
<input type="text" name="name" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#text-(type=text)-state-and-search-state-(type=search))

### Telephone state (type=tel)

*Attributes:*
[[list|API Attributes#list]],
[[maxlength|API Attributes#maxlength]],
[[minlength|API Attributes#minlength]],
[[pattern|API Attributes#pattern]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

*Filters:* Strip line breaks from the value.

If the `data-validator-country` attribute is set the `PhoneNumberValidator` is used. If not, it falls back to a
very loose regex pattern if none is set: `^\+[0-9]{1,3}[0-9\s]{4,17}$`.

```html
<input type="tel" name="tel" data-validator-country="es" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#telephone-state-(type=tel))

### URL state (type=url)

*Attributes:*
[[list|API Attributes#list]],
[[maxlength|API Attributes#maxlength]],
[[minlength|API Attributes#minlength]],
[[pattern|API Attributes#pattern]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

*Filters:* Strip line breaks from the value.

```html
<input type="url" name="location" list="urls">
<datalist id="urls">
    <option label="MIME: Format of Internet Message Bodies" value="https://tools.ietf.org/html/rfc2045">
    <option label="HTML" value="https://html.spec.whatwg.org/">
    <option label="DOM" value="https://dom.spec.whatwg.org/">
    <option label="Fullscreen" value="https://fullscreen.spec.whatwg.org/">
    <option label="Media Session" value="https://mediasession.spec.whatwg.org/">
    <option label="The Single UNIX Specification, Version 3" value="http://www.unix.org/version3/">
</datalist>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#url-state-(type=url))

### E-mail state (type=email)

*Attributes:*
[[list|API Attributes#list]],
[[maxlength|API Attributes#maxlength]],
[[minlength|API Attributes#minlength]],
[[multiple|API Attributes#multiple]],
[[pattern|API Attributes#pattern]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

*Filters:* Strip line breaks from the value, then strip leading and trailing whitespace from the value.

```html
<input type="email" name="email" data-validator-use-mx-check="true" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#e-mail-state-(type=email))

### Password state (type=password)

*Attributes:*
[[maxlength|API Attributes#maxlength]],
[[minlength|API Attributes#minlength]],
[[pattern|API Attributes#pattern]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

*Filters:* Strip line breaks from the value.

```html
<input type="password" name="password" required />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#password-state-(type=password))

### Date state (type=date)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="date" name="date" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#date-state-(type=date))

### Month state (type=month)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="month" name="month" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#month-state-(type=month))

### Week state (type=week)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="week" name="week" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#week-state-(type=week))

### Time state (type=time)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="time" name="time" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#time-state-(type=time))

### Local Date and Time state (type=datetime-local)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<fieldset>
    <legend>Destination</legend>
    <p>
        <label>Airport:</label>
        <input type="text" name="to" list="airports">
    </p>
    <p>
        <label>Departure time:</label>
        <input type="datetime-local" name="totime" step="3600">
    </p>
</fieldset>
<datalist id="airports">
    <option value="ATL" label="Atlanta">
    <option value="MEM" label="Memphis">
    <option value="LHR" label="London Heathrow">
    <option value="LAX" label="Los Angeles">
    <option value="FRA" label="Frankfurt">
</datalist>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#local-date-and-time-state-(type=datetime-local))

### Number state (type=number)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

The default step is 1, allowing only integers to be selected by the user. Unless the step base has a non-integer
(float) value in which case floats are allowed.
The base value of step equals the min value if it exists, otherwise it is set to `0`.
To disable the step validation use `step="any"`.

```html
<label>How much do you want to charge? $</label>
<input type="number" min="0" step="0.01" name="price">
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#number-state)

### Range state (type=range)

*Attributes:*
[[list|API Attributes#list]],
[[max|API Attributes#max]],
[[min|API Attributes#min]],
[[step|API Attributes#step]],
[[multiple|API Attributes#multiple]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<form ...>
    <fieldset>
        <legend>Outbound flight time</legend>
        <select ...>
            <option>Departure
            <option>Arrival
        </select>
        <p>
            <output name=o1>00:00</output> – <output name=o2>24:00</output>
        </p>
        <input type=range multiple min=0 max=24 value=0,24 step=1.0 ...
               oninput="o1.value = valueLow + ':00'; o2.value = valueHigh + ':00'">
    </fieldset>
    ...
</form>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#range-state-(type=range))

### Colour state (type=color)

*Attributes:*
[[list|API Attributes#list]],
[[disabled|API Attributes#disabled]],
[[value|API Attributes#value]].

*Filters:* Convert the value to lowercase.

```html
<input type="color" name="color" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#color-state-(type=color))

### Checkbox state (type=checkbox)

*Attributes:*
[[checked|API Attributes#checked]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="checkbox" name="checkbox" value="value" />
```

Input arrays are supported. The following will return an array `['cars'=>['audi', 'bmw']]`.

```html
<form action="/" method="post">
    <input type="checkbox" name="cars[]" value="audi" checked />
    <input type="checkbox" name="cars[]" value="bmw" checked />
    <input type="checkbox" name="cars[]" value="volkswagen" />
</form>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#checkbox-state-(type=checkbox))

### Radio Button state (type=radio)

*Attributes:*
[[checked|API Attributes#checked]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="radio" name="gender" value="male" /> Male<br />
<input type="radio" name="gender" value="female" /> Female<br />
<input type="radio" name="gender" value="other" /> Other
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#radio-button-state-(type=radio))

### File Upload state (type=file)

*Attributes:*
[[accept|API Attributes#accept]],
[[multiple|API Attributes#multiple]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<input type="file" accept=".doc,.docx,.xml,application/msword" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#file-upload-state-(type=file))

### Submit Button state (type=submit)

*Attributes:*
[[value|API Attributes#value]].

```html
<input type="submit" name="name" value="" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#submit-button-state-(type=submit))

### Image Button state (type=image)

*Attributes:*
[[value|API Attributes#value]].

```html
<form action="process.cgi">
    <input type="image" src="map.png" name="where" alt="Show location list">
</form>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#image-button-state-(type=image))

### Button state (type=button)

*Attributes:*
[[value|API Attributes#value]].

```html
<input type="button" name="name" value="" />
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#button-state-(type=button))

## The button element

*Attributes:*
[[value|API Attributes#value]].

```html
<button type="submit" name="name">Value</button>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#the-button-element)

## The select element

*Attributes:*
[[multiple|API Attributes#multiple]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]],
[[value|API Attributes#value]].

```html
<select name="car">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
    <option value="mercedes">Mercedes</option>
    <option value="audi">Audi</option>
</select>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#the-select-element)

## The textarea element

*Attributes:*
[[maxlength|API Attributes#maxlength]],
[[minlength|API Attributes#minlength]],
[[disabled|API Attributes#disabled]],
[[readonly|API Attributes#readonly]],
[[required|API Attributes#required]].

```html
<textarea name="textarea"></textarea>
```

Resources:
[whatwg](https://html.spec.whatwg.org/multipage/forms.html#the-textarea-element)
