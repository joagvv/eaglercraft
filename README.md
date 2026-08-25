# Eaglercraft 1.8.8 — Campeonato no Servidor

Manual completo para preparar um mundo de campeonato para **Eaglercraft/Minecraft 1.8.8**, usando um servidor e comandos do Minecraft.

## 1. Visão geral

Formato recomendado:

- 20 jogadores
- 4 times de 5 jogadores
- Time A — vermelho
- Time B — azul
- Time C — verde
- Time D — amarelo
- 5 minutos de preparação
- 15 minutos de batalha
- PvP desligado durante a preparação
- PvP ligado durante a batalha
- kills individuais no placar
- pontos por equipe
- anúncio do vencedor

Fluxo:

```text
Servidor liga
   ↓
Mundo do campeonato carrega
   ↓
Jogadores entram
   ↓
Times são definidos
   ↓
5 minutos de preparação
   ↓
PvP ON
   ↓
15 minutos de batalha
   ↓
PvP OFF
   ↓
placar final
   ↓
vencedor
```

O mundo pode ser preparado uma vez, salvo e reutilizado. Construções, command blocks e alterações do mundo ficam salvos quando o mundo é salvo corretamente.

---

# 2. Onde usar os comandos

## Chat do Minecraft

Use para comandos executados manualmente como administrador/OP.

Exemplo:

```mcfunction
/scoreboard teams add TimeA "TIME A"
```

## Command Block

Use para comandos automáticos durante a partida.

Exemplo:

```mcfunction
/scoreboard players remove @a Timer 1
```

## Console do servidor

No console, normalmente o comando é escrito **sem** `/`.

No jogo:

```text
/gamerule pvp false
```

No console:

```text
gamerule pvp false
```

---

# 3. Criar os times

## Time A

```mcfunction
/scoreboard teams add TimeA "TIME A"
```

## Time B

```mcfunction
/scoreboard teams add TimeB "TIME B"
```

## Time C

```mcfunction
/scoreboard teams add TimeC "TIME C"
```

## Time D

```mcfunction
/scoreboard teams add TimeD "TIME D"
```

---

# 4. Definir a cor de cada time

## Time A — vermelho

```mcfunction
/scoreboard teams option TimeA color red
```

## Time B — azul

```mcfunction
/scoreboard teams option TimeB color blue
```

## Time C — verde

```mcfunction
/scoreboard teams option TimeC color green
```

## Time D — amarelo

```mcfunction
/scoreboard teams option TimeD color yellow
```

Cores disponíveis incluem:

```text
black
dark_blue
dark_green
dark_aqua
dark_red
dark_purple
gold
gray
dark_gray
blue
green
aqua
red
light_purple
yellow
white
```

---

# 5. Impedir dano entre jogadores do mesmo time

## Time A

```mcfunction
/scoreboard teams option TimeA friendlyfire false
```

## Time B

```mcfunction
/scoreboard teams option TimeB friendlyfire false
```

## Time C

```mcfunction
/scoreboard teams option TimeC friendlyfire false
```

## Time D

```mcfunction
/scoreboard teams option TimeD friendlyfire false
```

---

# 6. Adicionar jogadores aos times

Substitua `NOME` pelo nome do jogador.

## Time A

```mcfunction
/scoreboard teams join TimeA NOME
```

Exemplo:

```mcfunction
/scoreboard teams join TimeA Joao
```

## Time B

```mcfunction
/scoreboard teams join TimeB NOME
```

## Time C

```mcfunction
/scoreboard teams join TimeC NOME
```

## Time D

```mcfunction
/scoreboard teams join TimeD NOME
```

---

# 7. Ver todos os times

Para conferir os times e jogadores:

```mcfunction
/scoreboard teams list
```

---

# 8. Alterar o nome exibido do time

O identificador interno do time, por exemplo `TimeA`, não é renomeado diretamente.

Uma maneira de trocar o nome exibido é usar um **prefixo**.

Exemplo: fazer o Time A aparecer como `[TIGRES]`.

```mcfunction
/scoreboard teams option TimeA prefix "§c[TIGRES] "
```

Outros exemplos:

```mcfunction
/scoreboard teams option TimeB prefix "§9[DRAGÕES] "
```

```mcfunction
/scoreboard teams option TimeC prefix "§a[LOBOS] "
```

```mcfunction
/scoreboard teams option TimeD prefix "§e[ÁGUIAS] "
```

Assim, um jogador pode aparecer como:

```text
[TIGRES] Joao
```

---

# 9. Trocar o nome interno do time

Se você quer que o identificador interno também seja diferente, crie um novo time.

Exemplo:

```mcfunction
/scoreboard teams add Tigres "TIGRES"
```

