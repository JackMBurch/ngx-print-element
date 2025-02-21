# ngx-print-element

This library is built to provide a solution for printing on html elements.\
This is the [stackblitz](https://stackblitz.com/edit/angular-ngx-print-element?file=src/app/app.component.html).

![Logo](https://raw.githubusercontent.com/id1945/ngx-print-element/master/ngx-print-element.png)

## Installation
Install `ngx-print-element` from `npm`:
```bash
npm install ngx-print-element --save
```

Add wanted package to NgModule imports:
```typescript
import { NgxPrintElementModule } from 'ngx-print-element';
@NgModule({
    imports: [
        NgxPrintElementModule,
    ]
})
```
Need to import css
```scss
@import '~ngx-print-element/styles.css';
```
Printing data sheet with id is up to you.\
If there is an element you don't want to display you can add the class ```print-none```

### 1# The first way doesn't need configuration
```html
<table id="demo" class="table table-bordered">
  <tr>
    <th>No</th>
    <th>Company</th>
    <th>Contact</th>
    <th>Country</th>
  </tr>
  <tr class="print-none" style="background: greenyellow"><!-- No print -->
    <td>01</td>
    <td>Alfreds Futterkiste</td>
    <td>Maria Anders</td>
    <td>Germany</td>
  </tr>
  <tr>
    <td>02</td>
    <td>Centro comercial Moctezuma</td>
    <td>Francisco Chang</td>
    <td>Mexico</td>
  </tr>
  <tr>
    <td>03</td>
    <td>AIS Playground</td>
    <td>Nakhon Pathom</td>
    <td>Thailand</td>
  </tr>
  <tr class="print-none" style="background: greenyellow"> <!-- No print -->
    <td>04</td>
    <td>FPT Software</td>
    <td>Cau Giay</td>
    <td>Vietnamese</td>
  </tr>
</table>

<button [print]="['demo']">Print</button>
```

### 2# The second way needs configuration
```html

<table id="demo" class="table table-bordered">
  <tr>
    <th>No</th>
    <th>Company</th>
    <th>Contact</th>
    <th>Country</th>
  </tr>
  <tr class="print-none" style="background: greenyellow"><!-- No print -->
    <td>01</td>
    <td>Alfreds Futterkiste</td>
    <td>Maria Anders</td>
    <td>Germany</td>
  </tr>
  <tr>
    <td>02</td>
    <td>Centro comercial Moctezuma</td>
    <td>Francisco Chang</td>
    <td>Mexico</td>
  </tr>
  <tr>
    <td>03</td>
    <td>AIS Playground</td>
    <td>Nakhon Pathom</td>
    <td>Thailand</td>
  </tr>
  <tr class="print-none" style="background: greenyellow"> <!-- No print -->
    <td>04</td>
    <td>FPT Software</td>
    <td>Cau Giay</td>
    <td>Vietnamese</td>
  </tr>
</table>

<button [print]="['demo', config]">Print</button>
```

```typescript
import { Component } from '@angular/core';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  public config = {
    printMode: 'template-popup',
    popupProperties: 'toolbar=yes,scrollbars=yes,resizable=yes,top=0,left=0,fullscreen=yes',
    pageTitle: 'Hello World',
    templateString: '<header>I\'m part of the template header</header>{{printBody}}<footer>I\'m part of the template footer</footer>',
    stylesheets: [{ rel: 'stylesheet', href: 'https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css' }],
    styles: ['td { border: 1px solid black; color: green; }', 'table { border: 1px solid black; }', 'header, table, footer { margin: auto; text-align: center; }']
  }
}
```

#### Services
```typescript
import { Component } from '@angular/core';
import { NgxPrintElementService } from 'ngx-print-element';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  constructor(public print: NgxPrintElementService) {}
}
```

```html
<p id="demo">Angular-Print</p>
<button (click)="print.print('demo')">Print</button>
```

#### API Documentation

| Field | Description | Type | Default |
| --- | --- | --- | --- |
| htmlType | `domObj`,`text` | string | `'domObj'` |
| printMode | `template`,`template-popup` | string | `template` |
| popupProperties | Options [window.open](https://www.w3schools.com/jsref/met_win_open.asp) | string | blank |
| pageTitle | Print title | string | blank |
| templateString | html | string | blank |
| stylesheets | Set the external style sheet for printing | object or object[] | null |
| styles | Set the internal style sheet for printing | string or string[] | null |


### Support versions
| ng version  |   version   |
|     ---     |     ---     |
|  Angular 8  | 8.0.14      |
|  Angular 9  | 8.0.14-rc.1 |
|  Angular 14 | 2.0.15      |


Author: `DaiDH`, Tel: `0845882882`

### License

[MIT License](https://github.com/id1945/ngx-print-element/blob/master/LICENSE). Copyright (c) 2022 DaiDH
