<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Typing Animation</title>

<style>
body {
    font-family: Arial, sans-serif;
    background-color: #111;
    color: #00ff9c;
    padding: 40px;
}

.typing {
    width: 0;
    overflow: hidden;
    border-right: 3px solid #00ff9c;
    white-space: nowrap;
    animation: typing 12s steps(120, end) forwards, blink 0.8s infinite;
}

@keyframes typing {
    from { width: 0 }
    to { width: 100% }
}

@keyframes blink {
    50% { border-color: transparent }
}
</style>
</head>

<body>

<h2>Cloud Computing</h2>

<p class="typing">
Cloud computing is the delivery of computing services (such as servers, storage, databases, networking, and software) over the internet instead of using your own physical computer or local servers. Instead of buying and maintaining hardware yourself, you use resources provided by cloud providers like Amazon Web Services, Microsoft through Microsoft Azure, or Google through Google Cloud Platform.
</p>

</body>
</html>



