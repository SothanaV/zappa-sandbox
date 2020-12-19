# zappa-sandbox

## create creadential
```python
    mkdir ~/aws
    cd aws
```
createfile >> credentials
```
# ~/aws/credentials

[default]
aws_access_key_id = <your access_key>
aws_secret_access_key = <your secret_access_key>
```

## create env 
```python
    virtualenv env
    source env/bin/activate
```
## install backend
```python
    pip install django
    # or
    pip install flask
```

## install zappa
```python
    pip install zappa
```

create superuser
```
zappa manage dev create_admin_user admin admin@defellow.com qwer1234
```

migrate db
```
# 1
python manage.py makemigrations

#2
zappa update dev

#3
zappa manage dev migrate

```

## install and settings
install
```
pip install django-s3-sqlite django-s3-storag
```

settings.py
```
INSTALLED_APPS = [
    ...

    'django_s3_sqlite',
    'django_s3_storage',

    ...
]

DATABASES = {
    "default": {
        "ENGINE": "django_s3_sqlite",
        "NAME": "sqlite.db",
        "BUCKET": "<BUCKET_NAME>",
    }
}

YOUR_S3_BUCKET = "<BUCKET_NAME>"

STATICFILES_STORAGE = "django_s3_storage.storage.StaticS3Storage"
AWS_S3_BUCKET_NAME_STATIC = YOUR_S3_BUCKET

# These next two lines will serve the static files directly 
# from the s3 bucket
AWS_S3_CUSTOM_DOMAIN = '%s.s3.amazonaws.com' % YOUR_S3_BUCKET
STATIC_URL = "https://%s/" % AWS_S3_CUSTOM_DOMAIN

```

# Frontend
install
```
brew install awscli
```
package.json
```js
"scripts": {
    ...
    "deploy":"aws s3 sync build/ s3://<BUCKET_NAME> --acl public-read"
    ...
  },
```

deploy 
```
    yarn build && yarn deploy  
```