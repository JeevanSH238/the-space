THE SPACE + ORBIT — UPDATED PROJECT
===================================

WHAT IS INCLUDED
----------------
- index.html: THE SPACE homepage and existing resource platform. The old floating ORBIT Lite panel is removed so there is one consistent ORBIT destination.
- ORBIT.html: redesigned standalone ORBIT workspace, based on the supplied blue-navy visual reference and adapted for mobile. The welcome greeting is shown when ORBIT is opened from either Ask ORBIT entry link.
- orbit-client.js: browser client for chat, conversation context, voice input, low-pitch spoken greeting/replies with synchronized word highlighting, a rotating orb while speech is active, theme switching and error handling.
- backend/app/main.py: FastAPI service using the OpenAI Responses API. The API key stays on the server.
- requirements.txt / requirements-dev.txt: Python dependencies.

IMPORTANT DESIGN / REPOSITORY NOTES
-----------------------------------
The original THE SPACE repository ZIP contained index.html, ORBIT.html and README.md. Its homepage includes the existing academics, learning resources, projects, industry, opportunities, careers, events and feedback sections. Those sections and the existing homepage navigation are retained. The old embedded floating ORBIT Lite panel was removed because it duplicated the standalone assistant and caused two competing ORBIT experiences.

The previous updated ORBIT.html had a missing closing </style> tag. That caused the browser to parse the page incorrectly and could result in a blank navy screen. The new ORBIT.html has a corrected document structure and a complete responsive interface.

EXPECTED REPOSITORY LAYOUT
--------------------------
THE_SPACE/
  index.html
  ORBIT.html
  orbit-client.js
  requirements.txt
  requirements-dev.txt
  README-ORBIT-SETUP.txt
  backend/
    app/
      __init__.py
      main.py

RUNNING THE BACKEND
-------------------
Acode is useful for editing the HTML, CSS and JavaScript files. It does not run the Python API server by itself. Deploy/run the backend on a Python-capable host.

1. Install dependencies:
   pip install -r requirements.txt

2. Configure private server environment variables:
   OPENAI_API_KEY=your_private_api_key
   OPENAI_MODEL=the_model_available_to_your_API_account

   Never put the API key in index.html, ORBIT.html, orbit-client.js, GitHub commits, or screenshots.

3. From the repository root, run:
   uvicorn backend.app.main:app --host 0.0.0.0 --port 8000

4. Open the deployed server's homepage. The backend serves index.html, ORBIT.html and orbit-client.js, and provides POST /api/chat plus GET /health.

5. If deploying frontend and API on different origins, configure CORS_ORIGINS on the server with the exact frontend origin(s), comma-separated. Prefer serving the frontend and API from the same origin when possible.

TESTING CHECKLIST
-----------------
- Open / and confirm the THE SPACE homepage sections and navigation remain available.
- Open /ORBIT.html and confirm the ORBIT workspace loads.
- Confirm /orbit-client.js loads (not a 404).
- Confirm /health returns status ok.
- Send a test message and confirm POST /api/chat returns an answer.
- Test microphone input only in a browser/context that supports speech recognition and grants microphone permission.
- Open ORBIT using either Ask ORBIT link and check the spoken “Hello supreme, what are you looking for?” greeting. The homepage speaks from the original tap before navigating to ORBIT; on the ORBIT page, use “Hear ORBIT greeting” to replay it. Browser voice choices and pitch vary by device.
- Enable the speaker toggle and send a question to hear spoken answers. Use “Listen to this answer” to replay an individual response. Word highlighting and the orb animation follow speech events when supported by the browser.
- Test the layout at desktop and mobile widths.

LIMITATIONS
-----------
- Chat context is held in the current browser page session and is not durable memory.
- Voice features depend on browser support, installed system voices and user permission. The browser controls pitch/rate; a specific Hollywood-style villain voice cannot be guaranteed on every phone.
- The backend's in-memory rate limiter is a lightweight safeguard, not a production-wide shared limiter.
- Do not treat AI output as verified without checking appropriate sources.


ORBIT VISUAL UPDATE
- ORBIT.html contains the blue-violet luminous glass orb from the supplied reference and a matching deep navy/blue gradient workspace.
- orbit-client.js MUST remain beside ORBIT.html and index.html in the repository root. It is the browser client for /api/chat, voice input, and optional spoken replies.
- The visual animation is CSS/SVG-based; no external animation library is required.
