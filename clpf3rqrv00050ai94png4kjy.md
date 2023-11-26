---
title: "🚀 Fastest way to build transparent login page HTML/CSS"
datePublished: Sun Nov 26 2023 06:32:10 GMT+0000 (Coordinated Universal Time)
cuid: clpf3rqrv00050ai94png4kjy
slug: fastest-way-to-build-transparent-login-page-htmlcss
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700980327799/eb7b3744-368d-4272-ab1d-a176416b8768.jpeg

---

## Live video example
%[https://www.youtube.com/watch?v=96O1oTxe5i4]


## Introduction
Creating a transparent login page involves combining HTML, CSS to achieve the desired effect. Below is a simple example using HTML and CSS to create a transparent login page. Keep in mind that this example assumes a basic understanding of web development.
**HTML**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Transparent login page</title>
    <style type="text/css">
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500&family=Open+Sans:wght@300;500;600&display=swap');
        *, *::after, *::before{
            box-sizing: border-box;
        }
        body {
            margin: 0;
            background: linear-gradient(90deg, #0D0D0D 0%, #8A8887 100%);
            font-family: 'Montserrat', sans-serif;
            font-family: 'Open Sans', sans-serif;
        }
        main {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            gap: 2rem;
            max-width: 1200px;
            margin: auto;
        }
        main::before {
            content: "";
            background: url("./assets/bg-transparent.png");
            position: absolute;
            top: 0;
            bottom: 0;
            left: 0;
            background-size: contain;
            width: 100%;
            height: 100%;
            background-repeat: no-repeat;
            z-index: -1;
        }
        form {
            background: rgba(99, 95, 95, 0.16);
            backdrop-filter: blur(15px);
            padding: 5rem 4rem;
            border-radius: 1rem;
            min-width: 380px;
            filter: drop-shadow(0px 4px 70px rgba(0, 0, 0, 0.10));
        }
        label {
            font-size: 0.9rem;
            color: #d4d2d2;
            margin-bottom: 5px;
            display: block;
            font-weight: 300;
        }
        h1 {
            color: white;
        }
        input {
            width: 100%;
            padding: 0.9rem;
            border-radius: 0.4rem;
            border: none;
            outline: none;
            font-weight: 300;
            font-size: 0.9rem;
            color: #333;
            background-color: white;
        }
        .form-group {
            margin-bottom: 1.4rem;
        }
        button {
            width: 100%;
            padding: 1rem;
            border-radius: 0.4rem;
            background-color: rgba(233, 101, 47, 0.7);
            border: none;
            display: block;
            font-size: 1rem;
            font-weight: 600;
            margin: 0;
            color: white;
            cursor: pointer;
            transition: ease 0.2s;
        }

        button:hover {
            background-color: rgba(233, 101, 47, 1);
        }

        .info-content {
            text-align: center;
            color: #dddddd;
            font-size: 0.8rem;
            font-weight: 300;
        }
        .banner {
            width: 100%;
            height: auto;
        }
        .link {
            font-size: 0.9rem;
            font-weight: 400;
            margin-left: 5px;
            cursor: pointer;
        }
        .link:hover {
            color: white;
        }
        .social-icons {
            display: flex;
            align-items: center;
            justify-content: space-evenly;
            margin: 1.5rem 0;
            gap: 2rem;
        }

        .social-icons a {
            height: auto;
            padding: 0.5rem 2rem;
            background-color: white;
            border-radius: 3rem;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }
        .social-icons a:hover {
            background-color: #DDD;
        }
        .social-icons > a > img {
            width: 24px;
            height: auto;
        }

        .forgot-link {
            font-size: 0.7rem;
            font-weight: 300;
            margin-top: 0.3rem;
            color: #DDD;
            cursor: pointer;
        }
        .forgot-link:hover {
            color: white;
        }

        .flex-50 {
            flex: 50%;
        }
        
        ::placeholder {
            color: #d1cfcf;
            font-weight: 300;
            font-size: 0.9rem;
        }

    </style>
</head>
<body>
    <main>
        <div class="flex-50">
            <form>
                <h1>Sign In</h1>
                <div class="form-group">
                    <label>Email address</label>
                    <div>
                        <input type="text" placeholder="Email address"/>
                    </div>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <div>
                        <input type="text" placeholder="Password"/>
                    </div>
                    <a class="forgot-link">Forgot Password?</a>
                </div>
                <div>
                    <button type="submit">Sign In</button>
                </div>
                <div>
                    <p class="info-content">or continue with</p>
                </div>
                <div class="social-icons">
                    <a><img src="./assets/google.svg"/></a>
                    <a><img src="./assets/github.svg"/></a>
                    <a><img src="./assets/facebook.svg"/></a>
                </div>
                <div>
                    <p class="info-content">Don’t have an account yet?<a class="link">Register account</a></p>
                </div>
            </form>
        </div>
        <div>
            <img src="./assets/bg-img.png" class="banner" width="400px"/>
        </div>
    </main>
</body>
</html>
```

Thanks for reaching the bottom of our blog post! If you've enjoyed our content, take the next step: [subscribe to our YouTube channel](https://www.youtube.com/@simpledevcode?sub_confirmation=1) for exclusive perks.


