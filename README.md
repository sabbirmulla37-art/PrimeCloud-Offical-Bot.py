PrimeCloud Docker Updated Bot
============================

Included:
- bot.py: Docker-based VPS manager with numeric command prefix `1`.
- custom_commands.json: persistent custom command storage.
- Dockerfile + docker-compose.yml: optional Docker deployment for the bot itself.
- requirements.txt: discord.py dependency.

Command prefix:
- Old: !help
- New: 1help

Custom command:
1coustem_command hello Hello!

This stores only `hello` as the command name, so users can run:
1hello

VPS creation:
1create @user <ram_GB> <cpu_cores> <disk_GB>

The create progress message is:
☁️ Creating VPS
Deploying ubuntu:22.04 VPS for @user
PrimeCloud | VPS Manager • date/time

After successful creation, the user receives the updated PrimeCloud VPS Created DM.

Docker deployment of the bot itself (optional):
1. Put your bot token in an environment variable:
   export DISCORD_BOT_TOKEN='YOUR_BOT_TOKEN'
2. Build/start:
   docker compose up -d --build
3. Check logs:
   docker compose logs -f

The compose file mounts /var/run/docker.sock so bot.py can manage VPS containers through the host Docker daemon.
Do NOT publish the Docker socket to the network.

If you run bot.py directly on the VPS instead of inside Docker:
   export DISCORD_BOT_TOKEN='YOUR_BOT_TOKEN'
   python3 bot.py
   
