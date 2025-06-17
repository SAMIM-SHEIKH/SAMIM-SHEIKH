# Re-create the HTML, CSS, JS website folder structure after code execution state reset

from zipfile import ZipFile
import os

# Set up the directory structure
base_dir = "/mnt/data/my-site"
os.makedirs(base_dir, exist_ok=True)

# HTML content
html_content = """<!DOCTYPE html>
<html>
<head>
  <title>আমার সাইট</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>স্বাগতম!</h1>
  <p id="text">এটি একটি ডেমো ওয়েবসাইট।</p>
  <button onclick="changeText()">লেখা বদলাও</button>
  <script src="script.js"></script>
</body>
</html>"""

# CSS content
css_content = """body {
  font-family: Arial;
  text-align: center;
  background-color: #f9f9f9;
}
h1 {
  color: green;
}"""

# JS content
js_content = """function changeText() {
  document.getElementById("text").innerText = "তুমি বাটনে ক্লিক করেছো!";
}"""

# File paths
html_path = os.path.join(base_dir, "index.html")
css_path = os.path.join(base_dir, "style.css")
js_path = os.path.join(base_dir, "script.js")

# Write the files
with open(html_path, "w", encoding="utf-8") as f:
    f.write(html_content)
with open(css_path, "w", encoding="utf-8") as f:
    f.write(css_content)
with open(js_path, "w", encoding="utf-8") as f:
    f.write(js_content)

# Create the zip file
zip_path = "/mnt/data/my-site.zip"
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(html_path, arcname="index.html")
    zipf.write(css_path, arcname="style.css")
    zipf.write(js_path, arcname="script.js")

zip_path

