<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Python IDE for Beginners</title>

  <!-- CodeMirror Styles -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.14/codemirror.min.css" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.14/theme/dracula.min.css" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.14/theme/eclipse.min.css" />

  <style>
    body {
      margin: 0;
      background: #1e1e2f;
      color: #f8f8f2;
      font-family: monospace;
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background: #282a36;
      color: #bd93f9;
      padding: 12px 20px;
      font-weight: bold;
      font-size: 24px;
    }

    #buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      padding: 10px;
      background: #222831;
      align-items: center;
    }

    #buttons button, #snippetMenu {
      background-color: #44475a;
      color: #f8f8f2;
      border: none;
      padding: 8px 12px;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
      font-size: 16px;
    }

    #buttons button:hover, #snippetMenu:hover {
      background-color: #6272a4;
    }

    #editor {
      flex-grow: 1;
      height: 100%;
    }

    .CodeMirror {
      height: 100%;
      font-size: 14px;
    }

    #run-btn {
      background-color: #bd93f9;
      color: #000;
      border: none;
      padding: 10px 22px;
      margin: 10px auto;
      font-weight: bold;
      border-radius: 6px;
      cursor: pointer;
      width: 120px;
    }

    #output {
      background: #121212;
      color: #50fa7b;
      font-family: monospace;
      padding: 10px;
      height: 150px;
      overflow-y: auto;
      white-space: pre-wrap;
    }

    #main-container {
      display: flex;
      flex-direction: column;
      height: 100%;
    }

    #editor-container {
      flex-grow: 1;
      display: flex;
      flex-direction: column;
    }

    #font-controls {
      margin-left: auto;
      display: flex;
      gap: 4px;
    }

    #execution-time {
      color: #f1fa8c;
      font-size: 14px;
      padding: 5px 10px;
    }
  </style>
</head>
<body>
  <header>Python IDE for Beginners</header>

  <div id="buttons">
    <button title="Refresh" onclick="location.reload()">🔄</button>
    <button title="Save" onclick="saveCode()">💾</button>
    <button title="Upload" onclick="uploadCode()">📂</button>
    <button title="Copy" onclick="copyCode()">📋</button>
    <button title="Erase" onclick="eraseCode()">🧹</button>
    <button title="Undo" onclick="undo()">↩️</button>
    <button title="Redo" onclick="redo()">↪️</button>
    <button title="Toggle Theme" onclick="toggleTheme()">🌗</button>
    <button title="Clear Output" onclick="clearOutput()">🧽</button>
    <select id="snippetMenu" onchange="insertSnippet(this.value)">
      <option value="">➕ Snippets</option>
      <option value="print('Hello, World!')">Hello World</option>
      <option value="for i in range(5):\n  print(i)">For Loop</option>
      <option value="name = input('Enter your name: ')\nprint(f'Hello {name}')">Input</option>
    </select>
    <div id="font-controls">
      <button onclick="adjustFontSize(1)">A+</button>
      <button onclick="adjustFontSize(-1)">A-</button>
    </div>
  </div>

  <div id="main-container">
    <div id="editor-container">
      <div id="editor"></div>
    </div>
    <button id="run-btn">Run Code</button>
    <div id="execution-time"></div>
    <div id="output"></div>
  </div>

  <!-- CodeMirror + Pyodide -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.14/codemirror.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.14/mode/python/python.min.js"></script>
  <script src="https://cdn.jsdelivr.net/pyodide/v0.23.4/full/pyodide.js"></script>

  <script>
    let editor, pyodide, isReady = false, isDark = true;
    const outputEl = document.getElementById('output');
    const editorEl = document.getElementById('editor');
    const execTimeEl = document.getElementById('execution-time');
    let fontSize = 14;

    const defaultCode = `def sum(a, b):\n    return (a + b)\n\na = int(input('Enter 1st number: '))\nb = int(input('Enter 2nd number: '))\n\nprint(f'Sum of {a} and {b} is {sum(a, b)}')`;

    function initializeEditor() {
      editor = CodeMirror(editorEl, {
        value: localStorage.getItem("autosave_code") || defaultCode,
        mode: 'python',
        theme: localStorage.getItem("theme") || 'dracula',
        lineNumbers: true,
        undoDepth: 200
      });

      isDark = editor.getOption("theme") === "dracula";

      setInterval(() => {
        localStorage.setItem("autosave_code", editor.getValue());
      }, 5000);
    }

    async function loadPyodideAndPackages() {
      outputEl.textContent = 'Loading Python runtime... Please wait.';
      pyodide = await loadPyodide();
      pyodide.globals.set("input", (msg) => prompt(msg));
      isReady = true;
      outputEl.textContent = '✅ Python runtime loaded. Ready to run!';
    }

    document.getElementById('run-btn').onclick = async () => {
      if (!isReady) {
        outputEl.textContent = '⚙️ Python is still loading...';
        return;
      }

      const code = editor.getValue();
      outputEl.textContent = '';
      execTimeEl.textContent = '';
      const start = performance.now();
      try {
        pyodide.setStdout({ batched: (data) => {
          outputEl.innerHTML += `<span style="color:#50fa7b">${data}</span>`;
          outputEl.scrollTop = outputEl.scrollHeight;
        }});
        pyodide.setStderr({ batched: (data) => {
          outputEl.innerHTML += `<span style="color:#ff5555">${data}</span>`;
          outputEl.scrollTop = outputEl.scrollHeight;
        }});

        await pyodide.runPythonAsync(code);
        const end = performance.now();
        execTimeEl.textContent = `⏱️ Execution Time: ${(end - start).toFixed(2)} ms`;
      } catch (err) {
        outputEl.innerHTML += `<span style="color:#ff5555">❌ Error:\n${err.message}</span>`;
      }
    };

    function saveCode() {
      const blob = new Blob([editor.getValue()], { type: 'text/plain' });
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = 'code.py';
      a.click();
    }

    function uploadCode() {
      const input = document.createElement('input');
      input.type = 'file';
      input.accept = '.py';
      input.onchange = e => {
        const reader = new FileReader();
        reader.onload = () => editor.setValue(reader.result);
        reader.readAsText(e.target.files[0]);
      };
      input.click();
    }

    function copyCode() {
      navigator.clipboard.writeText(editor.getValue())
        .then(() => alert("Code copied to clipboard!"))
        .catch(() => alert("Copy failed."));
    }

    function eraseCode() {
      editor.setValue('');
    }

    function undo() {
      editor.undo();
    }

    function redo() {
      editor.redo();
    }

    function toggleTheme() {
      isDark = !isDark;
      const theme = isDark ? 'dracula' : 'eclipse';
      editor.setOption('theme', theme);
      localStorage.setItem("theme", theme);
    }

    function insertSnippet(value) {
      if (value) {
        editor.replaceSelection(value + "\n");
        document.getElementById("snippetMenu").selectedIndex = 0;
      }
    }

    function clearOutput() {
      outputEl.textContent = '';
      execTimeEl.textContent = '';
    }

    function adjustFontSize(change) {
      fontSize = Math.min(30, Math.max(10, fontSize + change));
      document.querySelector('.CodeMirror').style.fontSize = `${fontSize}px`;
    }

    initializeEditor();
    loadPyodideAndPackages();
  </script>
</body>
</html>
