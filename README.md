# CLI Companion

Um companheiro digital para o seu terminal: um personagem animado, colorido e reativo que vive ao lado do seu CLI.

> **Status:** em construção. A estrutura do projeto e as ferramentas já estão configuradas; o código do companion está sendo desenvolvido.

## Escopo

- Personagem em ASCII/Unicode com **ciclos de animação** por estado (`idle`, `happy`, ...)
- **Cores** via ANSI no terminal
- **Reativo ao usuário**: o estado muda conforme eventos (a começar pelo teclado)
- **Máquina de estados** simples para controlar as transições

### Ideias para as próximas etapas

- Reagir ao código de saída do último comando (hooks `precmd`/`preexec` do shell)
- Reagir a eventos do git, ociosidade e hora do dia
- Falas e personalidade
- Persistência de estado (humor, etc.)

## Stack

| Peça | Tecnologia |
| --- | --- |
| Linguagem | TypeScript |
| Interface de terminal | [Ink](https://github.com/vadimdemedes/ink) (React para CLI) |
| Execução em desenvolvimento | [tsx](https://github.com/privatenumber/tsx) |
| Runtime | Node.js 20+ |

## Como rodar

```bash
git clone https://github.com/M-Machado1/CLI-Companion.git
cd CLI-Companion
npm install
npm run dev
```

Outros scripts:

```bash
npm run typecheck   # checagem de tipos (tsc, sem gerar arquivos)
```

> O `npm run dev` precisa de um terminal interativo (o Ink usa *raw mode* para ler o teclado).

## Estrutura planejada

```
src/
  index.tsx              # ponto de entrada
  App.tsx                # tela principal e reação ao teclado
  companion/
    sprites.ts           # frames e cores por estado (só dados)
    Companion.tsx        # componente que anima o personagem
    machine.ts           # estados e transições (lógica pura)
```

## Contribuindo

- Commits seguem o padrão [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `chore:`, `docs:`...)
- Rode `npm run typecheck` antes de abrir um PR