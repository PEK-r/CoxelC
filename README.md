# CubeC-mod
A minecraft mod bridge between Java and C for C programmer.

Ex mod.c:
 void on_player_join(const char *name)
{
    cubec_send_chat("§aWelcome, %s! You are player #%d", name, 1);
    cubec_log("Player joined: %s", name);
}

all event CubeC has now:
 on_player_joina()
  Ex: void on_player_join(const char *name) {}
all function CubeC has now:
 cubec_send_chat()
  Ex: cubec_send_chat("§aWelcome, %s! You are player #%d", name, 1);
 cubec_log()
  Ex: cubec_log("Player joined: %s", name);
