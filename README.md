# demo-codigofonte
Demonstração de Ansible com GitHub Actions para o Código Fonte TV (YouTube)

## Execução Manual

Como esse repositório faz uso de Git Submodules, ao clonar você use:

```bash
git clone https://github.com/davivcgarcia/demo-codigofonte.git --recursive
```

### Aplicação (api + public)

Para executar localmente o componente de backend (`api`), faça:

```bash
cd app-src/youtube-chapter-extractor/api
deno run --allow-read --allow-net app.ts
```

Para executar localmente o componente de front-end (`public`), faça:

```bash
cd app-src/youtube-chapter-extractor/public
firefox index.html
```

Ao abrir o navegador, use o link do video abaixo como exemplo:

https://www.youtube.com/watch?v=BvyQ70PVI4s

### Infraestrutura

Para execução local do Ansible, primeiro crie seu inventário, seguindo o modelo abaixo:

```bash
cd infra-src
cat <<<EOF > inventory
[fronend]
servidor1

[backend]
servidor1
EOF
```

E depois execute o playbook de deployment:

```bash
cd infra-src
ansible-playbook -i inventory main.yml
```
