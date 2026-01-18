# StepMania - Getting Started Guide

## What is StepMania?

**StepMania** is an advanced cross-platform rhythm game engine for home and arcade use. It's similar to Dance Dance Revolution (DDR) and other rhythm games. Players step on arrows in time with music, and the game supports custom songs, themes, and extensive modding.

---

## 🛠️ Technical Skills Required

To work with StepMania, you should have knowledge of:

### Core Programming Languages
- **C++** (Primary language) - The entire game engine is written in C++
  - Object-oriented programming
  - Template programming
  - Memory management
  - STL (Standard Template Library)
  
- **Lua** (Scripting language) - Used for:
  - Themes and UI customization
  - Gameplay logic
  - Screen transitions and effects
  - Custom modifications

### Build Tools & Systems
- **CMake** - Cross-platform build system generator
- **Visual Studio** (Windows) or **Xcode** (macOS) or **Make** (Linux)
- Git - Version control

### Graphics APIs (Optional, for advanced development)
- **OpenGL** - Primary graphics API
- **Direct3D** - Windows-specific graphics
- **GLES2** - Mobile/embedded systems

### Additional Technologies
- **FFmpeg** - Video/audio codec support
- **JSON** - Configuration and data files
- **XML** - Legacy configuration files

---

## 📁 Project Structure

```
stepmania/
├── src/                    # C++ source code (game engine)
│   ├── Actor*.cpp/h       # Actor system (game objects)
│   ├── Screen*.cpp/h      # Game screens (menus, gameplay)
│   ├── Rage*.cpp/h        # Core engine systems (RageEngine)
│   ├── Song*.cpp/h        # Song/music management
│   ├── Player*.cpp/h      # Player logic and input
│   ├── arch/              # Platform-specific code
│   └── archutils/         # Architecture utilities
│
├── Themes/                 # UI themes (Lua + XML)
│   ├── default/           # Default theme
│   ├── _fallback/         # Fallback theme (base)
│   └── legacy/            # Legacy theme
│
├── Data/                   # Game data files
│   ├── Translations.xml   # Language translations
│   ├── Shaders/           # Graphics shaders
│   └── AutoMappings/      # Input mappings
│
├── Songs/                  # Song packs (.sm, .ssc files)
├── NoteSkins/             # Note appearance customization
├── BGAnimations/          # Background animations (Lua)
├── BackgroundEffects/     # Background effects (Lua)
├── BackgroundTransitions/ # Transition effects
├── Courses/               # Course definitions
├── Characters/            # Dancing characters
│
├── extern/                # External dependencies
│   ├── lua-5.1/          # Lua interpreter
│   ├── ffmpeg/           # Audio/video codecs
│   ├── jsoncpp/          # JSON parsing
│   ├── libpng/           # PNG image support
│   ├── libjpeg/          # JPEG image support
│   └── (many more...)
│
├── Build/                 # Build documentation
├── Docs/                  # Documentation
│   ├── Themerdocs/       # Theme development docs
│   ├── Luadoc/           # Lua API documentation
│   └── Changelog*.txt    # Version history
│
├── CMakeLists.txt         # Main CMake configuration
└── StepmaniaCore.cmake    # Core build configuration
```

### Key Code Modules

1. **Actor System** (`Actor*.cpp/h`) - Base class for all visual elements
2. **Screen System** (`Screen*.cpp/h`) - Game state management (menus, gameplay)
3. **RageEngine** (`Rage*.cpp/h`) - Core engine (display, sound, files, input)
4. **Game Logic** (`Player*.cpp/h`, `Song*.cpp/h`) - Core gameplay
5. **Theming** (Lua files in `Themes/`) - UI and visual customization

---

## 🚀 How to Build and Run

### Prerequisites

#### Windows
1. **Visual Studio 2015 or later** (Community Edition works)
   - Include C++ desktop development workload
