# eaglercraft
from pathlib import Path

path = Path("/mnt/data/README.md")

readme = r'''# Campeonato Eaglercraft 1.8.8 — Manual Completo do Servidor

Este documento explica, do começo ao fim, como preparar um **mundo de campeonato para Eaglercraft/Minecraft 1.8.8 em um servidor**, deixar os comandos salvos no mundo e iniciar uma partida quando os jogadores entrarem.

## 1. Como o sistema funciona

A ideia é preparar o mapa **uma única vez**.

```text
MAPA DO CAMPEONATO
        ↓
comandos + command blocks + spawns + times
        ↓
salvar o mundo
        ↓
servidor carrega o mesmo mundo novamente
        ↓
20 jogadores entram
        ↓
4 times de 5
        ↓
5 minutos de preparação
        ↓
15 minutos de batalha
        ↓
pontuação por kills
        ↓
fim da partida
        ↓
vencedor
