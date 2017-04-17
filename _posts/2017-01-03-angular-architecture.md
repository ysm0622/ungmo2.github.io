---
layout: post
title: Angular <strong>Architecture</strong>
subtitle: Angular의 파일 구조와 구성 요소
categories: angular
section: angular
description: Angular CLI를 사용하여 프로젝트를 생성하면 아래와 같은 파일 구조의 스캐폴딩이 생성된다. Angular 프로젝트는 컴포넌트, 디렉티브, 서비스, 모듈 등 Angular 구성요소와 각종 설정 파일로 구성된다.
---

* TOC
{:toc}

![angular Logo](/img/angular-logo.png)

# 1. 프로젝트 파일의 구조

Angular CLI를 사용하여 프로젝트를 생성하면 아래와 같은 파일 구조의 스캐폴딩이 생성된다.

```bash
$ ng new my-app
```

```
my-app/
├── .angular-cli.json
├── .editorconfig
├── .git/
├── .gitignore
├── e2e/
│   ├── app.e2e-spec.ts
│   ├── app.po.ts
│   └── tsconfig.e2e.json
├── karma.conf.js
├── node_modules/
├── package.json
├── protractor.conf.js
├── README.md
├── src/
│   ├── app/
│   │   ├── app.component.css
│   │   ├── app.component.html
│   │   ├── app.component.spec.ts
│   │   ├── app.component.ts
│   │   └── app.module.ts
│   ├── assets/
│   ├── environments/
│   │   ├── environment.prod.ts
│   │   └── environment.ts
│   ├── favicon.ico
│   ├── index.html
│   ├── main.ts
│   ├── polyfills.ts
│   ├── styles.css
│   ├── test.ts
│   ├── tsconfig.app.json
│   ├── tsconfig.spec.json
│   └── typings.d.ts
├── tsconfig.json
└── tslint.json
```

Angular는 프레임워크이므로 웹 어플리케이션의 기본적인 기능을 구현한 구현체를 정형화된 구조로 제공한다. 이것을 바탕으로 우리의 어플리케이션에 필요한 기능을 추가하는 방식으로 어플리케이션을 완성해 간다. 따라서 프레임워크의 학습은 정형화된 프레임워크의 구조에 익숙해지는 것으로 시작한다. Angular가 제공하는 기본 구조와 각 파일의 기능을 살펴보도록 하자.

우리가 앞으로 작성할 코드는 기본적으로 src 폴더에 소속된다.

## 1.1 src

Angular 프로젝트는 컴포넌트, 디렉티브, 서비스, 모듈 등 Angular 구성요소와 각종 설정 파일로 구성된다.

`src` 폴더는 Angular의 모든 구성요소, CSS, 이미지 등 어플리케이션 필수 파일을 담고 있다.

`src/app` 폴더에는 Angular 구성요소가 위치하게 된다. 현재는 컴포넌트와 모듈만 존재하지만 구성요소가 추가되면 이 폴더에 위치하게 된다. 개발자가 작성하는 대부분의 파일은 이곳에 포함된다.

- app/app.component.{ts, html, css, spec.ts}  
: 컴포넌트를 구성하는 AppComponent, HTML 템플릿, CSS, 유닛 테스트 파일. 다른 컴포넌트가 추가되면 컴포넌트 트리에서 루트 컴포넌트로 역할을 담당하게 된다.

- app/app.module.ts  
: Angular 구성요소를 등록하는 루트 모듈 AppModule.

