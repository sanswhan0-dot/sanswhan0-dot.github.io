<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>เกมสุ่มหาตัวอักษรไทย</title>

  <link rel="stylesheet" href="https://pyscript.net/latest/pyscript.css">
  <script defer src="https://pyscript.net/latest/pyscript.js"></script>

  <style>
    body {
      background:#111;
      color:white;
      text-align:center;
      font-family:sans-serif;
    }
    #target { font-size:80px; color:yellow; }
    button { font-size:30px; padding:10px 30px; }
  </style>
</head>

<body>
  <h1>เกมสุ่มหาตัวอักษรไทย</h1>
  <div id="target">ก</div>
  <p id="result">กดปุ่มสุ่ม</p>
  <p id="count">0 / 10</p>

  <button onclick="pyscript.runPython('roll()')">สุ่ม</button>

  <py-script>
import random
from pyscript import Element

letters = list("กขฃคฅฆงจฉชซฌญฎฏฐฑฒณดตถทธนบปผฝพฟภมยรลวศษสหฬอฮ")
level = 0
count = 0

def roll():
    global count, level
    letter = random.choice(letters)
    count += 1
    Element("result").write(f"สุ่มได้: {letter}")
    Element("count").write(f"{count} / 10")
    if letter == letters[level]:
        level += 1
        count = 0
        Element("target").write(letters[level])
        Element("result").write("ผ่านด่าน!")
        Element("count").write("0 / 10")
  </py-script>
</body>
</html>
