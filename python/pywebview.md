### 1. `create_window()`
```python
import webview

# Simple window
webview.create_window('Simple Window', 'https://www.example.com')

# Window with additional parameters
webview.create_window(
    title='Advanced Window',
    url='https://www.example.com',
    width=800,
    height=600,
    resizable=True,
    fullscreen=False,
    min_size=(200, 100),
    confirm_close=True
)

# Run the webview
webview.start()
```

### 2. `start()`
```python
import webview

def on_loaded():
    print("Webview has loaded!")

webview.create_window('Simple Window', 'https://www.example.com')
webview.start(on_loaded)
```

### 3. `destroy_window()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def close_window():
    webview.destroy_window(window)

webview.start(close_window)
```

### 4. `toggle_fullscreen()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def toggle_fullscreen():
    webview.toggle_fullscreen(window)

webview.start(toggle_fullscreen)
```

### 5. `get_current_url()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def get_url():
    url = webview.get_current_url(window)
    print("Current URL:", url)

webview.start(get_url)
```

### 6. `load_url()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def load_new_url():
    webview.load_url(window, 'https://www.another-example.com')

webview.start(load_new_url)
```

### 7. `load_html()`
```python
import webview

window = webview.create_window('Simple Window', '')

def load_html_content():
    html_content = "<h1>Hello, World!</h1>"
    webview.load_html(window, html_content)

webview.start(load_html_content)
```

### 8. `evaluate_js()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def run_js():
    result = webview.evaluate_js(window, 'document.title')
    print("Page title is:", result)

webview.start(run_js)
```

### 9. `set_title()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def change_title():
    webview.set_title(window, 'New Title')

webview.start(change_title)
```

### 10. `resize()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def resize_window():
    webview.resize(window, 1024, 768)

webview.start(resize_window)
```

### 11. `move()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def move_window():
    webview.move(window, 100, 100)

webview.start(move_window)
```

### 12. `minimize()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def minimize_window():
    webview.minimize(window)

webview.start(minimize_window)
```

### 13. `restore()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def restore_window():
    webview.restore(window)

webview.start(restore_window)
```

### 14. `hide()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def hide_window():
    webview.hide(window)

webview.start(hide_window)
```

### 15. `show()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def show_window():
    webview.show(window)

webview.start(show_window)
```

### 16. `get_current_window()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def get_window():
    current_window = webview.get_current_window()
    print("Current window:", current_window)

webview.start(get_window)
```

### 17. `get_active_window()`
```python
import webview

window = webview.create_window('Simple Window', 'https://www.example.com')

def get_active_window():
    active_window = webview.get_active_window()
    print("Active window:", active_window)

webview.start(get_active_window)
```

### 18. `create_file_dialog()`
```python
import webview

def open_file_dialog():
    result = webview.create_file_dialog(webview.OPEN_DIALOG)
    print("Selected file:", result)

webview.create_window('File Dialog', 'https://www.example.com')
webview.start(open_file_dialog)
```

### 19. `create_folder_dialog()`
```python
import webview

def open_folder_dialog():
    result = webview.create_folder_dialog('Select a folder')
    print("Selected folder:", result)

webview.create_window('Folder Dialog', 'https://www.example.com')
webview.start(open_folder_dialog)
```

### 20. `create_save_dialog()`
```python
import webview

def save_file_dialog():
    result = webview.create_save_dialog('Save file', save_filename='example.txt')
    print("Save file to:", result)

webview.create_window('Save Dialog', 'https://www.example.com')
webview.start(save_file_dialog)
```
