### Confirmation Dialog
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SweetAlert2 Example</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<body>
    <button id="confirm-dialog">Show Confirmation Dialog</button>
    <script>
        document.getElementById('confirm-dialog').addEventListener('click', () => {
            Swal.fire({
                title: 'Are you sure?',
                text: "You won't be able to revert this!",
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#3085d6',
                cancelButtonColor: '#d33',
                confirmButtonText: 'Yes, delete it!'
            }).then((result) => {
                if (result.isConfirmed) {
                    Swal.fire(
                        'Deleted!',
                        'Your file has been deleted.',
                        'success'
                    );
                }
            });
        });
    </script>
</body>
</html>
```

### Input Field
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SweetAlert2 Example</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<body>
    <button id="input-field">Show Alert with Input Field</button>
    <script>
        document.getElementById('input-field').addEventListener('click', () => {
            Swal.fire({
                title: 'Enter your name',
                input: 'text',
                inputPlaceholder: 'Enter your name',
                showCancelButton: true,
                inputValidator: (value) => {
                    if (!value) {
                        return 'You need to write something!';
                    }
                }
            }).then((result) => {
                if (result.isConfirmed) {
                    Swal.fire(`Hello, ${result.value}!`);
                }
            });
        });
    </script>
</body>
</html>
```

### Timer Alert
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SweetAlert2 Example</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<body>
    <button id="timer-alert">Show Timer Alert</button>
    <script>
        document.getElementById('timer-alert').addEventListener('click', () => {
            Swal.fire({
                title: 'Auto close alert!',
                text: 'I will close in 2 seconds.',
                timer: 2000,
                timerProgressBar: true,
                didOpen: () => {
                    Swal.showLoading();
                },
                willClose: () => {
                    clearInterval(timerInterval);
                }
            });
        });
    </script>
</body>
</html>
```

### Chained Modals
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SweetAlert2 Example</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<body>
    <button id="chained-modals">Show Chained Modals</button>
    <script>
        document.getElementById('chained-modals').addEventListener('click', () => {
            Swal.fire({
                title: 'Step 1',
                input: 'text',
                inputPlaceholder: 'Enter your step 1'
            }).then((result) => {
                if (result.isConfirmed) {
                    Swal.fire({
                        title: 'Step 2',
                        input: 'text',
                        inputPlaceholder: 'Enter your step 2'
                    });
                }
            });
        });
    </script>
</body>
</html>
```

### Loading Indicator
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SweetAlert2 Example</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<body>
    <button id="loading-indicator">Show Loading Indicator</button>
    <script>
        document.getElementById('loading-indicator').addEventListener('click', () => {
            Swal.fire({
                title: 'Loading...',
                timer: 2000,
                didOpen: () => {
                    Swal.showLoading();
                }
            }).then((result) => {
                if (result.dismiss === Swal.DismissReason.timer) {
                    Swal.fire('Done!');
                }
            });
        });
    </script>
</body>
</html>
```

### Custom Image
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SweetAlert2 Example</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<body>
    <button id="custom-image">Show Alert with Custom Image</button>
    <script>
        document.getElementById('custom-image').addEventListener('click', () => {
            Swal.fire({
                title: 'Sweet!',
                text: 'Modal with a custom image.',
                imageUrl: 'https://via.placeholder.com/150',
                imageWidth: 150,
                imageHeight: 150,
                imageAlt: 'Custom image'
            });
        });
    </script>
</body>
</html>
```
