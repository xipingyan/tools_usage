# VSCode Debug: Python (APP) + CPP (LIBS)

1: 安装exstentions： Python C++ Debugger  <br>
2：编译debug版本的cpp库  <br>
3：设置 .vscode/launch.json  <br>
3.1 添加：Python Debugger: Current File  <br>
3.2 添加：Python C++ Debugger
3.3 添加："(gdb) Attach"

Example: launch.json
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Attach",
            "type": "cppdbg",
            "request": "attach",
            "program": "[Your work path]/python-env/bin/python",
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "Set Disassembly Flavor to Intel",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ]
        },
        {
            "name": "Python C++ Debugger",
            "type": "pythoncpp",
            "request": "launch",
            // "pythonConfig": "default",
            // "cppConfig": "default (gdb) Attach"
            "pythonLaunchName": "Python Debugger: Current File",
            "cppAttachName": "(gdb) Attach"
        },
        {
            "name": "Python Debugger: Current File",
            "type": "debugpy",
            "request": "launch",
            "python": "[Your work path]/python-env/bin/python",
            "cwd": "[Your work path]/custom_op/1_register_kernel",
            "program": "[Your work path]/custom_op/1_register_kernel/test_register_custom_op.py",
            "env": {
                "PYTHONPATH":"/mnt/xiping/openvino/bin/intel64/Debug/python"
            },
            "console": "integratedTerminal"
        }
    ]
}
```
