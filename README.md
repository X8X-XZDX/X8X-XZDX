```mermaid
flowchart TB
    subgraph User["User Interface"]
        Disks["Input Disks\n(ZIP Archives)"]
        TTY["TTY Terminal"]
    end

    subgraph CommandTypes["Command Types"]
        direction LR
        System["System Commands\n(p.commands)"]
        Program["Program Execution\n(Prefix + Command Strings)"]
    end

    subgraph HallucinationManagement["Hallucination Management"]
        Detection["Data Validation"]
        subgraph ProcessingModes["Processing Modes"]
            Creative["Creative Mode\n(Intentional Hallucination)"]
            Parsed["Parsed Mode\n(Validated Processing)"]
        end
        subgraph ChecksumEngine["Checksum Engine"]
            Recycler["Data Recycler"]
            ChecksumAgent["Checksum Agent"]
        end
        Logging["Situation Logging"]
    end

    subgraph ExecutionFlow["Execution Flow"]
        subgraph CommandStructure["Command Structure"]
            Prefix["Command Prefix\n(!!, %%, ##)"]
            Command["Command"]
            Chain["Command Chaining\n(,  ->)"]
            HFlags["Hallucination Flags"]
        end

        subgraph States["Execution States"]
            Start["Start\n(On-Call)"]
            Run["Run\n(Wait)"]
            End["End\n(Halted)"]
        end
    end

    subgraph Gizmo["Gizmo Framework"]
        Config["System Configuration"]
        Panel["Panel Context"]
        User["User Context"]
        StateManager["State Management"]
    end

    subgraph AI["AI Compute Layer"]
        CommandParser["Command Parser"]
        
        subgraph ExecutionEngine["Execution Engine"]
            AIParser["AI Parser\n(Natural Language Processing)"]
            CPUEmulator["CPU Emulator\n(ISA Implementation)"]
            CPUParser["CPU Parser\n(Instruction Decode)"]
        end
        
        Reporter["Output Handler"]
    end

    TTY --> CommandTypes
    Disks --> Config
    
    System --> Panel
    Program --> CommandStructure
    
    CommandStructure --> HallucinationManagement
    ProcessingModes --> ChecksumEngine
    Parsed --> ChecksumEngine
    HallucinationManagement --> States
    States --> CommandParser
    
    CommandParser --> AIParser
    AIParser --> CPUParser
    CPUParser --> CPUEmulator
    CPUEmulator --> Reporter
    
    Panel --> StateManager
    User --> StateManager
    StateManager --> ExecutionEngine
    
    Reporter --> TTY
    
    Creative --> Logging
