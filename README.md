EAV-behavior

============

EAV behavior for ActiveRecord



Installation

------------



The preferred way to install this extension is through [composer](http://getcomposer.org/download/).



Either run



```

php composer.phar require --prefer-dist reshik84/yii2-eav-behavior "*"

```



or add



```

"reshik84/yii2-eav-behavior": "*"

```



to the require section of your `composer.json` file.


```php

$ php yii migrate/up --migrationPath=@vendor/reshik84/yii2-eav-behavior/migrations

```


Usage

-----



Once the extension is installed, add to your model  :



```php

    public function behaviors()
    {
        return [
            'eav' => [
                'class' => resh\eav\behaviors\EavBehavior::className(),
                'model_id' => 'id' // primary key
            ]
        ];
    }
    
    // list of EAV attributes
    public function additionalAttributes(){
        return ['attr1', 'attr2', 'attr3', ... ];
    }

    public function rules() {
        return [
            [['attr1', 'attr2', 'attr3'], 'safe']
        ];
    }
    
    public function attributeLabels()
    {
        return [
            'attr1' => 'Attribute 1',
            'attr2' => 'Attribute 2',
            'attr3' => 'Attribute 3',
        ];
    }
```

Call EAV attributes:

```php

$model = new Model();
$attr = $model->attr1; // get value
$model->attr1 = 'some value'; // set value
$model->save();

```