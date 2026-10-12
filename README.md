# CoxelC

-  CoxelC is a NeoForge Minecraft mod designed for Minecraft 1.21 (NeoForge 21.1.172) that embeds TinyCC (TCC)
-  via the Java Native Interface (JNI). It allows developers to write Minecraft mods directly in the C
-  programming language without needing to recompile Java code.

  ---
##  Key Features

   1. Embedded C Compiler (TinyCC): Integrates TinyCC to compile .c source files into dynamic libraries (.so)
      and load them dynamically at runtime (in memory).
   2. Event Callbacks: Exposes common Minecraft server events to C mods:
      - on_player_join
      - on_player_leave
      - on_player_chat
      - on_player_death
      - on_server_tick
      - on_block_break
   3. C Utility Functions: Provides built-in utility functions for C mods:
      - cubec_send_chat(...)
      - cubec_log(...)
      - cubec_run_command(...)
      - cubec_get_player_pos(...)

  ---
##  Usage
- Developing C Mods:
     Place your custom C source files into the coxelc_mods directory created at runtime, referencing the
  coxelc.h header for available functions and callbacks.
