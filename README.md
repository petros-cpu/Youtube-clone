# youtube_clone.py

"""
MIT License

Copyright (c) 2025 NRS

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
"""

import os
from flask import Flask, Response
from threading import Thread
import time

app = Flask(__name__)

HTML_CONTENT = """
<!DOCTYPE html>
<html>
<head>
  <title>NRS YouTube Clone</title>
  <style>
    body { font-family: sans-serif; background: #111; color: white; text-align: center; }
    video { width: 90%; max-width: 600px; margin-top: 20px; }
  </style>
</head>
<body>
  <h1>NRS YouTube Clone</h1>
  <video controls>
    <source src="/video" type="video/mp4">
    Your browser does not support HTML5 video.
  </video>
</body>
</html>
"""

VIDEO_URL = "https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_1mb.mp4"

@app.route('/')
def index():
    return HTML_CONTENT

@app.route('/video')
def video():
    import requests
    r = requests.get(VIDEO_URL, stream=True)
    return Response(r.iter_content(chunk_size=1024), content_type=r.headers['Content-Type'])

def run_flask():
    app.run(host="127.0.0.1", port=8000)

def create_launcher_html():
    with open("youtube_viewer.html", "w") as f:
        f.write("""
        <html>
          <head><meta charset="UTF-8"><title>Viewer</title></head>
          <body>
            <script>window.location.href = "http://127.0.0.1:8000";</script>
          </body>
        </html>
        """)

if __name__ == "__main__":
    print("🟢 Starting YouTube clone server at http://127.0.0.1:8000")
    Thread(target=run_flask).start()
    time.sleep(2)
    create_launcher_html()
    print("🌐 Opening viewer...")
    os.system("termux-open 
    MIT License
# NRS YouTube Clone

A simple YouTube-like video app using Python and Flask, ready for mobile preview or wrapping in a WebView Android app.

## Features
- Local Flask video stream
- Web-based video player
- Android browser/WebView launch
- MIT Licensed

## Run It in Termux

```bash
pkg install python
pip install flask requests
---

## ✅ How to Upload to GitHub

```bash
git init
git remote add origin https://github.com/yourusername/youtube-clone.git
git add .
git commit -m "Initial commit - YouTube clone Flask app"
git push -u origin master9 youtube_clone.py
---

## ✅ How to Upload to GitHub

```bash
git init
git remote add origin https://github.com/yourusername/youtube-clone.git
git add .
git commit -m "Initial commit - YouTube clone Flask app"
git push -u origin master
