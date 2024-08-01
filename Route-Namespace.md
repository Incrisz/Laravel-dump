# Configuring Routes in the `boot` Function

## Overview

The `boot` function in the `app\Providers\RouteServiceProvider` is responsible for defining how routes are loaded and configured in your Laravel application. It allows you to specify routing behavior, including middleware, namespaces, and route files.

## Structure of the `boot` Function

```php


## at your 'app\Providers\RouteServiceProvider' Location

## Declare this

protected $namespace = 'App\Http\Controllers';



## Make changes to Boot function

public function boot()
{
    $this->configureRateLimiting();

    $this->routes(function () {
        Route::middleware('api')
            ->prefix('api')
            ->namespace($this->namespace) // Base namespace for API routes
            ->group(base_path('routes/api.php'));

        Route::middleware('web')
            ->namespace($this->namespace) // Base namespace for Web routes
            ->group(base_path('routes/web.php'));
    });
}


## Route/web.php

Route::group(['namespace' => 'SupportTeam'], function(){
    Route::get('/test', 'StudentRecordController@create')->name('create');
});
