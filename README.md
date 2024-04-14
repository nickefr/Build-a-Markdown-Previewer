# Build-a-Markdown-Previewer

User Story #1: I can see a textarea element with a corresponding id="editor".

User Story #2: I can see an element with a corresponding id="preview".

User Story #3: When I enter text into the #editor element, the #preview element is updated as I type to display the content of the textarea.

User Story #4: When I enter GitHub flavored markdown into the #editor element, the text is rendered as HTML in the #preview element as I type (HINT: You don't need to parse Markdown yourself - you can import the Marked library for this: https://cdnjs.com/libraries/marked).

User Story #5: When my markdown previewer first loads, the default text in the #editor field should contain valid markdown that represents at least one of each of the following elements: a heading element (H1 size), a subheading element (H2 size), a link, inline code, a code block, a list item, a blockquote, an image, and bolded text.

User Story #6: When my markdown previewer first loads, the default markdown in the #editor field should be rendered as HTML in the #preview element.

Optional Bonus (you do not need to make this test pass): My markdown previewer interprets carriage returns and renders them as br (line break) elements.



```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Markdown Previewer</title>
  <!-- Bootstrap CSS -->
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <!-- Custom CSS -->
  <style>
    #editor {
      height: 300px;
    }

    #preview {
      height: 300px;
      overflow-y: auto;
    }
  </style>
</head>
<body>
  <div class="container mt-5">
    <!-- User Story #1: Textarea element for editing markdown -->
    <label for="editor">Editor</label>
    <textarea id="editor" class="form-control"></textarea>
    <!-- User Story #2: Element for previewing markdown -->
    <label for="preview" class="mt-3">Preview</label>
    <div id="preview" class="border p-3"></div>
  </div>

  <!-- React, ReactDOM, Marked -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/react/17.0.2/umd/react.production.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/17.0.2/umd/react-dom.production.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/marked/2.0.3/marked.min.js"></script>
  <!-- Main JS bundle -->
  <script>
    // JavaScript for rendering markdown
    document.getElementById('editor').addEventListener('input', function() {
      const markdown = this.value;
      document.getElementById('preview').innerHTML = marked(markdown);
    });

    // User Story #5: Default markdown content
    const defaultMarkdown = `
      # Heading 1
      ## Heading 2
      [Link](https://www.example.com)
      \`Inline code\`
      \`\`\`
      // Code block
      const example = 'Markdown';
      console.log(example);
      \`\`\`
      - List item 1
      - List item 2
      > Blockquote
      ![Image](https://via.placeholder.com/150)
      **Bold text**
    `;
    document.getElementById('editor').value = defaultMarkdown;

    // User Story #6: Render default markdown content on initial load
    document.getElementById('preview').innerHTML = marked(defaultMarkdown);
  </script>
</body>
</html>
```
