# World.js
A new javascript framework. No deps. Pure js, no typescript required.

## IMPORTANT!
Suspense does not work... Except if used with the 'progressive' attribute.

## What does code in World.js look like?
```
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>World.js demo</title>
    <style>
        html, body {
            height: 100%;
            margin: 0;
        }

        body {
            display: flex;
            flex-direction: column;
        }

        .content {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        .app {
            flex: 1;
        }

        footer {
            background-color: #f1f1f1;
            text-align: center;
            padding: 1rem;
        }

        nav {
            background-color: #f1f1f1;
            text-align: center;
            padding: 1rem;
        }

        a {
            font-size: large;
            font-family: Verdana, Geneva, Tahoma, sans-serif;
        }
    </style>
    <script src="../world-router.js"></script>
    <script src="../world-suspense.js" defer></script>
</head>
<body>
    <div class="content">
        <nav>
            <a href="/" class="nav-link">Home</a>
            <a href="/about" class="nav-link">About</a>
            <a href="/contact" class="nav-link">Contact</a>
            <a href="/download" class="nav-link">Get it now!</a>
        </nav>
        <!--
        <world-suspense waitingtext="Please wait..." delay="0" progressive>
            //<img src="res/large-image.png" alt="Large Image">
            <h1>
                Finished loading!
            </h1>
        </world-suspense>
        -->
        <div id="app"></div>
        <footer>&copy;2024 CodeurGeek</footer>
    </div>
    <script>
        // Usage
        const app = new WorldRouter();

        /*

        app.addRoute('/', () => {
            app.defer('HTML', () => {
                console.log('Home page HTML loaded');
                // Do something after HTML is loaded
            });
            app.defer('JS', () => {
                console.log('All scripts loaded');
                // Do something after all scripts are loaded
            });
            return '<h1>Welcome to World.js!</h1>';
        });

        */

        app.addRoutePage('/', 'pages/home.html')

        app.addRoute('/about', () => {
            app.defer('HTML', () => {
                console.log('About page HTML loaded');
                // Do something after HTML is loaded
            });
            return '<h1>About Page</h1>';
        });

        app.addRoute('/contact', () => '<h1>Contact Page</h1>');

        app.addRoutePage('/download', 'pages/downloads.html');

        app.addRoutePage('/learn-defering', 'pages/learning/defering-tutorial.html');

        app.navigate('/');
    </script>
</body>
</html>
```

## How do i learn World.js?
By cloning this repo, and opening tests/index.html.
