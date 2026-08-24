```markdown
### Dispatcher / Protocol
| Endereço | Descrição |
| :--- | :--- |
| `0x14041bd00` | main game-packet dispatcher (custom opcodes 0x5DD-0x634, jump table @ 0x14041ddfc) |
| `0x14041ae60` | ProtocolGame connect path (auto-fires fingerprint upload) |
| `0x14042edb0` | ProtocolGame::parseGameServerCheckBot (opcode 0x5EA) |
| `0x1404474f0` | sendProcessList (reply opcode 0x50) |
| `0x140447660` | sendModuleList (reply opcode 0x51) |
| `0x1404477d0` | sendWindowList (reply opcode 0x52) |
| `0x14046d620` | OutputMessage ctor |
| `0x14041ac40` | addU8 (opcode writer) |
| `0x140733de0` | addU16 / count writer |
| `0x140733fc0` | addString |

### Collectors (HWID/environment cluster)
| Endereço | Descrição |
| :--- | :--- |
| `0x140752f20` | process enumerator (Toolhelp32) |
| `0x140752ce0` | module enumerator (EnumProcessModules) |
| `0x1407532b0` | window-title collector (EnumWindows driver) |
| `0x140753120` | EnumWindows callback (GetWindowTextA) |
| `0x1407518f0` | MAC address collector (GetAdaptersInfo) |
| `0x140751d50` | SMBIOS reader (GetSystemFirmwareTable 'RSMB') |
| `0x140752430` | disk serial reader (PhysicalDrive0 + IOCTL_STORAGE_QUERY_PROPERTY) |
| `0x140751c00` | MachineGuid registry reader |
| `0x140751340` | CPU name reader (registry) |
| `0x140751b60` | GetUserNameA wrapper |
| `0x1407526c0` | getHWID combiner (calls 1d50/2430/1c00) |
| `0x140750800` | FindWindowA boolean wrapper (isProcessRunning) |

### Fingerprint Upload
| Endereço | Descrição |
| :--- | :--- |
| `0x14046a800` | login extended-data builder/sender (opcode 0x000A, signal "getLoginExtendedData") |

### Blacklist Enforcement
| Endereço | Descrição |
| :--- | :--- |
| `0x1407c3de0` | blacklist/checksum orchestrator (reads BAD_* / DLL_CHECKSUM) |
| `0x1407c49e4` | call site -> process lister inside orchestrator |
| `0x1407c50e0` | "not clean" evaluator |
| `0x1407c5160` | loader-stage caller of terminator |
| `0x140516740` | terminator: PostMessageA(hwnd, WM_CLOSE) |

### Bot Protection / Integrity
| Endereço | Descrição |
| :--- | :--- |
| `0x1402daae0` | checkBotProtection native guard |
| `0x141ffd7c0` | guard byte A |
| `0x143754925` | guard byte B |
| `0x141da5b10` | "caught a lua call..." log string |
| `0x140510520` | selfChecksum |
| `0x14050e4b0` | filesChecksums |
| `0x14050e080` | fileChecksum |
| `0x14041acc0` | enableChecksum |

### Strings
| Endereço | Símbolo / Valor |
| :--- | :--- |
| `0x141e27748` | BAD_PROCESSES |
| `0x141e27758` | BAD_DLLS |
| `0x141e27768` | DLL_CHECKSUM |
| `0x141e27778` | BAD_FILES |
| `0x141db2050` | mangled parseGameServerCheckBot symbol |
| `0x141dac168` | checkBotProtection |
| `0x141e1cc78` | getHWID |
| `0x141e1cce0` | isProcessRunning |
| `0x141e1cc50` | getMacAddresses |
| `0x141e1d218` | filesChecksums |
| `0x141e1d228` | fileChecksum |
| `0x141e1d338` | selfChecksum |
| `0x141e1f558` | enableChecksum |
| `0x141db3730` | "getLoginExtendedData" |
