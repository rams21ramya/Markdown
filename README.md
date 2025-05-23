# Markdown
import markdown
from google.colab import files
import os

uploaded = files.upload()

for filename in uploaded.keys():
    if filename.endswith('.md'):
        with open(filename, 'r', encoding='utf-8') as f:
            text = f.read()

        html = markdown.markdown(text)
        output_file = os.path.splitext(filename)[0] + '.html'

        with open(output_file, 'w', encoding='utf-8') as f:
            f.write(html)

        print(f"✅ HTML file created: {output_file}")


        files.download(output_file)
    else:
        print(f"⚠️ Skipped non-Markdown file: {filename}")