- assets/*  
: 이미지 등과 같은 정적 파일을 위한 폴더. 프로젝트 생성 초기에는 빈 폴더이다.

- environments/*  
: 프로젝트 빌드 시에 사용될 프로덕션 또는 개발 환경 설정 파일.

- favicon.ico  
: 파비콘

- index.html  
: 웹사이트에 방문시 처음으로 로딩되는 디폴트 페이지. 루트 컴포넌트의 샐렉터에 의해 <app-root> 내에 템플릿이 표시되며 빌드 시 번들링된 JavaScript 파일이 자동 추가된다.

- main.ts  
: 프로젝트의 메인 진입점. platformBrowserDynamic()에 의해 JIT 컴파일러가 실행되고 루트 모듈(AppModule)을 부트스트랩한다.

- polyfills.ts  
: Change Detection을 위한 zone.js와 ES6/ES7와 크로스 브라우저 웹 표준 지원을 위한 폴리필을 임포트한다. 자세한 내용은 [Browser support](https://angular.io/docs/ts/latest/guide/browser-support.html) 참조.

- styles.css  
: 어플리케이션 전역에 적용되는 글로벌 CSS.

- test.ts  
: 유닛 테스트를 위한 메인 진입점.

- tsconfig.{app|spec}.json  
: TypeScript 컴파일 옵션 설정 파일.

- typings.d.ts  
: TypeScript를 위한 타입 선언 파일.

## 1.2 그외의 파일

src 폴더 밖의 파일들은 테스트, 빌드, 배포 등을 위한 각종 설정 파일이다.

- e2e/  
: e2e(end-to-end) 테스트 관련 파일

- node_modules/  
: 의존 모듈 저장소. 패키지 매니저에 의해 package.json에 등록된 의존 모듈이 설치되는 장소이다.

- .angular-cli.json  
: Angular CLI를 위한 설정 파일. 상세한 설정 방법은 [Angular CLI Config Schema](https://github.com/angular/angular-cli/wiki/angular-cli) 참조.

- .editorconfig  
: 코드 에디터 기본 설정 파일. 상세한 설정 방법은 [http://editorconfig.org](http://editorconfig.org) 참조

- .gitignore  
: Git 소스 관리 제외 대상을 위한 설정 파일.

- karma.conf.js  
: [Karma test runner](https://karma-runner.github.io/1.0/index.html)를 위한 유닛 테스트 설정 파일. ng test 명령어 실행시 참조된다.

- package.json  
: 의존 모듈 관리를 위해 패키지 매니저가 사용하는 모듈 관리 파일.

- protractor.conf.js  
: e2e 테스트를 위해 [Protractor](http://www.protractortest.org/#/)가 사용하는 설정 파일. ng e2e 명령어 실행시 참조된다.

- README.md  
: 프로젝트의 개요를 기술한 README 파일. Angular CLI가 기본적인 내용을 자동 생성한다.

- tsconfig.json  
: TypeScript 컴파일 옵션 설정 파일

- tslint.json  
: [TSLint](https://palantir.github.io/tslint/)가 사용하는 linting(구문 체크) 설정 파일. ng lint 명령어 실행시 참조된다.

# 2. Angular의 구성 요소

Angular는 컴포넌트를 중심으로 Angular 구성요소를 조합하여 어플리케이션을 구축한다.

컴포넌트는 Angular 고유의 마크업인 템플릿 문법을 사용하여 작성된 HTML 템플릿과 이러한 템플릿을 관리하기 위해 컴포넌트 클래스로 구성된다. 어플리케이션에서 공통으로 사용하는 어플리케이션 로직은 서비스에 작성하고 컴포넌트와 서비스 등의 구성요소를 모듈에 등록한다. 어플리케이션은 루트 모듈을 부트스트랩핑하는 것으로 동작한다.

Angular 어플리케이션의 핵심 구성요소는 아래와 같다.

- 컴포넌트 (Component)
- 모듈 (Module)
- 디렉티브 (Directive)
- 서비스 (Service)

![angular-element](./img/angular-element.png)

## 2.1 컴포넌트

컴포넌트는 Angular 구성요소의 핵심으로 어플리케이션 뷰(View)를 구성하는 단위가 된다. 컴포넌트의 궁극적인 역할은 뷰를 생성하여 브라우저에 표시하고 관리하는 것이다.

컴포넌트는 템플릿과 컴포넌트 클래스로 구성된다.

템플릿  
: 
- <strong>뷰</strong>(화면을 구성하는 한부분)를 표현하기 위해 HTML을 동적으로 생성한다. 
- HTML과 Angular 고유의 템플릿 문법을 사용하여 작성한다.  
- 다른 컴포넌트, 디렉티브, 파이프를 포함시킬 수 있다.
- 컴포넌트마다 별도의 가상 DOM(Virtual DOM)을 사용한다. 따라서 다른 컴포넌트의 스타일에 영향을 주지 않는다.

컴포넌트 클래스  
: 
- 뷰를 관리하는 <strong>로직</strong>을 포함한다.
- import 구문과 의존성 주입(Dependency Injection)을 통해 다른 클래스나 서비스를 사용할 수 있다.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <h1>안녕하세요 {{ "{{name" }}}}</h1>
    <hr>
    <input type="text" placeholder="이름을 입력하세요" #inputYourName>
    <button (click)="setName(inputYourName.value)">등록</button>  
  `
})
export class AppComponent {
  name = 'Angular';

  setName(name) {
    this.name = name;
  }
}
```

템플릿과 컴포넌트 클래스는 데이터 바인딩을 통해 연결된다. 바인딩을 통해 클래스에서 템플릿으로 데이터를 전달하거나 템플릿에서 클래스로 이벤트를 전달한다.

컴포넌트는 @Component 데코레이터를 가지고 있는 클래스이다. @Component 데코레이터 함수는 메타데이터 객체를 전달받아 컴포넌트를 정의한다. 메타데이터 객체의 중요 프로퍼티는 아래와 같다.

- seletor 속성
: 컴포넌트를 마크업으로 표현할 때의 이름 
- template 속성  
: 인라인으로 정의된 템플릿
- templateUrl 속성  
: 외부 파일로 정의된 템플릿의 경로
- styles 속성
: 인라인의 정의된 CSS의 배열
- styleUrls 속성  
: 외부 파일로 정의된 CSS 경로의 배열

## 2.2 모듈

컴포넌트는 단독으로 동작할 수 없으며 모듈에 등록되어야 한다. 컴포넌트뿐만 아니라 모든 구성요소는 모듈에 등록되어야 사용할 수 있다.

Angular 어플리케이션은 여러개의 모듈로 구성될 수 있으며 적어도 하나 이상의 모듈을 갖는다. 최상위에 위치하는 모듈을 루트 모듈이라하며 일반적으로 AppModule로 명명한다. 어플리케이션은 main.ts에서 루트 모듈을 부트스트랩핑하는 것으로 동작한다.

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { HttpModule } from '@angular/http';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    FormsModule,
    HttpModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

모듈은 @NgModule 데코레이터를 가지고 있는 클래스이다. @NgModule 데코레이터 함수는 메타 데이터 객체를 전달받아 모듈을 정의한다. 메타 데이터 객체의 중요 프로퍼티는 아래와 같다.

- declarations 속성
: 모듈에 소속될 구성요소(컴포넌트, 디렉티브, 파이프) 리스트
- imports 속성  
: 모듈에 소속된 구성요소가 필요로 하는 다른 모듈
- providers 속성
: 모듈에 소속된 구성요소가 사용할 서비스
- bootstrap 속성
: 최초로 호출될 컴포넌트

## 2.3 디렉티브

Angular는 디렉티브에 의해 DOM을 변환하여 템플릿을 렌더링한다. 디렉티브는 컴포넌트의 템플릿에서 HTML 요소 또는 HTML 요소의 속성과 유사하게 사용된다.

디렉티브에는 구조 디렉티브(Structural directive)와 속성 디렉티브(Attribute directive)가 있다.

- 구조 디렉티브  
: DOM 요소를 추가, 삭제 등 DOM 트리를 동적으로 조작하여 레이아웃을 변경할 때 사용한다.
: ngIf, ngSwithch, ngFor

- 속성 디렉티브
: DOM의 모습이나 동작을 조작하기 위해 사용한다.
: ngClass, ngStyle

디렉티브는 @Directive 데코레이터를 가지고 있는 클래스이다. 사실은 컴포넌트도 디렉티브이다. 컴포넌트와 디렉티브의 차이는 템플릿을 가지고 있는가이다. 즉 컴포넌트는 템플릿이 있는 디렉티브이다.

## 2.4 서비스

어플리케이션의 다양한 목적의 비즈니스 로직을 담당하는 클래스이다. 컴포넌트에서 공통 처리 로직을 분리하기 위해 사용하며 의존성 주입(Dependency Injection)이 가능한 클래스로 작성된다. 서비스의 사용 사례는 아래와 같다.

- 로깅 서비스
- 데이터 공유 서비스
- 사용자 인증 서비스


# Reference

* [Angular](https://angular.io/)