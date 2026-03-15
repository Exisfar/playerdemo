# Repository Guidelines

## Project Structure & Module Organization
- `src/`: Core C++/Qt sources (`.cpp/.h`), UI forms (`.ui`), and resources (`mainwid.qrc`, `res/`).
- `lib/`: Third-party headers/libs for FFmpeg and SDL2 (primarily for Windows builds).
- `CMakeLists.txt` + `src/CMakeLists.txt`: CMake build entry points.
- `playerdemo.pro`: QtCreator/qmake project file for multi-platform builds.
- `playerdemo.sln` / `playerdemo.vcxproj`: Visual Studio project files.
- `scripts/`: Utility scripts (e.g., `scripts/windows-publish.ps1`).

## Build, Test, and Development Commands
- CMake (Linux/macOS with system FFmpeg + SDL2 installed):
  - `cmake -S . -B build`
  - `cmake --build build`
- QtCreator (all platforms):
  - Open `playerdemo.pro`, configure kits, then Build/Run.
- Linux deps (example):
  - `sudo apt-get install libsdl2-dev libavformat-dev libavutil-dev libavcodec-dev libswscale-dev libswresample-dev libavdevice-dev`
- macOS deps (example):
  - `brew install ffmpeg` (SDL2 is pulled in as a dependency; adjust paths in `playerdemo.pro` if needed).

## Coding Style & Naming Conventions
- Indentation: 4 spaces; braces on the next line (see `src/main.cpp`).
- Naming: Classes in `PascalCase`, methods in `camelCase`, member variables often prefixed with `m_`.
- Keep Qt idioms (signals/slots, `QWidget` patterns) consistent with existing code.
- No automated formatter is configured; match surrounding style.

## Testing Guidelines
- There is no dedicated test suite. Validate changes by building and running the app locally.
- If you add tests, document how to run them and where they live.

## Commit & Pull Request Guidelines
- Commit messages follow a conventional pattern: `feat:`, `fix:`, `docs:`, `test:` (see `git log`).
- PRs should include:
  - A clear summary of changes and affected platforms.
  - Linked issues (if applicable).
  - Screenshots or short clips for UI changes.

## Configuration & Dependencies
- Windows builds often rely on the `lib/` copies of FFmpeg/SDL2; ensure bitness matches your toolchain.
- macOS builds may require updating include/library paths in `playerdemo.pro` to match your Homebrew installation.
