# PRISMA

PRISMA é um jogo de quebra-cabeça em que o jogador ajusta espelhos para refletir um feixe de luz até um cristal. O repositório contém o projeto do jogo feito no Godot e seus recursos de áudio, cenas e scripts.

## Requisitos

- Godot **4.6** (versão indicada em `project.godot`).
- Windows, Linux ou macOS com suporte ao Godot 4.6.
- Não há dependências externas ou variáveis de ambiente necessárias no estado atual.

## Abrir e executar

1. Clone ou baixe este repositório.
2. Abra o Godot 4.6 e escolha **Importar**.
3. Selecione a pasta do repositório e importe `project.godot`.
4. Abra o projeto e pressione **F6** para executar a cena atual ou **F5** para executar o projeto a partir do menu principal.
5. No menu, inicie uma partida e use os controles abaixo.

O projeto inicia pela cena `scenes/menu.tscn`. O documento [README_PROTOTIPO.md](README_PROTOTIPO.md) contém detalhes adicionais sobre a organização e os elementos do protótipo.

## Controles

- Clique em um espelho para selecioná-lo.
- Use `1`, `2` e, nas fases que oferecem mais espelhos, `3` e `4`; `Tab` alterna a seleção.
- Use `Q` e `E` para girar o espelho selecionado.
- Use `R` para reiniciar a fase.
- Depois de concluir o objetivo, use `N` para avançar quando disponível.
- Use `M` para alternar a música e `Esc` para voltar ao menu.

## Verificação funcional

O projeto ainda não possui uma suíte de testes automatizados. Para conferir manualmente uma alteração que afete o jogo:

1. Importe o projeto no Godot 4.6 e execute-o com **F5**.
2. Inicie uma fase, selecione um espelho e confirme que `Q`/`E` alteram sua orientação e o trajeto do feixe.
3. Direcione a luz ao cristal e confirme o feedback de conclusão; use `R` para conferir o reinício e `N` para avançar, quando disponível.
4. Confirme que `M` alterna o áudio e `Esc` retorna ao menu.
5. Ao modificar cenas ou recursos, confira também as fases e a saída de erros do Godot.

## Estrutura principal

- `project.godot`: configuração do projeto e cena inicial.
- `scenes/`: menu, fases e tela de conclusão.
- `scripts/`: lógica do jogo, espelhos, feixe de luz, cristais e música.
- `assets/audio/`: músicas e áudio ambiente.
- `README_PROTOTIPO.md`: documentação detalhada do protótipo.
- `docs/gcs/Plano_GCS_PRISMA.md`: plano de Gestão de Configuração de Software.

## Exportar uma versão

No Godot, abra **Project → Export**, configure a plataforma e os templates de exportação necessários, escolha o destino fora das pastas de código e use **Export Project**. Build local deve ficar em `build/`, `exports/` ou `dist/`, ignoradas pelo Git. Para uma entrega publicada, o artefato deve ser revisado antes de ser anexado a uma release.

## Configuração e segurança

O projeto não precisa de credenciais nem de variáveis de ambiente atualmente. `.env.example` registra essa condição; arquivos `.env` locais são ignorados pelo Git. Nunca comite senhas, tokens, chaves ou dados pessoais.
