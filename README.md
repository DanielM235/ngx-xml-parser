# NgxXmlParser
Small angular library to parse and read xml files.


### Installation

`npm install ngx-xml-parser`

To use the library, in your root module, import `NgxXmlParserModule` specifying the default parser :


```typescript

import { NgxXmlParserModule, DefaultXmlParser, HotmailArchiveParser } from 'ngx-xml-parser';

@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    NgxXmlParserModule.forRoot({
      defaultParser: { provide: DefaultXmlParser, useClass: HotmailArchiveParser }
    })
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {
}
```

You can define your own parser as an injectable service implementing the `IXmlParser` interface :

```typescript
import { InjectionToken } from '@angular/core';
import { XmlItem } from '../reader';

interface IXmlParser {
  parse(sourceFile?: string | File): Promise<XmlItem[]>;
}
```

Then just call the component in the template :

```angular2html
<ngx-xml-parser></ngx-xml-parser>
```

## Development server

Run `npm run startLib` to build the library in dev mode.
Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