Depois:

```mcfunction
/scoreboard teams option Tigres color red
```

```mcfunction
/scoreboard teams option Tigres friendlyfire false
```

```mcfunction
/scoreboard teams option Tigres prefix "§c[TIGRES] "
```

Coloque o jogador nele:

```mcfunction
/scoreboard teams join Tigres NOME
```

Quando não precisar mais do time antigo:

```mcfunction
/scoreboard teams remove TimeA
```

---

# 10. Exemplos completos de equipes

## TIGRES — vermelho

```mcfunction
/scoreboard teams add Tigres "TIGRES"
/scoreboard teams option Tigres color red
/scoreboard teams option Tigres friendlyfire false
/scoreboard teams option Tigres prefix "§c[TIGRES] "
```

## DRAGÕES — azul

```mcfunction
/scoreboard teams add Dragoes "DRAGÕES"
/scoreboard teams option Dragoes color blue
/scoreboard teams option Dragoes friendlyfire false
/scoreboard teams option Dragoes prefix "§9[DRAGÕES] "
```

## LOBOS — verde

```mcfunction
/scoreboard teams add Lobos "LOBOS"
/scoreboard teams option Lobos color green
/scoreboard teams option Lobos friendlyfire false
/scoreboard teams option Lobos prefix "§a[LOBOS] "
```

## ÁGUIAS — amarelo

```mcfunction
/scoreboard teams add Aguias "ÁGUIAS"
/scoreboard teams option Aguias color yellow
/scoreboard teams option Aguias friendlyfire false
/scoreboard teams option Aguias prefix "§e[ÁGUIAS] "
```

---

# 11. Spawns dos times

Use:

```mcfunction
/spawnpoint NOME X Y Z
```

Exemplo:

```mcfunction
/spawnpoint Joao 100 65 200
```

Faça isso para os jogadores de cada equipe.

Exemplo:

```mcfunction
/spawnpoint Joao 100 65 200
/spawnpoint Pedro 100 65 200
/spawnpoint Lucas 100 65 200
```

Substitua as coordenadas pelas bases reais do seu mapa.

---

# 12. Placar de kills individuais

Crie o objetivo:

```mcfunction
/scoreboard objectives add Kills playerKillCount "Kills"
```

Mostrar na lateral:

```mcfunction
/scoreboard objectives setdisplay sidebar Kills
```

Zerar as kills:

```mcfunction
/scoreboard players reset @a Kills
```

---

# 13. Placar dos times

Crie:

```mcfunction
/scoreboard objectives add TeamKills dummy "Pontos"
```

Zere os quatro:

```mcfunction
/scoreboard players set TimeA TeamKills 0
```

```mcfunction
/scoreboard players set TimeB TeamKills 0
```

```mcfunction
/scoreboard players set TimeC TeamKills 0
```

```mcfunction
/scoreboard players set TimeD TeamKills 0
```

Mostrar os pontos:

```mcfunction
/scoreboard objectives setdisplay sidebar TeamKills
```

Exemplo:

```text
Pontos

TimeA  27
TimeB  21
TimeC  18
TimeD  12
```

---

# 14. Timer do campeonato

Crie:

```mcfunction
/scoreboard objectives add Timer dummy "Tempo"
```

## Preparação

5 minutos = 300 segundos.

```mcfunction
/scoreboard players set @a Timer 300
```

PvP desligado:

```mcfunction
/gamerule pvp false
```

Mensagem:

```mcfunction
/title @a title {"text":"PREPARAÇÃO","color":"yellow"}
```

```mcfunction
/title @a subtitle {"text":"A batalha começa em 5 minutos!","color":"gold"}
```

## Batalha

15 minutos = 900 segundos.

```mcfunction
/scoreboard players set @a Timer 900
```

Ligar PvP:

```mcfunction
/gamerule pvp true
```

Mensagem:

```mcfunction
/title @a title {"text":"BATALHA!","color":"red"}
```

```mcfunction
/title @a subtitle {"text":"15 minutos!","color":"gold"}
```

---

# 15. Como montar o timer com command block

Na 1.8.8, usando somente comandos, o timer precisa ser acionado por um **clock de redstone**.

Faça uma área de controle no mapa.

Estrutura:

```text
[Clock de redstone]
        ↓
[Command Block]
```

No command block:

```mcfunction
/scoreboard players remove @a Timer 1
```

O relógio deve emitir aproximadamente um pulso por segundo.

A lógica é:

```text
300
↓
299
↓
298
↓
...
↓
0
↓
BATALHA
↓
900
↓
899
↓
...
↓
0
↓
FIM
```

---

# 16. Iniciar a batalha

