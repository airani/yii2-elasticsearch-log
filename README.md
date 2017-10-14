Yii 2.0 Elasticsearch log target
================================

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require -vv --prefer-dist airani/yii2-elasticsearch-log
```

or add below line to the composer.json and run `php composer.phar update -vv --prefer-dist --profile`

```
"airani/yii2-elasticsearch-log": "~1.0"
```

Usage
-----
Config elasticsearch log target in config file like below code. with set `extraFields` property in log target config you can set more extra fields to log results.

```php
'components' => [
    // ...
    'log' => [
        'targets' => [
            [
                'class' => 'airani\log\ElasticsearchTarget',
                'levels' => ['error', 'warning'],
                'index' => 'yii',
                'type' => 'log',
                'db' => 'elasticsearch',
                'extraFields' => [
                    'ip' => function ($app) {
                        return $app->request->getUserIP();
                    }
                ]
            ],
        ],
    ],
],
```