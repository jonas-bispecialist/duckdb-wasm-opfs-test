# DuckDB OPFS Persistence Test

A browser-based test application demonstrating persistent storage capabilities of DuckDB WebAssembly using Origin Private File System (OPFS).

<img width="478" alt="image" src="https://github.com/user-attachments/assets/675875c9-94ac-461d-970f-dc9dcf8ce9f7" />

## Overview

This test application showcases:
- **DuckDB WebAssembly** running entirely in the browser
- **OPFS persistence** for storing database files across browser sessions
- **Interactive UI** for testing database operations
- **No backend required** - everything runs client-side

## Features

- Initialize new OPFS-backed database
- Connect to existing persistent database
- Add rows to test table
- Display table contents
- Data persists across browser sessions

## Requirements

**Important**: This application **must** be served via a web server due to:
- ES module imports from CDN
- OPFS (Origin Private File System) requirements
- CORS restrictions on `file://` protocol

## Quick Start (Windows)

### Option 1: Using Node.js http-server (Recommended)

```powershell
# Install http-server globally
npm install -g http-server

# Navigate to the directory containing the HTML file
cd C:\Users\JonasHertz\Desktop

# Start the server
http-server -p 8080 -c-1

# Open browser and navigate to:
# http://localhost:8080/duckdb-wasm-opfs-test.html
```

### Option 2: Using Node.js live-server (Auto-reload)

```powershell
# Install live-server globally
npm install -g live-server

# Navigate to the directory
cd C:\Users\JonasHertz\Desktop

# Start with specific file
live-server --port=8080 --open=duckdb-wasm-opfs-test.html
```

### Option 3: Using Python (if Node.js not available)

```powershell
# Python 3
python -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080

# Then navigate to http://localhost:8080/duckdb-wasm-opfs-test.html
```

## Usage Instructions

1. **Start the web server** using one of the methods above
2. **Open the application** in a modern browser (Chrome, Edge, Firefox)
3. **Test the functionality**:
   - Click "Initialize New OPFS DB" to create a fresh database
   - Click "Add Rows to Table" to insert test data
   - Click "Print Test Table" to view current data
   - Refresh the page and click "Initialize from existing OPFS DB" to verify persistence

## Technical Details

### DuckDB Version
- Uses `@duckdb/duckdb-wasm@1.29.1-dev68.0` (development build with OPFS support)
- OPFS support is not available in stable 1.29 but implemented in dev builds

### OPFS Storage
- Database stored at `opfs://test.db`
- Data persists across browser sessions
- Storage is origin-specific and private

### Browser Compatibility
- **Chrome/Edge**: Full OPFS support
- **Firefox**: Limited OPFS support (experimental)
- **Safari**: No OPFS support

## Troubleshooting

### Common Issues

1. **"Module not found" errors**
   - Ensure you're serving via HTTP server, not opening as `file://`

2. **OPFS not working**
   - Use Chrome or Edge for best compatibility
   - Ensure site is served over HTTP/HTTPS

3. **Database connection errors**
   - Check browser console for detailed error messages
   - Try initializing a new database first

### Browser Developer Tools
- Open DevTools (F12) to view console logs
- Check Application > Storage > Origin Private File System to see stored files

## Files

- `duckdb-wasm-opfs-test.html` - Main test application
- `README.md` - This documentation file

## License

This is a test/demo application. DuckDB is licensed under MIT License. 
