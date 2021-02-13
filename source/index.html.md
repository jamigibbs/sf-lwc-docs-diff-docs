---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://github.com/jamigibbs/sf-lwc-docs-diff-docs'>Docs Github repo</a>
  - <a href='https://github.com/jamigibbs/sf-lwc-docs-diff'>Diff script Github repo</a>

# includes:
#   - errors

search: true

code_clipboard: true
---

# LWC Docs Diff

These docs highlights changes or updates made in the [Salesforce Component Reference](https://developer.salesforce.com/docs/component-library/overview/components) documentation and specifications for **Lightning Web Components**.

When a new diff is found, a new section will be created with each component that has had content added, removed, or updated. It's possible that this isn't an exhuastive list so make sure to check the official docs before relying on it. 

# Updates: Feb 5, 2021

## lightning-button

### Documentation

Link to [lightning-button documention](https://developer.salesforce.com/docs/component-library/bundle/lightning-button/documentation)

Accessibility addition:

ATTRIBUTE | TYPE | DESCRIPTION
-------------- | -------------- | --------------
aria-haspopup | string | Indicates the type of popup element, such as menu or dialog, that can be triggered by the button. See [aria-haspopup](https://www.w3.org/TR/wai-aria/#aria-haspopup) for supported values.


## lightning-combobox

### Documentation

Link to [lightning-combobox documention](https://developer.salesforce.com/docs/component-library/bundle/lightning-combobox/documentation)

**Usage Considerations**

`lightning-combobox` doesn't currently support autocomplete or typeahead. The autocomplete attribute is reserved for internal use.

On mobile devices, `lightning-combobox` has the following limitations.

- The dropdown menu doesn't scroll correctly when there isn't enough room to display the complete list of options.
- The mobile viewport doesn't display the dropdown menu correctly especially if the component is placed near the bottom of the page.
We recommend using the HTML `<select>` element on mobile instead.

### Specification

Link to [lightning-combobox specifications](https://developer.salesforce.com/docs/component-library/bundle/lightning-combobox/specification)


NAME  | ACCESS | DESCRIPTION
-------------- | -------------- | --------------
autocomplete | global | Reserved for internal use. Controls auto-filling of the field. Set the attribute to pass through autocomplete values to be interpreted by the browser.
dropdown-alignment | global | Specifies where the drop-down list is aligned with or anchored to the selection field. By default the list is aligned with the selection field at the top left so the list opens down. Use bottom-left to make the selection field display at the bottom so the list opens above it. Use auto to let the component determine where to open the list based on space available.


## lightning-datatable

```javascript
const columns = [
     {label: 'Opportunity name', fieldName: 'opportunityName', type: 'text'},
     {label: 'Confidence', fieldName: 'confidence', type: 'percent', cellAttributes:
     { iconName: { fieldName: 'trendIcon' }, iconPosition: 'right' }},
     {label: 'Amount', fieldName: 'amount', type: 'currency', typeAttributes: { currencyCode: 'EUR', step: '0.001'}},
     {label: 'Contact Email', fieldName: 'contact', type: 'email'},
     {label: 'Contact Phone', fieldName: 'phone', type: 'phone'},
];
```

### Documentation

Link to [lightning-datatable documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-datatable/documentation)

ATTRIBUTE | TYPE | DESCRIPTION
-------------- | -------------- | --------------
currency | Displays a currency using [lightning-formatted-number](https://developer.salesforce.com/docs/component-library/bundle/lightning-datatable/bundle/lightning-formatted-number/). See Displaying Currency and Percentages. | currencyCode, currencyDisplayAs, minimumIntegerDigits, minimumFractionDigits, maximumFractionDigits, minimumSignificantDigits, maximumSignificantDigits, **step**
percent | Displays a percentage using [lightning-formatted-number](https://developer.salesforce.com/docs/component-library/bundle/lightning-datatable/bundle/lightning-formatted-number/). See Displaying Currency and Percentages. | minimumIntegerDigits, minimumFractionDigits, maximumFractionDigits, minimumSignificantDigits, maximumSignificantDigits, **step**

**Displaying Currency and Percentages**

Currency type displays a value based on the org currency and your Salesforce locale by default.

To override the default currency code, pass in a custom currencyCode value.

```javascript
const columns = [
    { label: 'Amount', fieldName: 'amount', type: 'currency', typeAttributes: { currencyCode: 'EUR' }},
    // other column data
]
```

To specify the granularity on a currency or percentage for inline editing, pass in the step attribute. For example, specify step: `0.01` to allow numbers with two decimal places, or step: `0.001` permits three decimal places. Specify step: `1` to require whole numbers. The default is `0.01`. You can preserve the number of fraction digits for display using `minimumFractionDigits` and `maximumFractionDigits`.

```javascript
const columns = [
    { 
        label: 'Confidence', fieldName: 'confidence', type: 'percent',
        typeAttributes: { 
            step: '0.00001', minimumFractionDigits: '2', maximumFractionDigits: '3'
        },
        editable: true
    },
    //other column data
]
```

For example, if you pass in confidence: `0.21234` in your column data, the display value is `21.234%`. When you inline edit, the step value is used to determine if your input is valid. If you pass in confidence: `0.78`, the display value is `78.00%` because minimumFractionDigits is set to `2`.


**Displaying Date and Time Using Type Attributes**

The locale set in the Salesforce user preferences determines the default formatting for date and time types.

**Creating Header Actions**

If `hideDefaultActions` is set to true on a column that has custom header actions, the "Clip text" and "Wrap text" actions are removed from the actions dropdown menu, and the content is clipped by default. To wrap text when the default actions are hidden, set `wrapText: true` in the column definition.

### Specification

Link to [lightning-datatable specifications](https://developer.salesforce.com/docs/component-library/bundle/lightning-datatable/specification)

NAME | TYPE | DESCRIPTION
-------------- | -------------- | --------------
render-config | global | Reserved for internal use. Enables and configures advanced rendering modes.
resize-column-disabled | global | If present, column resizing is disabled.
resize-step | global | The width to resize the column when a user presses left or right arrow. The default is 10px.

## lightning-formatted-date-time

### Documentation

Link to [lightning-formatted-date-time](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-date-time/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-formatted-date-time`, see the `c-clock` component.


## lightning-formatted-email

### Documentation

Link to [lightning-formatted-email documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-email/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-formatted-email`, see the following components in the LWC Recipes repo.

- `c-nav-to-record`
- `c-wire-get-record-user`

## lightning-formatted-number

### Documentation

Link to [lightning-formatted-email documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-number/documentation)

The locale set in your Salesforce user settings determines where to display spaces, commas, and periods in numbers, and the currency used by default. See the **Usage Considerations** section for limitations in some locales.

**Usage Considerations**

The locale set in your Salesforce user preferences determines how numbers are formatted. Some locales such as the Arabic (Lebanon) and Bangla (Bangladesh) locales also specify a numeral system other than the Hindu-Arabic numerals 0-9. The org permission “Show Hindu-Arabic Numbers” is intended to override a locale's default numerals. However, `lightning-formatted-number` displays the locale's default numerals even when this permission is enabled in your org. See [Supported Number, Name, and Address Formats (ICU)](https://help.salesforce.com/articleView?id=admin_supported_locales.htm%22).

The `format-style` attribute is called the style attribute in the Aura version of this component. See [Base Components: Aura Vs Lightning Web Components](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-number/docs/component-library/documentation/lwc/lwc.migrate_map_aura_lwc_components).

**LWC Recipes**

The LWC Recipes GitHub repository contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-formatted-date-time`, see the `c-misc-shared-javascript` component.

## lightning-formatted-phone

### Documentation

Link to [lightning-formatted-phone documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-phone/documentation)

To display the phone number in plain text without a hyperlink, include the disabled attribute. Disabling the phone number also prevents setting focus on the phone number using the Tab key.

```javascript
<template>
    <lightning-formatted-phone value="18005551212" disabled></lightning-formatted-phone>
</template>
```

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses lightning-formatted-phone, see the following components in the LWC Recipes repo.

- c-contact-tile
- c-event-bubbling

### Specification

Link to [lightning-formatted-phone specification](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-phone/specification)

NAME | DEFAULT | DESCRIPTION
-------------- | -------------- | --------------
disabled | false | If present, the phone number displays as plain text instead of a link. The number cannot be clicked or receive focus.

## lightning-formatted-url

### Documentation

Link to [lightning-formatted-url documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-formatted-url/documentation)

**Specifying a Target**

- `_blank`: Opens the link in a new window or tab. In a mobile hybrid app like the Salesforce mobile app, the link is handled similar to `_self` and opens inside the app if possible.
- `_self`: Opens the link in the same frame as it was clicked. This is the default behavior. In Lightning Experience and Experience Builder sites, the link is opened in a new tab if it cannot be opened inside the app. We recommend that you use `lightning-navigation` to create links within Lightning Experience and Experience Builder sites.

**Usage Considerations**

We recommend using absolute URLs where possible as they can prevent duplicate content to improve search engine optimization. Having your internal links as relative URLs can also expose the structure of your website.

## lightning-input-address

### Documentation

Link to [lightning-input-address documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-input-address/documentation)

**Using Lookup to Find and Autofill an Address** (header title was updated to this from "Using Autocomplete to Autofill an Address" [git link](https://github.com/jamigibbs/sf-lwc-docs-diff/commit/65676d94c5c20b73c14677a15b7a079f758e08ff#diff-72f25198df988156527f0eecbb924f2970a60104bf29b2edaa75de2053d5ae40L84)):


## lightning-input-rich-text

### Documentation

Link to [lightning-input-rich-text documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-input-right-text/documentation)

When you use `lightning-input-rich-text` in Salesforce, pasting an image from an HTTP source results in the display of a broken image icon. Mixed content is blocked in Salesforce to improve security. We recommend uploading the image as a static resource first before using it in the component. Alternatively, enable the image toolbar button so your users can upload the image to the org.

### Specification

Link to [lightning-input-rich-text specification](https://developer.salesforce.com/docs/component-library/bundle/lightning-input-right-text/specification)


NAME | DEFAULT | DESCRIPTION
-------------- | -------------- | --------------
required | false | 	If present, an asterisk is displayed before the label when labelVisible is set to true.


## lightning-input

### Documentation

Link to [lightning-input documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-input/documentation)


The `label` attribute is required. If you don't want to display a label, specify the `variant="label-hidden"` attribute. See **Accessibility** for more information.

**Using Autocomplete in Input Fields**

The values on and off are supported, but the behavior depends on the browser. Some browsers might ignore the passed value. See [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete) for more information.

**Set and Read Selection Indexes**

```javascript
<template>
    <lightning-input type="text" label="Enter some text" 
                     value={textvalue} onchange={handleChange}></lightning-input>
    <lightning-button label="Focus selection" onclick={handleClick}></lightning-button>
</template>
```

```javascript
import { LightningElement } from 'lwc';

export default class DemoInputSelection extends LightningElement {
    textvalue = 'initial value';
    handleChange(event) {
        this.textvalue = event.detail.value;
    }
    handleClick(event) {
        let input = this.template.querySelector('lightning-input');
        let end = input.value.length;
        input.selectionStart = 0;
        input.selectionEnd = end;
        // Optionally, focus to highlight the selected characters
        // input.focus();
    }
}
````

The `selection-start` and `selection-end` attribute values are passed through to the `<input>` element. Only the input type `text` is currently supported. The `selection-start` value specifies the index of the first character selected in the input element, while the `selection-end` value specifies the index of the last character selected. Index values start at 0.

This example selects the characters from index 0 to the end when you click the button.

In JavaScript, the `selectionEnd` property is set to the length of the current input value.

**Accessibility**

Specify the `aria-labelledby` attribute and `variant="label-hidden"` to provide a custom label for assistive devices. Although the `label` attribute is still required, the `<label>` element is not rendered in this case.

```html
<template>
    <p id="otherlabel">Your Event Name
    <lightning-input label="Event" 
                     variant="label-hidden" 
                     aria-labelledby="otherlabel"
    </lightning-input>
    </p>
</template>
```

**LWC Recipes**

The [LWC Recipes GitHub](https://github.com/trailheadapps/lwc-recipes) repository contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-input`, see the following components in the LWC Recipes repo.

- c-lds-create-record
- c-misc-modal
- c-wire-get-picklist-values

### Specification

Link to [lightning-input specification](https://developer.salesforce.com/docs/component-library/bundle/lightning-input/specification)

NAME | DESCRIPTION
-------------- | --------------
selection-end | Specifies the index of the last character to select in the input element. This attribute is supported only for text type. Use with selection-start to programmatically set or read the position of selected text.
selection-start | Specifies the index of the first character to select in the input element. This attribute is supported only for text type. Use with selection-end to programmatically set or read the position of selected text.

## lightning-map

### Documentation

Link to [lightning-map documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-map/documentation)

**Marker Properties**

Use the following marker properties to customize the map display.

PROPERTY | TYPE | DESCRIPTION
-------------- | -------------- | --------------
type | string | A type of shape to use instead of the default map marker. Accepted values are `Circle`, `Rectangle`, and `Polygon`. See Marking Locations with Shapes.
mapIcon | objecyt | A custom SVG icon to use instead of the default map marker. See Marking Locations with Custom Icons.

**Displaying or Hiding the List of Locations**

Note that if you specify a type to display a shape at a location, the list view doesn't show an entry for the location. See Marking Locations with Shapes.

**Setting Map Controls**

`lightning-map` enables you to specify which map controls to allow. Set the options attribute to enable or disable map controls using the following boolean properties.

PROPERTY | DEFAULT VALUE | DESCRIPTION
-------------- | -------------- | --------------
draggable | true | Enables dragging to pan the map with the mouse. Set to false to prevent dragging. This property affects the map only. Markers aren't draggable.
zoomControl | true | Shows the +/- zoom controls on the bottom of the map. Set to false to remove the controls and prevent zooming.
scrollwheel | true | Permits zooming with the mouse wheel. Set to false to disable zooming with the mouse wheel when zooming is enabled. If zoomControl is false or disableDefaultUI is true, the scrollwheel setting has no effect because these settings disable zooming.
disableDefaultUI | false | Set to true to remove Map/Satellite and +/- zoom buttons. The satellite view and zooming are disabled. Mouse scrolling and dragging is not affected by disableDefaultUI.
disableDoubleClickZoom | false | Set to true to disable zooming with a mouse double-click when zooming is enabled.

Zooming behavior is influenced by all the properties except draggable.

- To prevent all zooming, set zoomControl: false
- To prevent all zooming and also remove the Map/Satellite buttons, set disableDefaultUI: true
- To allow zooming, but prevent the scroll wheel from activating zoom, set scrollwheel: false
- To allow zooming, but prevent a double-click from activating zoom, set disableDoubleClickZoom: true
- This example disables dragging and also disables the default UI, which removes the zoom capability and - Map/Satellite button. The result is a static map.

```javascript
<template>
    <lightning-map
        map-markers={mapMarkers}
        options={mapOptions}
        zoom-level="14"
    ></lightning-map>
</template>
```
The values of the options attribute are set in an object of boolean values in JavaScript.

```javascript
import { LightningElement } from 'lwc';

export default class LightningExampleMapControls extends LightningElement {
    mapMarkers = [
        {
            location: {
                Street: '1000 5th Ave',
                City: 'New York',
                State: 'NY',
            },

            title: 'Metropolitan Museum of Art',
            description:
                'A grand setting for one of the greatest collections of art, from ancient to contemporary.',
        },
    ];
    mapOptions = {
           draggable: false, 
           disableDefaultUI: true 
        };
}
```

**Marking Locations with Shapes**

lightning-map enables you to customize your maps to use different indicators for locations instead of the default Google Maps markers.

The map-markers attribute supports the type property to define colored shapes to mark a location. Available type values are Circle, Rectangle, and Polygon. The values are case-sensitive.

The type property works with the following properties to define a shape's appearance.


TYPE VALUE | PROPERTY | PROPERTY TYPE | DESCRIPTION
-------------- | -------------- | -------------- | --------------
Circle | radius | number | The number in meters for the radius of the circle. This value represents the Earth's surface included in the circle around the location.
Rectangle | bounds | object | Uses north and south latitude values and east and west longitude values to specify the corners of the rectangle.
Polygon | paths | object | Defines a set of lat and lng properties for the latitude and longitude coordinates of the polygon's shape.
All | strokeColor | string | Hexadecimal color code or CSS3 color name for the stroke, which creates the edge of the shape.
  | strokeOpacity | number | The degree of transparency of the stroke. The value is between 0.0 and 1.0, where 0.0 is transparent and 1.0 is opaque.
  | strokeWeight | number | The stroke width in pixels.
  | fillColor | string | Hexadecimal color code or CSS3 color name to fill the shape.
  | fillOpacity | number | The degree of transparency of the fill for the shape. The value is between 0.0 and 1.0, where 0.0 is transparent and 1.0 is opaque.

**Mark a Location with a Circle**

This example creates a yellow circle to mark the location.

```javascript
<template>
    <lightning-map
        map-markers={mapMarkers}
        zoom-level="15"
    ></lightning-map>
</template>
```

The mapMarkers object defines the location and the type. The properties specified after type define the circle as having a 200 meter radius, and a yellow color #FFF000 for both the stroke edge and fill, with the edge more opaque than the fill.

```javascript
import { LightningElement } from 'lwc';

export default class MapCircleShape extends LightningElement {
    mapMarkers = [
        {   
            location: {
                City: 'San Francisco',
                Country: 'USA',
                PostalCode: '94105',
                State: 'CA',
                Street: '50 Fremont St',
            },
            type: 'Circle',
            radius: 200, 
            strokeColor: '#FFF000', 
            strokeOpacity: 0.8,
            strokeWeight: 2,
            fillColor: '#FFF000', 
            fillOpacity: 0.35,
        },
    ];
}
```

**Mark a Location with a Rectangle**

This example shows the JavaScript for defining a rectangle shape for a location.

The mapMarkers object sets the type to Rectangle. The bounds property defines the coordinates of the rectangle for the location. Other properties define the characteristics of the stroke and fill.

```javascript
import { LightningElement } from 'lwc';

export default class MapRectangleShapeExample extends LightningElement {
    mapMarkers = [
        {   
            location: {
                City: 'San Francisco',
                Country: 'USA',
                PostalCode: '94105',
                State: 'CA',
                Street: '500 Howard St',
            },
            type: 'Rectangle',
            bounds: {
                north: 37.788,
                south: 37.774,
                east: -122.395,
                west: -122.412,
                }, 
            strokeColor: '#0b5411', 
            strokeOpacity: 0.8,
            strokeWeight: 2,
            fillColor: '#0b5411', 
            fillOpacity: 0.35,
        },
    ];
}
```

**Mark a Location with a Polygon**

This example sets the type to Polygon and draws a pink polygon with a black outline. The polygon's segments are defined in the paths property using coordinates specified by the lat and lng properties.

```
import { LightningElement } from 'lwc';

export default class MapPolygonShape extends LightningElement {
    mapMarkers = [
        {   
            location: {
                City: 'San Francisco',
                Country: 'USA',
                PostalCode: '94105',
                State: 'CA',
                Street: '425 Mission St', 
            },
            type: 'Polygon',
            paths: [
            { lat: 37.78806990305951, lng: -122.39873856028704 }, 
            { lat: 37.790689809711886, lng: -122.39540189227252 }, 
            { lat: 37.79036762555352, lng: -122.39495128115801 }, 
            { lat: 37.787569651422224, lng: -122.39842742404132 }, 
            { lat: 37.7879172842749, lng: -122.39886730631976 },
            { lat: 37.7880699030595, lng: -122.39873856028704 },
            ], 
            strokeColor: 'black',
            strokeOpacity: 0.35,
            strokeWeight: 2,
            fillColor: 'pink',
            fillOpacity: 0.35,
        },
    ];
}
```

**Marking Locations with Custom Icons**

Pass the mapIcon property to the map-markers attribute to specify an SVG icon image in place of the Google Maps marker.

Use either type or mapIcon to customize a given location. You can't use both for one location.

The mapIcon property works with the following properties to define the icon's appearance.

PROPERTY | TYPE | DESCRIPTION
-------------- | -------------- | --------------
path | string | SVG path notation to add a vector-based symbol as the icon for a marker.
scale | number | The amount by which the marker icon is scaled in size. The default value is 1. The marker icon size is multiplied by the scale value to produce the actual output size of the marker in pixels.
strokeColor | string | Hexadecimal color code or CSS3 color name for the stroke, which creates the edge of the custom icon.
strokeOpacity | string | The degree of transparency of the stroke. The value is between 0.0 and 1.0, where 0.0 is transparent and 1.0 is opaque.
strokeWeight | string | The stroke width in pixels. The default is 1.
fillColor | string | Hexadecimal color code or CSS3 color name to fill the icon.
fillOpacity | string | The degree of transparency of the fill for the icon. The value is between 0.0 and 1.0, where 0.0 is transparent and 1.0 is opaque.

This example creates a gold star without an outline as the marker. The list-view is made visible to show that a location with a custom marker is displayed in the list of markers.

```javascript
<template>
    <lightning-map
        map-markers={mapMarkers}
        zoom-level="15"
        list-view="visible"
    ></lightning-map>
</template>
```

The scale property sets the star to display at a comfortable size for the map viewed on a desktop.

```javascript
import { LightningElement } from 'lwc';

export default class MapCustomIconExample extends LightningElement {
    mapMarkers = [
        {   
            location: {
                City: 'San Francisco',
                Country: 'USA',
                PostalCode: '94105',
                State: 'CA',
                Street: '415 Mission St', 
            },
            mapIcon: {
            path: 'M 125,5 155,90 245,90 175,145 200,230 125,180 50,230 75,145 5,90 95,90 z',            
            fillColor: 'gold',
            fillOpacity: .8,
            strokeWeight: 0,
            scale: .10
            },
        ];
    }
}   
```

## lightning-message-service

### Documentation

Link to [lightning-message-service documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-message-service/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning/messageService`, see the following components in the LWC Recipes repo.

- `c-lms-publisher-web-component`
- `c-lsm-suscriber-web-component`

## lightning-navigation

### Documentation

Link to [lightning-navigation documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-navigation/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning/navigation`, see the `c-nav-to-*` components in the LWC Recipes repo.

## lightning-output-field

### Specification

Link to [lightning-output-field specifications](https://developer.salesforce.com/docs/component-library/bundle/lightning-output-field/specification)

NAME | ARGUMENTS | DESCRIPTION
-------------- | -------------- | --------------
wirePicklistValues | picklistValues | Reserved for internal use.
wireRecordUi | data | Reserved for internal use. The record and objectInfo data

## lightning-page-reference-utils

### Documentation

**LWC Recipes**

Link to [lightning-page-reference-utils documenation](https://developer.salesforce.com/docs/component-library/bundle/lightning-page-reference-utils/documentation)


The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning/pageReferenceUtils`, see the `c-nav-to-new-record-with-defaults` component.

## lightning-platform-resource-loader

### Documentation

Link to [lightning-platform-resource-loader documenation](https://developer.salesforce.com/docs/component-library/bundle/lightning-platform-resource-loader/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning/platformResourceLoader`, see the following components in the LWC Recipes repo.

- `c-libs-chartjs`
- `c-libs-d3`

## lightning-platform-show-toast-event

### Documentation

Link to [lightning-platform-show-toast-event documenation](https://developer.salesforce.com/docs/component-library/bundle/lightning-platform-show-toast-event/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning/platformShowToastEvent`, see the following components in the LWC Recipes repo.

- c-lds-create-record
- c-misc-notification

## lightning-record-edit-form

### Documentation

Link to [lightning-record-edit-formt documenation](https://developer.salesforce.com/docs/component-library/bundle/lightning-record-edit-form/documentation)

**Submitting Form Values with a Button**

`lightning-record-edit-form` renders the fields within the HTML form element and uses a button for form submission. Customizing the form element for form submission is not supported. We recommend that you use `lightning-button` with `type="submit"` as shown in the previous sections. The default type on `lightning-button` is button, which does nothing unless you include an `onclick` handler. If you use an HTML button element within `lightning-record-edit-form`, the default is `t`ype="submit"`.

When you submit the form, the component fires the custom events in this order.

- `click` if you use the onclick event handler on the button
- `submit`
- `success` or `error`

You can edit the field values programmatically using the `onsubmit` event handler or selectively handle any of the custom events. See Overriding Default Behaviors.

**Error Handling**

`lightning-record-edit-form` handles field-level validation errors and Lightning Data Service errors automatically. For example, entering an invalid email format for the Email field results in an error message when you move focus away from the field. Similarly, a required field like the Last Name field displays an error message when you leave the field blank and move focus away.

A Lightning Data Service error is returned when a resource becomes inaccessible on the server or an invalid record ID is passed in, for example. To display the error message automatically, include `lightning-messages` immediately before or after the `lightning-input-field` components. For more information, see Overriding Default Behaviors.

lightning-record-edit-form also verifies data input based on your validation rules. The form submits and saves data input only if all data in the fields are valid. The form clears validation rule errors when an onchange event is fired on the overall form, and also when you update a field with a validation rule error.

If a single field has multiple validation errors, the form shows only the first error on the field. Similarly, if a submitted form has multiple errors, the form displays only the first error encountered. When you correct the displayed error, the next error is displayed.

We recommend using custom validation rules to verify data input instead of implementing client-side validation errors. A validation rule can contain a formula or expression that evaluates the data in one or more fields. You can include an error message to display on an invalid field. See [Validation Rules](https://help.salesforce.com/articleView?id=fields_about_field_validation.htm) in Salesforce Help for more information.

**Resetting the Form**

We recommend creating a button that reverts the field values to their initial values using `lightning-button`. The default type for `lightning-button` is button, which does nothing unless you include an onclick handler.

If you use an HTML button element within `lightning-record-edit-form` to perform an action such as resetting the field values, specify `type="button"`. By default, an HTML button element uses `type="submit"` when it's rendered in an HTML form element. Additionally, using `type="reset"` on a button deletes the form values and does not preserve the intial values.

**Custom Events**

`loads`

The returned record data includes the fields contained in the Full layout, and the input and output fields specified in `lightning-record-edit-form`.

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-record-edit-form`, see the following components in the LWC Recipes repo.

- `c-record-edit-form-dynamic-contact`
- `c-record-edit-form-static-contact`


## lightning-record-form

### Documentation

Link to [lightning-record-form documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-record-form/documentation)

**Custom Events**

### Specification

`error`

The event fired when the record form returns a server-side error.

Use the `event.detail` property to return the error.

PARAMETER | TYPE | DESCRIPTION
-------------- | -------------- | --------------
message | string | General description of error.
detail | object | Description of error details, if any.
output | object | [Record exception errors](https://developer.salesforce.com/docs/atlas.en-us.uiapi.meta/uiapi/ui_api_responses_record_exception.htm#ui_api_responses_record_exception) with errors and `fieldErrors` properties. For example, to return the error details when a required field is missing, use event.`detail.output.fieldErrors`.

The event properties are as follows.

PARAMETER | VALUE | DESCRIPTION
-------------- | -------------- | --------------
bubbles | false | This event does not bubble.
cancelable | false | 	This event has no default behavior that can be canceled. You can't call `preventDefault()` on this event.
composed | false | This event does not propagate outside the template in which it was dispatched.

`load`

The event fired when the record form loads record data.

`load` is fired when the form gets new data from Lightning Data Service, which can be once or multiple times after the component is initialized. For example, the load event is fired when:

- The `record-id` value changes
- The fields list changes
- The form includes picklist fields
- The record type changes
- If you require the load event to be called only once, write code to prevent it from running more than once.

Use the `event.detail` property to return the [record UI](https://developer.salesforce.com/docs/atlas.en-us.uiapi.meta/uiapi/ui_api_responses_record_ui.htm), and [picklist values](https://developer.salesforce.com/docs/atlas.en-us.uiapi.meta/uiapi/ui_api_responses_picklist_values.htm) if you include picklist fields in the form.

The returned record data includes the fields that are contained in the specified Full or Compact layout, and any fields you specify in `lightning-record-form`.

The event properties are as follows.

PARAMETER | VALUE | DESCRIPTION
-------------- | -------------- | --------------
bubbles | false | This event does not bubble.
cancelable | false | This event has no default behavior that can be canceled. You can't call `preventDefault()` on this event.
composed | false | This event does not propagate outside the template in which it was dispatched.

`submit`

The event fired when the submit button is pressed. Client-side validation errors, if any, are displayed. The form is then submitted only when all fields in the form are valid. The form can be submitted only after it's loaded.

The submit event returns the following parameters.

PARAMETER | VALUE | DESCRIPTION
-------------- | -------------- | --------------
fields | object | The editable fields that are provided for submission during a record create or edit. For example, if you include the Name field, fields returns FirstName, LastName, and Salutation. Read-only fields, such as the record ID, can't be changed in a form. If you include a read-only field in a form, it's not included in the fields object returned by the onsubmit event handler.

The event properties are as follows.

PARAMETER | VALUE | DESCRIPTION
-------------- | -------------- | --------------
bubbles | true | This event bubbles up through the DOM.
cancelable | true | This event can be canceled. You can call `preventDefault()` on this event.
composed | true | This event propagates outside of the component in which it was dispatched.

`success`

The event fired when the record data is updated successfully. The load event then fires to return the updated data.

Use the event.detail property to return the saved record. For more information, see the [User Interface API Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.uiapi.meta/uiapi/ui_api_responses_record.htm).

The event properties are as follows.

PARAMETER | VALUE | DESCRIPTION
-------------- | -------------- | --------------
bubbles | true | This event bubbles up through the DOM.
cancelable | true | This event can be canceled. You can call `preventDefault()` on this event.
composed | true | This event propagates outside of the component in which it was dispatched.

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-record-form`, see the following components in the LWC Recipes repo.

- `c-record-form-dynamic-contact`
- `c-record-form-static-contact`


## lightning-record-view-form

### Documentation

Link to [lightning-record-view-form documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-record-view-form/documentation)

**Custom Events**

`load`

The returned record data includes the fields contained in the Full layout, and the output fields specified in `lightning-record-view-form`.

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-record-view-form`, see the following components in the LWC Recipes repo.

- `c-record-view-form-dynamic-contact`
- `c-record-view-form-static-contact`


## lightning-relative-date-time

### Documentation

Link to [lightning-relative-date-time documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-relative-date-time/documentation)

It formats the relative time for the current locale following the rules from [Unicode CLDR](http://cldr.unicode.org/translation/date-time-1/date-time-names).

The user's language setting in an org determines the language displayed for the units of time. If the locale uses a different language, the output uses the language setting and ignores the locale. For example, if you set the locale to Arabic and the language to English, the output uses digits 0-9 for numbers and English instead of Arabic numerals to be consistent with the language on the user interface. For more information, see [Supported Languages](https://help.salesforce.com/articleView?id=faq_getstart_what_languages_does.htm).

To obtain the language and locale information in your org, use the `@salesforce/i18n` scoped module. For more information, see [Access Internationalization Properties](https://developer.salesforce.com/docs/component-library/documentation/en/lwc/lwc.create_i18n).

## lightning-textarea

### Documentation

Link to [lightning-textarea documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-textarea/documentation)

**Using Autocomplete**

Textarea fields can be autofilled, based on your browser's support of the feature. The `autocomplete` attribute passes through its value to the browser.

See [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete) for more information.

## lightning-tree

### Documentation

Link to [lightning-tree documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-tree/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-tree`, see the `c-wire-get-picklist-values-by-record-type` component in the LWC Recipes repo.

## lightning-ui-object-info-api

### Documentation

Link to [lightning-ui-object-info-api documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-ui-object-info-api/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning-tree`, see the `c-wire-get-picklist-values-by-record-type` component in the LWC Recipes repo.

## lightning-ui-record-api

### Documentation

Link to [lightning-ui-record-api documentation](https://developer.salesforce.com/docs/component-library/bundle/lightning-ui-record-api/documentation)

**LWC Recipes**

The [LWC Recipes GitHub repository](https://github.com/trailheadapps/lwc-recipes) contains code examples for Lightning Web Components that you can test in an org.

For a recipe that uses `lightning/uiRecordApi`, see the following components in the LWC Recipes repo.

- `c-wire-get-record-dynamic-contact`
- `c-wire-get-record-static-contact`
- `c-wire-get-record-user`
