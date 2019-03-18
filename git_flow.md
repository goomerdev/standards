# Sugestão de Git Flow

A idéia é padronizar o *workflow* do time de desenvolvimento em relação à entrega e versionamento de código.

## Rebase Flow

O **rebase** é um dos comandos que integram mudanças entre *branches*, assim como o *merge*, ...

## Benefícios

Com um fluxo padrão de entrega de código ou **CD**(Continuous Delivery), a automatização por parte do time de **DevOps** é
facilitada e se torna mais consistente.

Conflitos são resolvidos localmente junto com a reescrita da história, assim cada *pull request* já vem "pronto" e o trabalho de quem vai aceitar as mudanças se torna mais fácil e rápido.

Práticas de *code review* se tornam mais viáveis, com um *pipe* de entrega mais homogêneo, rápido e efetivo por parte 
do processo de qualidade de código ser parcialmente automatizado, restando apenas a validação de qualidade pelo responsável
da *review*.

O processo de *squashing* torna o histórico de alterações mais limpo e linear, reduzindo vários *commits* que não agregam tanto à visualização da linha do tempo em poucos e mais relevantes.

## Como Fazer?

Abrimos uma nova *branch* para trabalhar originada da *develop* como de costume.

```bash
$ git checkout -b <nova-branch>
```

Após finalizarmos o trabalho, atualizamos a *branch develop* local e realizamos o **rebase**. Assim juntamos ambas as histórias ao mesmo tempo de resolver possíveis conflitos interativamente(*flag* -i) e realizar o *squashing*(flag --autosquash).

```bash
$ git checkout develop && git pull

$ git checkout <nova-branch>

$ git rebase -i --autosquash develop
```

Enviamos o resultado do **rebase** após resolver os conflitos.

Caso a *branch* não esteja no *remote*(-u cria a *branch*, -f força a utilização da nova história escrita pelo *rebase*):
```bash
$ git push -uf origin <nova-branch>
```
Caso já esteja:
```bash
$ git push -f
```

Assim resta apenas abrir um *pull request* para a *develop*.

## Cuidados

O rebase pode ser bastante destrutivo, pois ele literalmente reescreve a história da branch destino.

Não faça rebase de uma *branch* ao mesmo tempo que mais pessoas ainda estejam trabalhando nelas.

## Referências

TODO