Quando a preparação chegar a zero, execute:

```mcfunction
/gamerule pvp true
```

```mcfunction
/scoreboard players set @a Timer 900
```

```mcfunction
/title @a title {"text":"BATALHA!","color":"red"}
```

```mcfunction
/title @a subtitle {"text":"15 minutos!","color":"gold"}
```

Esses comandos podem ficar em command blocks acionados pela lógica de transição do timer.

---

# 17. Finalizar a batalha

Quando os 15 minutos acabarem:

```mcfunction
/gamerule pvp false
```

```mcfunction
/title @a title {"text":"FIM DA PARTIDA!","color":"gold"}
```

```mcfunction
/title @a subtitle {"text":"Contagem final de pontos","color":"yellow"}
```

---

# 18. Pontuar kills por time

O placar individual é:

```mcfunction
/scoreboard objectives add Kills playerKillCount "Kills"
```

O placar da equipe é:

```mcfunction
/scoreboard objectives add TeamKills dummy "Pontos"
```

A operação de scoreboard pode copiar/somar o valor de kills de um jogador para o total de seu time.

Exemplo:

```mcfunction
/scoreboard players operation TimeA TeamKills += Joao Kills
```

Outro jogador:

```mcfunction
/scoreboard players operation TimeA TeamKills += Pedro Kills
```

Time B:

```mcfunction
/scoreboard players operation TimeB TeamKills += Ana Kills
```

Use o mesmo princípio para os demais jogadores.

## Atenção

Não execute a soma repetidamente sem controlar o valor que já foi contabilizado. Caso contrário, uma mesma kill pode ser somada mais de uma vez.

Para 20 jogadores e contagem automática confiável, um plugin de servidor é mais adequado.

---

# 19. Anunciar o vencedor

## Time A

```mcfunction
/title @a title {"text":"TIME A VENCEU!","color":"red"}
```

```mcfunction
/say §c🏆 TIME A VENCEU!
```

## Time B

```mcfunction
/title @a title {"text":"TIME B VENCEU!","color":"blue"}
```

```mcfunction
/say §9🏆 TIME B VENCEU!
```

## Time C

```mcfunction
/title @a title {"text":"TIME C VENCEU!","color":"green"}
```

```mcfunction
/say §a🏆 TIME C VENCEU!
```

## Time D

```mcfunction
/title @a title {"text":"TIME D VENCEU!","color":"yellow"}
```

```mcfunction
/say §e🏆 TIME D VENCEU!
```

---

# 20. Reset completo para uma nova partida

Use:

```mcfunction
/scoreboard players set TimeA TeamKills 0
```

```mcfunction
/scoreboard players set TimeB TeamKills 0
```

```mcfunction
/scoreboard players set TimeC TeamKills 0
```

```mcfunction
/scoreboard players set TimeD TeamKills 0
```

```mcfunction
/scoreboard players reset @a Kills
```

```mcfunction
/scoreboard players set @a Timer 300
```

```mcfunction
/gamerule pvp false
```

Depois, inicie novamente a preparação.

---

# 21. Sala de controle recomendada

Crie uma área administrativa no mundo.

Exemplo:

```text
┌───────────────────────────────┐
│      CONTROLE DO CAMPEONATO   │
│                               │
│  RESET                        │
│  PREPARAÇÃO                   │
│  BATALHA                      │
│  FINAL                        │
│                               │
│  REDSTONE CLOCK               │
│       ↓                       │
│  COMMAND BLOCKS               │
└───────────────────────────────┘
```

Nessa sala você pode deixar os command blocks separados por função.

---

# 22. Como preparar o mundo uma vez

Faça:

1. construa as quatro bases;
2. configure os times;
3. configure as cores;
4. configure os nomes;
5. defina os spawns;
6. crie os scoreboards;
7. monte os command blocks;
8. monte o clock;
9. teste a partida;
10. salve o mundo;
11. faça backup.

Depois disso, o mesmo mundo pode ser carregado novamente pelo servidor.

---

# 23. Servidor

Arquitetura:

```text
Jogador
   ↓
Cliente Eaglercraft
   ↓
EaglerXServer
   ↓
Servidor Minecraft
   ↓
Mundo do campeonato
   ↓
Command blocks / plugin
```

Os jogadores não precisam usar Terminal.

O servidor mantém:

- mundo;
- times;
- placares;
- command blocks;
- regras;
- spawns;
- partida.

---

# 24. Mundo salvo

O mapa do campeonato deve ser salvo no servidor.

Ao iniciar novamente:

```text
servidor liga
↓
mundo carrega
↓
construções continuam
↓
command blocks continuam
↓
times continuam criados
↓
scoreboards continuam existentes
```

