# Plano de Gestão de Configuração de Software — PRISMA

**Projeto:** PRISMA — jogo de quebra-cabeça de reflexão de luz  
**Responsável pelo projeto:** Felipe Schwabe (`Felipe-Schwabe`)  
**Par de revisão proposto:** Eduardo Gabriel Macedo (`Eduardo-Macedo07`)  
**Repositório:** [Felipe-Schwabe/N1_FelipeSchwabe](https://github.com/Felipe-Schwabe/N1_FelipeSchwabe)  
**Versão deste plano:** 1.0  
**Data:** 16/11/2026

## 1. Objetivo e escopo

Este plano define como identificar, versionar, revisar, proteger e disponibilizar os itens de configuração do PRISMA. Aplica-se ao projeto Godot 4.6, suas cenas, scripts, recursos, documentação e builds produzidas para validação ou entrega.

A versão atual não usa serviços externos, credenciais, variáveis de ambiente ou dependências de terceiros. Também não tem pipeline de publicação ou suíte automatizada de testes configurada; as verificações descritas aqui são manuais até que as aulas seguintes definam automação.

## 2. Papéis e responsabilidades

| Papel | Responsável | Responsabilidade |
|---|---|---|
| Responsável/desenvolvedor líder | Felipe Schwabe (`Felipe-Schwabe`) | Mantém o repositório e as baselines, prepara mudanças e builds, aprova deploys em produção e mantém este plano. |
| Par de revisão | Eduardo Gabriel Macedo (`Eduardo-Macedo07`) | Tem acesso de escrita após aceitar o convite; revisa e aprova Pull Requests de mudanças propostas pelo responsável. |
| Autor do Pull Request | Quem propõe a mudança | Descreve contexto e testes, mantém o PR focado e corrige apontamentos. Não aprova o próprio PR. |

A configuração de `.github/CODEOWNERS` identifica os responsáveis previstos. A aprovação deve ser feita pelo par, nunca pelo próprio autor.

## 3. Itens de configuração

Os itens abaixo são versionados no repositório. A branch `main` é a baseline integrada.

| Grupo | Itens principais | Identificação e controle |
|---|---|---|
| Código e lógica | `scripts/` | Alterações via branch e Pull Request; revisar o comportamento no Godot. |
| Cenas e interface | `scenes/` | Manter referências e recursos carregáveis; conferir as cenas inicial, de jogo e conclusão. |
| Recursos do jogo | `assets/`, `icon.svg` e arquivos importados associados | Preservar os arquivos de origem e metadados necessários ao Godot; verificar áudio e referências após mudanças. |
| Configuração do motor | `project.godot`, `export_presets.cfg` | Revisar versão do motor, cena inicial, controles e opções de exportação. Não guardar credenciais nesses arquivos. |
| Documentação | `README.md`, `README_PROTOTIPO.md`, `docs/gcs/` | Atualizar junto com mudanças de instalação, execução, controles e processo. |
| Colaboração e segurança | `.github/`, `.gitignore`, `.gitattributes`, `.env.example` | Versionar modelos e regras de colaboração; ignorar dados locais e segredos. |
| Builds | Executáveis e arquivos `.pck` exportados | Builds de trabalho ficam em `build/`, `exports/` ou `dist/`; não substituir uma entrega sem validar. |

### Dependências e lockfile

O projeto usa Godot 4.6 e não possui dependências de pacotes externos. Por isso, não há lockfile de gerenciador de pacotes a manter. A versão do motor e as configurações do projeto ficam registradas em `project.godot`; recursos necessários ao jogo são versionados junto com o projeto.

## 4. Identificação de versões e branches

- `main` contém a baseline integrada e deve permanecer protegida.
- Cada alteração começa em uma branch separada, por exemplo `feature/42-fase-espelhos` ou `fix/43-audio-menu`.
- Títulos de Pull Request usam Conventional Commits, por exemplo `feat(gameplay): adiciona nova fase` ou `fix(ui): corrige retorno ao menu`.
- A integração usa somente **Squash and merge**. A mensagem do commit de squash usa o título e a descrição do Pull Request; branches de trabalho são apagadas automaticamente após o merge.
- Mudanças aceitas na `main` formam uma nova baseline. O histórico do Git permite localizar o PR, o autor, a revisão e os arquivos alterados.

## 5. Controle de mudanças e revisão

1. Registrar defeitos e propostas em Issues usando os formulários do projeto.
2. Criar branch a partir da `main` e limitar cada PR a um objetivo.
3. Explicar contexto, decisão e passos de verificação no Pull Request.
4. Solicitar revisão do par com acesso de escrita. Exigir pelo menos uma aprovação antes do merge.
5. Corrigir as observações e obter nova aprovação se novos commits invalidarem uma aprovação anterior.
6. Fazer squash merge; não integrar commits diretamente na `main`.

A regra de proteção da `main` exige Pull Request, uma aprovação, descarte de aprovações antigas após novos commits, histórico linear e impede bypass das regras. A exigência de status checks fica desativada até que os checks sejam configurados na aula correspondente.

## 6. Ambientes e disponibilização

- **staging:** validação de uma build candidata antes da entrega. Deploy permitido somente a partir de branches protegidas.
- **production:** disponibilização da build aprovada. Deploy permitido somente a partir de branches protegidas e requer aprovação obrigatória de Felipe Schwabe. A opção que impede auto-revisão deve ficar desativada conforme a configuração da atividade.

O projeto ainda não tem pipeline que publique builds nesses ambientes. Até sua implantação, executar e verificar uma build localmente no Godot 4.6; não declarar um deploy concluído sem evidência de execução.

## 7. Verificação e aceite

Como não há testes automatizados configurados, verificar manualmente no Godot 4.6:

- projeto importa e inicia pelo menu;
- espelhos podem ser selecionados e girados, e o feixe muda de direção;
- cristal é ativado ao receber o feixe;
- reinício e progressão de fase funcionam quando disponíveis;
- música pode ser ligada/desligada e o retorno ao menu funciona;
- as cenas e recursos alterados não apresentam erros no Godot.

Registrar no PR os passos executados e o resultado. Se um defeito permanecer, abrir Issue com versão, ambiente, passos e evidências.

## 8. Proteção de dados e segredos

Não comitar senhas, tokens, chaves, dados pessoais ou configurações locais. `.env` e arquivos `.env.*` são ignorados; `.env.example` contém somente nomes ou comentários, nunca valores reais. Se um segredo for publicado, removê-lo do uso não é suficiente: revogar/rotacionar a credencial no serviço de origem e registrar a correção.

## 9. Manutenção do plano

Felipe mantém este documento quando mudar a estrutura, as ferramentas, a política de revisão ou os ambientes. Mudanças neste plano também devem passar por Pull Request e revisão do par.
