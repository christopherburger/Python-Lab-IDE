# Client-Side Python Lab IDE

A lightweight, zero-backend Python Integrated Development Environment built specifically for introductory programming courses in a restricted academic intranet environment.

Powered by Pyodide (Python compiled to WebAssembly), this IDE runs the CPython interpreter entirely inside the student's local browser tab. It requires no backend compute servers, no database configurations, and was built to play nicely with testing environments like Respondus LockDown Browser.

## Major Features

### Zero-Backend Execution

Client-Side Processing: Code compilation and execution happen entirely in the browser's RAM via WebAssembly.

Intranet Ready: Capable of running completely offline on a local network by self-hosting the Pyodide .wasm binaries, bypassing campus firewall or internet outage risks.

The current version has self-hosting enabled. You can default to loading pyodide from the cdn by adjusting *script src* and commenting out *indexURL: "./pyodide/"* in the *loadPyodideEnvironment * function. The current configuration has you extract the contents of pyodide-0.24.1.tar.bz2 (found at the official source https://github.com/pyodide/pyodide/releases/tag/0.24.1) to the *pyodide* folder which is stored at the same leve as the index.html file.

### Workspace and Editor

Tabbed Editor: Students can open multiple independent code windows for testing logic before committing it to their main script.

Persistent Auto-Save: Keystrokes are continuously saved to the browser's localStorage. If a computer crashes or a browser tab is accidentally refreshed, the student's entire workspace and tab structure should be instantly recovered.

Asynchronous Input Prompts: The standard Python input() function is overridden to trigger native browser prompts and echoes student responses directly into the console.

Virtual File System (VFS): Supports true file I/O operations (open('data.csv', 'r')). Students can upload datasets into the browser's RAM, write Python scripts to parse them, and download the generated output files back to their physical machines. A version of Tableau's Sample Superstore dataset is preconfigured to be loaded automatically.

Auto-Package Loading: The IDE scans student code prior to execution. If it detects libraries like numpy or pandas, it automatically fetches and loads the required WebAssembly wheels on the fly, keeping the initial page load fast.


## Architecture

This project is delivered as a monolithic HTML file containing the necessary HTML, CSS, and JavaScript.

#### Frontend: Vanilla HTML5/CSS3. Zero external design frameworks.

#### Editor Engine: Standard <textarea> elements mapped with custom JavaScript event listeners.

#### Execution Engine: Pyodide (v0.24.1) fetching the Python 3.11 environment.

## Deployment

Because it contains no backend routing, deployment consists solely of serving the static files. It can be hosted on a basic Apache/Nginx intranet server, PythonAnywhere, GitHub Pages, or Cloudflare Pages.
