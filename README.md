# Django PostgreSQL on Docker

### 1.dockerイメージを作成
    $ docker-compose build

### 2.Djangoプロジェクトを作成
    $ docker-compose run --rm website django-admin startproject djangoproject .

以下が生成されます。
プロジェクトディレクトリ
    
    djangoproject/
    manage.py

### 3.DB設定
settings.py

    ALLOWED_HOSTS = ["*"]

    ...

	DATABASES = {
	    'default': {
	        'ENGINE': 'django.db.backends.postgresql',
	        'NAME': 'postgres',
	        'USER': 'postgres',
            'PASSWORD': 'postgres',
	        'HOST': 'database',
	        'PORT': 5432,
	    }
	}
	
### 4.マイグレーション

    docker-compose run --rm website python manage.py makemigrations
    docker-compose run --rm website python manage.py migrate

### 5.起動

    docker-compose up

http://localhost:8000/ にアクセスして以下の画像が表示されれば完了です。

![Django-PostgreSQL-on-Docker](https://user-images.githubusercontent.com/10918113/59118585-7c470780-898b-11e9-9ac2-084b237a3899.png)
