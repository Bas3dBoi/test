# Bugs and Issues in Application

## Issues

```console
============================================== warnings summary ============================================== 
..\..\..\..\.virtualenvs\weather_project_folder-89nt3U5t\Lib\site-packages\flask_caching\__init__.py:145       
  C:\Users\Marcos\.virtualenvs\weather_project_folder-89nt3U5t\Lib\site-packages\flask_caching\__init__.py:145: DeprecationWarning: Using the initialization functions in flask_caching.backend is deprecated.  Use the a full path to backend classes directly.
    self._set_cache(app, config)

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
======================================== 2 passed, 1 warning in 0.83s ======================================== 
```

## In extensions.py File

```python
cache = Cache()
```

- ### Change To

 ```python
cache = Cache(config={'CACHE_TYPE': 'flask_caching.backends.simplecache.SimpleCache'})
```

## In app.py File

```python
app.config['CACHE_TYPE'] = 'simple'
cache.init_app(app) 
```

- ### Change To

 ```python
app.config['CACHE_TYPE'] = 'flask_caching.backends.simplecache.SimpleCache'
cache.init_app(app)
```