Antes de cada nova partida, faça o reset.

---

# 25. Backup

Mantenha cópias do mundo:

```text
backup-campeonato-01
backup-campeonato-02
backup-campeonato-final
```

Faça backup principalmente antes de uma partida oficial.

---

# 26. Cliente HTML e servidor

O cliente web e o servidor são partes separadas.

```text
GitHub Pages
      ↓
cliente Eaglercraft
      ↓
servidor EaglerXServer
      ↓
mundo do campeonato
```

O GitHub Pages serve os arquivos do cliente.

O servidor mantém o mundo e o multiplayer.

Os jogadores não precisam rodar comandos ou Terminal para entrar.

---

# 27. Checklist de preparação

- [ ] Servidor configurado
- [ ] Mundo carregando
- [ ] Backup feito
- [ ] Time A criado
- [ ] Time B criado
- [ ] Time C criado
- [ ] Time D criado
- [ ] Cores definidas
- [ ] Nomes definidos
- [ ] Friendly fire desligado
- [ ] 20 jogadores separados
- [ ] 5 jogadores por time
- [ ] Bases construídas
- [ ] Spawns configurados
- [ ] Kills configuradas
- [ ] TeamKills configurado
- [ ] Timer configurado
- [ ] Clock testado
- [ ] PvP OFF testado
- [ ] PvP ON testado
- [ ] 15 minutos testados
- [ ] fim da partida testado
- [ ] placar testado
- [ ] vencedor testado

---

# 28. Exemplo final

```text
CAMPEONATO EAGLERCRAFT 1.8.8

20 JOGADORES

🔴 TIGRES — 5
🔵 DRAGÕES — 5
🟢 LOBOS — 5
🟡 ÁGUIAS — 5

PREPARAÇÃO: 5 MINUTOS
BATALHA: 15 MINUTOS

PONTUAÇÃO:
1 KILL = 1 PONTO

FIM:
Maior pontuação = CAMPEÃO
```

---

# 29. Regras importantes

- Use comandos compatíveis com Minecraft/Eaglercraft 1.8.8.
- Não misture sintaxe de versões mais novas sem confirmar compatibilidade.
- Teste todos os command blocks antes da partida oficial.
- Faça backup do mundo antes do campeonato.
- Para soma automática de kills, timer completo e vencedor automático, considere usar um plugin de servidor.
- O mundo preparado pode ser reutilizado em várias partidas.

---

# 30. Resumo dos comandos essenciais

### Criar time

```mcfunction
/scoreboard teams add TimeA "TIME A"
```

### Cor

```mcfunction
/scoreboard teams option TimeA color red
```

### Friendly fire

```mcfunction
/scoreboard teams option TimeA friendlyfire false
```

### Adicionar jogador

```mcfunction
/scoreboard teams join TimeA NOME
```

### Ver times

```mcfunction
/scoreboard teams list
```

### Prefixo/nome exibido

```mcfunction
/scoreboard teams option TimeA prefix "§c[TIGRES] "
```

### Spawn

```mcfunction
/spawnpoint NOME X Y Z
```

### Kills

```mcfunction
/scoreboard objectives add Kills playerKillCount "Kills"
```

### Pontos por time

```mcfunction
/scoreboard objectives add TeamKills dummy "Pontos"
```

### Timer

```mcfunction
/scoreboard objectives add Timer dummy "Tempo"
```

### Preparação

```mcfunction
/gamerule pvp false
```

```mcfunction
/scoreboard players set @a Timer 300
```

### Batalha

```mcfunction
/gamerule pvp true
```

```mcfunction
/scoreboard players set @a Timer 900
```

### Timer por segundo

```mcfunction
/scoreboard players remove @a Timer 1
```

### Fim

```mcfunction
/gamerule pvp false
```

### Placar

```mcfunction
/scoreboard objectives setdisplay sidebar TeamKills
```

### Reset

```mcfunction
/scoreboard players set TimeA TeamKills 0
```

```mcfunction
/scoreboard players set TimeB TeamKills 0
```

```mcfunction
/scoreboard players set TimeC TeamKills 0
```

```mcfunction
/scoreboard players set TimeD TeamKills 0
```

```mcfunction
/scoreboard players reset @a Kills
```

---

## Regra principal

**Prepare o mundo uma vez, salve e faça backup.**

Depois:

```text
CARREGAR MUNDO
   ↓
ENTRAR COM 20 JOGADORES
   ↓
SEPARAR EM 4 TIMES
   ↓
RESETAR PLACAR
   ↓
5 MIN PREPARAÇÃO
   ↓
15 MIN BATALHA
   ↓
FINAL
   ↓
VENCEDOR
```
