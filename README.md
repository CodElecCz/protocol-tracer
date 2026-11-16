# Protocol Tracer

Protocol Tracer (TracerUI) is a Qt desktop application for cyclic monitoring and control of configured device values. It organizes communication tasks, areas, and typed nodes in an editable tree, showing live read/write values, update times, descriptions, and exceptions.

The project includes models and libraries for:

- **Modbus** over serial or Ethernet.
- **OMC8000** over serial or network.
- **ELM327** over serial.

XML profiles define each task's communication settings and polling interval, mapped areas, access mode, and nodes. Start or stop the configured tasks from the toolbar. Writable nodes can be edited in the **W** column; only configure writes for devices and values that are safe to change.

## Interface

The screenshot shows a Modbus profile displayed as a tree, with current values, write values, read/write timestamps, descriptions, and status indicators.

![Protocol Tracer tree view monitoring configured device values](screenshots/Tracer01.png)

## Run the Windows build

A 64-bit Windows build and its Qt runtime files are included in `bin/msvc2017_64/`. Run `TracerUI.exe`, then use **File → Open** to load an XML profile from that directory. Review and adjust its communication settings and addresses for your test setup before starting any tasks.

## Build from source

The project uses Qt 5 and qmake. The 64-bit project is `TracerUI_64.pro`; it references the bundled 64-bit protocol libraries under `Lib/Build64/`.

1. Install Qt 5.14.2 with the MSVC 2017 64-bit toolchain and the Qt Charts and XML modules.
2. Open `TracerUI_64.pro` in Qt Creator and select the matching MSVC 2017 64-bit kit.
3. Build and run the `TracerUI` target.

## XML profile format

The root element selects the backend: `modbus`, `omc8000`, or `elm327`. A task describes its serial or network connection and polling interval. Areas map protocol data and define access; nested nodes provide typed values, offsets, and descriptions. See [`TracerUI.txt`](TracerUI.txt) and the sample XML profiles in `bin/msvc2017_64/`.

## Project article

- [Česky: Protocol Tracer](https://codeleccz.github.io/codelec.web/blog/protocol-tracer/)
- [English: Protocol Tracer](https://codeleccz.github.io/codelec.web/en/blog/protocol-tracer/)