2. **CMake 2.8.12 or later**
   - Download from [cmake.org](https://cmake.org/download/)
   - Or install via Chocolatey: `choco install cmake`
3. **Microsoft Visual C++ Redistributable 2015**

#### macOS
1. **Xcode** with command-line tools
2. **CMake**
   - Via Homebrew: `brew install cmake`
   - Via MacPorts: `port install cmake`
3. **macOS 10.6.8 or later**

#### Linux
1. **GCC/G++** compiler
2. **CMake**
   - `sudo apt-get install cmake` (Debian/Ubuntu)
   - `sudo yum install cmake` (Red Hat/Fedora)
3. **Development libraries** (OpenGL, ALSA, etc.)

---

### Build Steps

#### Step 1: Install CMake
See prerequisites above for your platform.

#### Step 2: Generate Build Files

Navigate to the `Build/` directory:

```bash
cd Build
```

**Generate project files:**

```bash
# Windows (Visual Studio 2019)
cmake -G "Visual Studio 16 2019" .. && cmake ..

# Windows (Visual Studio 2022)
cmake -G "Visual Studio 17 2022" .. && cmake ..

# Windows XP support (if needed)
cmake -G "Visual Studio 16 2019" -T "v140_xp" .. && cmake ..

# macOS (Xcode)
cmake -G Xcode .. && cmake ..

# Linux (Makefiles)
cmake -G "Unix Makefiles" .. && cmake ..
```

**Note:** Running `cmake ..` twice ensures all variables are properly set.

#### Step 3: Build Type (Linux/Makefiles only)

For Debug build:
```bash
cmake -DCMAKE_BUILD_TYPE=Debug ..
```

For Release build:
```bash
cmake -DCMAKE_BUILD_TYPE=Release ..
```

Other options: `RelWithDbgInfo`, `MinSizeRel`

#### Step 4: Compile

**Windows:**
- Open the generated `.sln` file in Visual Studio
- Build the solution (F7 or Build → Build Solution)
- Executable will be in the project root

**macOS:**
- Open the generated `.xcodeproj` in Xcode
- Build the project (⌘B)
- App will be in the project root

**Linux:**
```bash
make
```
- Executable `stepmania` will be in the project root

---

## ▶️ Running StepMania

After building:

**Windows:**
```cmd
stepmania.exe
```

**macOS:**
```bash
open StepMania.app
```

**Linux:**
```bash
./stepmania
```

---

## 🎮 Basic Usage

1. **First Launch:**
   - The game will initialize with default settings
   - Navigate using arrow keys and Enter
   
2. **Adding Songs:**
   - Place song folders in the `Songs/` directory
   - Song formats: `.sm` (StepMania), `.ssc` (StepMania 5), `.dwi`, `.bms`, `.ksf`

3. **Theming:**
   - Themes are in `Themes/` directory
   - Edit Lua files to customize appearance
   - See `Docs/Themerdocs/` for documentation

4. **Configuration:**
   - Preferences are saved in the user profile
   - Edit `Data/` files for game-wide settings

---

## 📚 Learning Resources

### Official Documentation
- **Lua API:** `Docs/Luadoc/` folder
- **Theming:** `Docs/Themerdocs/` folder
- **Lua for SM5:** https://quietly-turning.github.io/Lua-For-SM5/
- **Website:** https://www.stepmania.com/

### Community
- **IRC:** irc.freenode.net/#stepmania-devs
- **GitHub:** https://github.com/stepmania/stepmania

### File Format Documentation
- **Course Format:** `Docs/CourseFormat.txt`
- **Simfile Formats:** `Docs/SimfileFormats/` directory
- **SSC Format:** `Docs/Changelog_SSCformat.txt`

---

## 🔧 Development Tips

### Modifying the Code
1. Make changes to C++ files in `src/`
2. Rebuild using your IDE or `make`
3. Test changes by running the executable

### Creating Themes
1. Copy `Themes/_fallback/` as a starting point
2. Modify Lua files for custom logic
3. Edit XML files for layouts
4. No recompilation needed - just restart StepMania

### Debugging
- **Windows:** Use Visual Studio's debugger
- **macOS:** Use Xcode's debugger or lldb
- **Linux:** Use gdb: `gdb ./stepmania`

### Quick Iteration
- For Lua/theme changes: No rebuild needed
- For C++ changes: Incremental builds are usually fast
- Use Debug builds during development for better error messages

---

## 📝 License

- **Source Code:** MIT License
- **Included Songs:** Creative Commons Non-Commercial (CC-NC)
- **MAD/FFmpeg:** GPL License (when MP3 support is enabled)

**You can:**
- Modify and distribute the engine
- Create commercial products with it

**You cannot:**
- Sell the game with included songs
- Remove credits or claim you created the engine
- Distribute builds with MP3 support without providing source code

---

## 🐛 Troubleshooting

### Build Fails
- Delete `CMakeCache.txt` and regenerate
- Ensure all dependencies are installed
- Check that CMake version is 2.8.12+

### Missing Visual C++ Runtime (Windows)
- Install [VC++ 2015 Redistributable](http://www.microsoft.com/en-us/download/details.aspx?id=48145)

### Linking Errors
- Clean build: Delete `Build/` contents and regenerate
- Ensure external libraries in `extern/` are present

---

## 🎯 Next Steps

1. **Build the project** following the steps above
2. **Run StepMania** and familiarize yourself with the game
3. **Explore the code** - Start with `src/Main.cpp`
4. **Read Lua documentation** if you want to create themes
5. **Join the community** on IRC for support

Happy coding! 🎵💃🕺
