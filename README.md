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