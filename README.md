# flask-webpack-loader


flask version [django-webpack-loader](https://github.com/owais/django-webpack-loader)


## Install

```bash
npm install --save-dev webpack-bundle-tracker

pip install flask-webpack-loader
```

## Usage
app.py
```python
from flask_webpack_loader import WebpackLoader

WEBPACK_LOADER = {
    'BUNDLE_DIR_NAME': os.path.join('static', 'bundles'),
    'STATIC_URL': 'static',
    'STATS_FILE': 'webpack-stats.prod.json',
    'POLL_INTERVAL': 0.1,
    'TIMEOUT': None,
    'IGNORES': [re.compile(r'.+\.hot-update.js'), re.compile(r'.+\.map')]
}

app.config['WEBPACK_LOADER'] = WEBPACK_LOADER
webpack_loader = WebpackLoader(app)
```

template.html
```html
    {{ render_bundle('main') | safe }}
    
    # webpack 4+
    {{ render_bundle('runtime~main') | safe }}
    {{ render_bundle('undefined') | safe }}
```
