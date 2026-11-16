# Protocol Tracer: a tree view of device values

**Protocol Tracer (TracerUI)** is a C++ and Qt desktop application for cyclic monitoring and control of configured device values. It presents communication tasks, areas, and typed nodes in an editable tree. Depending on the selected XML profile, it supports Modbus, OMC8000, and ELM327.

![Protocol Tracer interface showing configured values and read/write details](../screenshots/Tracer01.png)

## Live value overview

After an XML profile is loaded, the application displays its tasks and data areas. The table shows read and write values, read/write timestamps, descriptions, and status indicators. Tasks can be started and stopped from the toolbar; writable nodes can be edited in the **W** column.

This is not a generic raw-packet capture tool. It polls the values and nodes defined by a profile and displays their associated status and errors.

## Supported profiles

- **Modbus** — serial or Ethernet tasks, with areas defining data type, address, count, and read/write access.
- **OMC8000** — tasks over serial or network connections.
- **ELM327** — serial tasks for the nodes configured in a profile.

Profiles describe tasks, areas, and nodes. A task defines its connection and polling interval; an area defines data and access; and a node describes a typed value, offset, and description. The root XML element (`modbus`, `omc8000`, or `elm327`) selects the corresponding application model.

## Run the application

A 64-bit Windows build is included in `bin/msvc2017_64/`. Start `TracerUI.exe`, open a matching XML profile through **File → Open**, and adjust the communication settings and addresses for your test setup before starting tasks.

The source project uses Qt 5 and qmake. To build the 64-bit version, open `TracerUI_64.pro` in Qt Creator with Qt 5.14.2 and the MSVC 2017 64-bit kit. The configuration format is described in [`TracerUI.txt`](../TracerUI.txt).

> **Caution:** Writing through the **W** column can change values on the connected device. Verify address mappings, access settings, and the target test device before starting communication.

Source code: [CodElecCz/protocol-tracer](https://github.com/CodElecCz/protocol-tracer).
