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

## Tip:
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
## Check: Add Search component html
```
<h4>Advanced Search</h4>
<form #f="ngForm">
  <div class="form-group">
    <label for="title">Product title:</label>
    <input id="title"
           placeholder="Title" type="text"
           name="title" ngModel>
  </div>
  <div class="form-group">
    <label for="price">Product price:</label>
    <input id="price"
           placeholder="Price" type="number"
           name="price" ngModel>
  </div>
  <div class="form-group">
    <label for="category">Category:</label><br/>
    <select id="category"
            placeholder="Category"
            name="category" ngModel>
      <option>books</option>
      <option>electronics</option>
      <option>hardware</option>
    </select>
  </div>
  <div class="form-group">
    <button type="submit"
            class="btn btn-primary btn-block">Search</button>
  </div>
</form>
```
## Tip: blank screen fix
The browser stopped rendering the app. Its console shows an error "There is no directive with "exportAs" set to "ngForm" - it doesn’t know about ngForm, which is a part of Angular Forms API. Add the FormsModule to the imports section of app.module.ts:
```
import {FormsModule} from "@angular/forms";

@NgModule({
  ...
  imports: [
    FormsModule,
```

## Check: Add Footer component html
```
<div class="container">
  <hr>
  <footer>
    <div class="row">
      <div class="col-lg-12">
        <p>Copyright &copy; My Store 2018</p>
      </div>
    </div>
  </footer>
</div>
```
## Check: Add shared/prodct.ts
```
export interface Product {
    id: number;
    title: string;
    price: number;
    rating: number;
    shortDescription: string;
    description: string;
    categories: string[];
}
```
## Check: Add product.service.ts code
```

```import { Injectable } from '@angular/core';
import { Product } from './product';

@Injectable({
  providedIn: 'root'
})
export class ProductService {

  getProducts(): Product[] {
    return products;
  }

  getProductById(productId: number): Product {
    return products.find(p => p.id === productId);
  }
}

const products = [
  {
    "id": 0,
    "title": "First Product",
    "price": 24.99,
    "rating": 4.3,
    "shortDescription": "This is a short description of the First Product",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "categories": ["electronics", "hardware"]
  },
  {
    "id": 1,
    "title": "Second Product",
    "price": 64.99,
    "rating": 3.5,
    "shortDescription": "This is a short description of the Second Product",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "categories": ["books"]
  },
  {
    "id": 2,
    "title": "Third Product",
    "price": 74.99,
    "rating": 4.2,
    "shortDescription": "This is a short description of the Third Product",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "categories": ["electronics"]
  },
  {
    "id": 3,
    "title": "Fourth Product",
    "price": 84.99,
    "rating": 3.9,
    "shortDescription": "This is a short description of the Fourth Product",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "categories": ["hardware"]
  },
  {
    "id": 4,
    "title": "Fifth Product",
    "price": 94.99,
    "rating": 5,
    "shortDescription": "This is a short description of the Fifth Product",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "categories": ["electronics", "hardware"]
  },
  {
    "id": 5,
    "title": "Sixth Product",
    "price": 54.99,
    "rating": 4.6,
    "shortDescription": "This is a short description of the Sixth Product",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "categories": ["books"]
  }
];
```

## Tip: new to Angular 6.x
```
@Injectable({
  providedIn: 'root'
})
```
This is the DI provider  save you from adding it in the NgModule secrion ```Providers:[ServiceProvider],```

## Check: Add Product-item component code, html and css
```
import {Component, Input} from '@angular/core';
import {Product} from '../shared/product';

@Component({
  selector: 'app-product-item',
  templateUrl: './product-item.component.html',
  styleUrls: ['./product-item.component.css']
})
export class ProductItemComponent {

  @Input() product: Product;
}
```
We’ll use the HTML 5 tags <figure>, <figcaption> and Bootstrap styles in the file product-item.component.html. The routerLink directive will be used to nabigate to the product detail view. Change its content to the following:
```
<figure class="figure">
  <img src="http://placehold.it/320x150" class="figure-img img-fluid rounded">
  <figcaption class="figure-caption">
    <h5><a [routerLink]="['/products', product.id]">{{product.title}}</a>
        <span>{{product.price | currency}}</span>
    </h5>
    <p>{{product.shortDescription}}</p>
  </figcaption>
</figure>
```
And css
```
figure {
    margin-top: 1em;
    margin-bottom: 1em;
    margin-left: 5px;
    margin-right: 5px;
  }
```

## Check: Add Home component code, html and css
```
import { Component, OnInit } from '@angular/core';
import { Product } from '../shared/product';
import { ProductService } from '../shared/product.service';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {

  products: Product[] = [];
  constructor(private productService: ProductService) { }

  ngOnInit() {
    this.products = this.productService.getProducts();
  }
}
```
```
<div class="row">
  <div *ngFor="let product of products" class="col-sm-4 col-lg-4 col-md-4">
    <app-product-item [product]="product"></app-product-item>
  </div>
</div>
```
```
figure {
    margin-top: 1em;
    margin-bottom: 1em;
    margin-left: 5px;
    margin-right: 5px;
  }
  ```
  ## Test screen shot
  
  ![Screen Shot](/resources/GUI.png)
