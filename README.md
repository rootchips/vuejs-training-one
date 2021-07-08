## VueJS Installation

Untuk penerangan. PHP adalah `Backend` dan kerangkanya ialah `Laravel`. Javascript adalah Frontend dan kerangkanya ialah `VueJS`.

Untuk `VueJS Framework`, disarankan menginstall `VueJS DevTools` di `Chrome Extension`.

* Sesudah install Laravel sampai ke copy .env file, dan generate key.

Sambung ini untuk install VueJS

1. Install package depedency UI daripada Laravel - Untuk Laravel 5.8 ke atas, ia telah dipisahkan daripada library Laravel. Jadi harus menginstall secara berasingan. Ini kerana terdapat ramai Frontend Developer menggunakan framework lain seperti Svelte, Angular, dan React.
```sh
$ composer require laravel/ui
```

2. Generate VueJS Scaffolding - Ia akan menjana file `ExampleComponent.vue` di `resources/js/components` dan menjana beberapa baris kod Javascript di `resources/js/app.js` untuk VueJS.
```sh
$ php artisan ui vue
```

3. Install NPM - Ia berfungsi seperti Composer, menginstall package dependency lalu mencipta folder `node_modules`. Di dalam folder ini terdapat banyak library yang dicipta oleh developer seluruh dunia.
```sh
$ npm install
```
Jika terdapat ralat semasa install, sila kenal pasti ralat dengan jelas. Kadang-kadang ia adalah ralat daripada `node` version atau harus menginstall package lain terdahulu.

4. Compile script - Secara tetapan yang telah dibuat di `resources/js/components/app.js`. Iaitu baris kod di bawah. Kemudian ia akan menggunakan `Laravel Mix` untuk compile script ini.
`Laravel Mix` akan membaca `webpack.mix.js`, kemudian ia akan menjana file di `public/js/app.js`

`webpack.mix.js`
```js
const mix = require('laravel-mix');

/*
 |--------------------------------------------------------------------------
 | Mix Asset Management
 |--------------------------------------------------------------------------
 |
 | Mix provides a clean, fluent API for defining some Webpack build steps
 | for your Laravel application. By default, we are compiling the Sass
 | file for the application as well as bundling up all the JS files.
 |
 */

mix.js('resources/js/app.js', 'public/js') // Ia akan generate app.js di folder ini
    .vue()
    .sass('resources/sass/app.scss', 'public/css');
```

`resources/js/app.js`
```js
/**
 * First we will load all of this project's JavaScript dependencies which
 * includes Vue and other libraries. It is a great starting point when
 * building robust, powerful web applications using Vue and Laravel.
 */

require('./bootstrap');

window.Vue = require('vue').default; 

/**
 * The following block of code may be used to automatically register your
 * Vue components. It will recursively scan this directory for the Vue
 * components and automatically register them with their "basename".
 *
 * Eg. ./components/ExampleComponent.vue -> <example-component></example-component>
 */

// Ini akan register Vue Component di resources/js/components/ExampleComponent
Vue.component('example-component', require('./components/ExampleComponent.vue').default);

/**
 * Next, we will create a fresh Vue application instance and attach it to
 * the page. Then, you may begin adding components to this application
 * or customize the JavaScript scaffolding to fit your unique needs.
 */


// Ini akan attach di welcome.blade.php
const app = new Vue({
    el: '#app',
});
```

Kemudian run compiler dalam mode development.
```sh
$ npm run dev
```
Run ini boleh juga, ia akan stay active kemudian apa perubahan di `app.js` dan file berkaitan dengan `.vue`, ia akan compile secara automatik.
```sh
$ npm run watch
```
5.	Di blade master layout seperti master, app, atau welcome. Harus letak template sebegini untuk memaparkan komponen vue dan script daripada `public/js/app.js`
```html
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
	# Attach di sini
	<div id="app">
		<example-component></example-component>
	</div>

	# Untuk load file yang telah di compile public/js/app.js
	<script src="{{ asset('js/app.js') }}"></script>
</body>
</html>
```

6. Sila lihat di browser anda samada ia berjaya dipaparkan atau tidak, jika tidak. Sila debug dengan menggunakan `Chrome Developer Tools` untuk melihat ralat-ralat itu.

&nbsp;
&nbsp;
&nbsp;

## Assignment 1
1.	Sila create satu file bernama `AssignmentOneComponent.vue`
2.	Buat satu `button` untuk memanipulasikan perkataan `Saya sedang belajar VueJS`.
3. Apabila `button` itu diclick. Ia akan `reverse` kan perkataan tersebut menjadi `JSeuV rajaleb gnades ayaS`.

## Assignment 2
1. Sila create satu file bernama `AssignmentTwoComponent.vue`
2. Memanipulasikan `nombor` (bermula daripada `5`) secara menurun dengan menekan `button`.
3. Jika ia telah mencapai `nilai 0`, maka `button` untuk menurun telah di hide, dan `button` menaik pula muncul untuk menambahkan `nilai 0` kepada `5` semula.

### Sila rujuk dokumentasi di <a href="https://vuejs.org/v2/guide/">https://vuejs.org/v2/guide/</a>
