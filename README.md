# CoxelC

-  CoxelC is a NeoForge `Minecraft` mod designed for Minecraft 1.21 (NeoForge 21.1.172) that embeds `TinyCC` (TCC)
-  via the Java Native Interface (JNI). It allows developers to write Minecraft mods directly in the C
-  programming language without needing to recompile Java code.

  ---
##  Key Features

-    Embedded C Compiler (TinyCC): Integrates TinyCC to compile .c source files into dynamic libraries (.so)
      and load them dynamically at runtime (in memory).
-    Event Callbacks: Exposes common Minecraft server events to C mods:
      - on_player_join
      - on_player_leave
      - on_player_chat
      - on_player_death
      - on_server_tick
      - on_block_break
-    C Utility Functions: Provides built-in utility functions for C mods:
      - coxelc_send_chat(...)
      - coxelc_log(...)
      - coxelc_run_command(...)
      - coxelc_get_player_pos(...)

  ---
##  Usage
- Developing C Mods:
     Place your custom C source files into the coxelc_mods directory created at runtime, referencing the
  coxelc.h header for available functions and callbacks.
- Physics & Heavy Voxel Computations: Offloads intensive mathematical operations (e.g., complex mechanical linkages, projectile dynamics, and voxel field updates) directly to native C execution. (not now)

  ---
## Ex.
```c
#include "coxelc.h"

void on_player_join(const char *name)
{
    coxelc_send_chat("§a[CoxelC] Welcome, %s!", name);
    coxelc_log("Player joined: %s", name);
    coxelc_run_command("say Hello from C!");
    double x, y, z;
    coxelc_get_player_pos(name, &x, &y, &z);
    coxelc_log("pos: %.1f %.1f %.1f", x, y, z);
}

void on_player_leave(const char *name)
{
    coxelc_send_chat("§c[CoxelC] Goodbye, %s!", name);
}

void on_player_chat(const char *name, const char *message)
{
    coxelc_log("[Chat] %s: %s", name, message);
}

void on_player_death(const char *name)
{
    coxelc_send_chat("§4[CoxelC] %s died!", name);
}

void on_block_break(const char *name, const char *block, int x, int y, int z)
{
    coxelc_log("%s broke %s at %d %d %d", name, block, x, y, z);
}

void on_server_tick(void)
{
    coxelc_log("tick!");
}
```
