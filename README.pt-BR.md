# Mission board

[English](README.md) | [Português (Brasil)](README.pt-BR.md) | [Español (España)](README.es-ES.md)

![Um quadro de missões de uma guilda pirata com o chapéu do Chopper e os livros de arqueologia da Robin.](docs/assets/mission-board.png)

Um assistente de carreira com arquivos locais, feito com skills e arquivos
simples. Registre sua experiência, encontre oportunidades e prepare candidaturas
adaptadas a cada vaga.

## Status

A skill `career-record` mantém o perfil, o registro de experiências e os
objetivos profissionais em `~/.local/share/mission-board/`. A skill `job-search`
avalia uma vaga trazida pela pessoa com base nesses registros e acompanha seu
status. A skill `job-snapshot` reúne essas vagas em uma página HTML para
compartilhar. A busca em sites de vagas, a adaptação de currículos, as cartas de
apresentação e a exportação para PDF ainda não foram implementadas.

## Skills disponíveis

[Ideal work](.agents/skills/ideal-work/SKILL.md) conduz uma conversa sobre o
trabalho que você gosta de fazer, como quer colaborar e seus próximos objetivos
profissionais. Escolha uma descrição curta, alguns parágrafos ou uma reflexão
pessoal mais completa.

Para começar, peça ao seu agente para usar `ideal-work` neste repositório. Por
exemplo:

> Use ideal-work para me ajudar a descobrir como quero trabalhar e o que explorar a seguir.

O exercício fica na conversa, a menos que você peça para salvá-lo em
`~/.local/share/mission-board/`, fora deste repositório.

## Escopo planejado

- Registrar o trabalho do dia a dia, responsabilidades, projetos e resultados.
- Revisar currículos para melhorar a clareza, identificar afirmações sem evidências e informações desatualizadas.
- Adaptar currículos a uma vaga com base na experiência real da pessoa.
- Pesquisar vagas conforme as preferências da pessoa e retornar links das fontes.
- Escrever cartas de apresentação com base na experiência da pessoa e na vaga.
- Exportar currículos e cartas de apresentação para PDF quando necessário.

Os registros de carreira são o material de origem. Currículos e cartas são
documentos adaptados a cada candidatura. A pessoa revisa cada candidatura e
decide o que enviar.

## Limites

Sem candidaturas automáticas, contato em massa, spam no LinkedIn ou automação de
engajamento. Nunca inventar experiências, qualificações ou resultados para
corresponder à descrição de uma vaga.

## Arquivos públicos e privados

Este repositório se destina a skills reutilizáveis, modelos, documentação e
exemplos fictícios. Dados pessoais, registros de carreira, vagas salvas,
anotações sobre candidaturas e documentos gerados ficam em
`~/.local/share/mission-board/`, fora do repositório. Nunca copie esses dados
para o repositório, inclua-os em commits ou publique seu conteúdo.

O uso de arquivos locais descreve onde eles ficam armazenados. Um provedor de IA
ainda pode processar o conteúdo fornecido ao assistente.

## Desenvolvimento

Acompanhe o trabalho nas [GitHub Issues](https://github.com/momoi-labs/mission-board/issues).
Leia os [princípios de engenharia](docs/PRINCIPLES.md) antes de contribuir.
