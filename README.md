Client-Side Python Exam IDE
A lightweight, zero-backend Python Integrated Development Environment (IDE) built specifically for secure academic testing and introductory programming courses.

Powered by Pyodide (Python compiled to WebAssembly), this IDE runs the CPython interpreter entirely inside the student's local browser tab. It requires no backend compute servers, no database configurations, and seamlessly integrates with high-security testing environments like Respondus LockDown Browser.

Key Features
Zero-Backend Execution
Client-Side Processing: Code compilation and execution happen entirely in the browser's RAM via WebAssembly. This eliminates server scaling issues during exams; 10 students or 1,000 students put the exact same zero load on your infrastructure.

Intranet Ready: Capable of running completely offline on a local network by self-hosting the Pyodide .wasm binaries, bypassing campus firewall or internet outage risks.

Resilient Workspace
Tabbed Editor: Students can open multiple independent scratchpads for testing logic before committing it to their main script.

Persistent Auto-Save: Keystrokes are aggressively saved to the browser's localStorage. If a computer crashes or a browser tab is accidentally refreshed during an exam, the student's entire workspace and tab structure is instantly recovered.

Factory Reset: A global panic button allows administrators or students to instantly wipe local storage and restore the environment to a clean state.

Advanced I/O Handling
Asynchronous Input Prompts: The standard Python input() function is overridden to trigger native browser prompts, bypassing WebAssembly's line-buffering limitations and echoing student responses directly into the console.

Virtual File System (VFS): Supports true file I/O operations (open('data.csv', 'r')). Students can upload datasets into the browser's RAM, write Python scripts to parse them, and download the generated output files back to their physical machines.

Dynamic Data Science Support
Auto-Package Loading: The IDE scans student code prior to execution. If it detects libraries like numpy or pandas, it automatically fetches and loads the required WebAssembly wheels on the fly, keeping the initial page load lightning fast while supporting advanced engineering and data science calculations.

Accessible & Focused UX
Distraction-Free Interface: A clean, CSS-grid layout matching standard university lab portals.

Accessibility Controls: Instant Dark Mode toggling and A-/A+ font scaling to reduce eye strain during timed assessments.

One-Click Clipboard Backup: Output logs and code can be instantly copied to the clipboard for easy pasting into LMS text boxes (like Blackboard or Canvas essay questions).

Architecture
This project is delivered as a highly portable, monolithic HTML file containing the necessary HTML, CSS, and JavaScript.

Frontend: Vanilla HTML5/CSS3. Zero external design frameworks (like Bootstrap or Tailwind) to ensure maximum compatibility and minimum payload size.

Editor Engine: Standard <textarea> elements mapped with custom JavaScript event listeners for precise Tab-key indentation and clipboard interception.

Execution Engine: Pyodide (v0.24.1) fetching the Python 3.11 environment.

Deployment
Because it contains no backend routing, deployment consists solely of serving the static files. It can be hosted on a basic Apache/Nginx intranet server, PythonAnywhere, GitHub Pages, or Cloudflare Pages.
