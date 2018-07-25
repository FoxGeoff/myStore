# MyStore

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.0.8.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

# myStore step by step example (7/25/2018 rev 1.0)

## Check: setup the initial project
1. Run ```   ```
1. Run ```   ```

## Check: Add Bootstrap 4.x
1. Run ```npm i bootstrap jquery popper.js```
1. Add to angular.json ``` "styles": [
  "styles.css",
  "node_modules/bootstrap/dist/css/bootstrap.min.css"
],```
1. Add to angular.json ```"scripts": [
  "node_modules/jquery/dist/jquery.js",
  "node_modules/popper.js/dist/umd/popper.js",
  "node_modules/bootstrap/dist/js/bootstrap.js"
]```

## Check: Add components, service and routes
1. Run ```ng g c home --spec false```
1. Run ```ng g c footer --spec false```
1. Run ```ng g c navbar --spec false```
1. Run ```ng g c product-item --spec false```
1. Run ```ng g c product-detail --spec false```
1. Run ```ng g c search --spec false```
1. Run ```ng g s shared/product --spec false```

##Tip: 
If you see an error like ```You seem to not be depenging on '@angular/core' and/or 'rxjs' ```, delete node_modules and run ```npm install`` to rebuild this folder.

## Check: Add app.component.html
1. Add to app component.html
1. Tip: to see the bootstrap style applied close the server and run ```sever -o```
```
<app-navbar></app-navbar>

<div class="container">
  <div class="row">
    <div class="col-md-3">
      <app-search></app-search>
    </div>

    <div class="col-md-9">
      <router-outlet></router-outlet>
    </div>
  </div>
</div>

<app-footer></app-footer>
```

## Check: Add Navbar component html
1. Add to navbar.component.ts
```
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Dropdown
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <div class="dropdown-divider"></div>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled" href="#">Disabled</a>
      </li>
    </ul>
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
    </form>
  </div>
</nav>
```
