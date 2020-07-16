# Demonstração para Código Fonte TV

Esse reposiório contém os artefatos usados na demonstração de Ansible Engine (Ansible CLI) como ferramenta de CD complementar ao Ansible Tower (AWX) e GitHub Actions para o vídeo da Código Fonte TV (YouTube).

## Instruções

Como esse repositório faz uso de Git Submodules, ao clonar você precisa usar:

```bash
git clone https://github.com/davivcgarcia/demo-codigofonte.git --recursive
```

### Executando a Aplicação (api + public)

Mais informações [aqui](https://github.com/davivcgarcia/youtube-chapter-extractor/blob/master/README.md).

### Executando Automação Ansible

Para execução local do Ansible, primeiro crie seu inventário, seguindo o modelo abaixo:

```bash
cat <<<EOF > inventory
[frontend]
servidor  ansible_host=192.168.2.30 ansible_user=usuario

[backend]
servidor  ansible_host=192.168.2.30 ansible_user=usuario
EOF
```

E depois execute o playbook de deployment:

```bash
ansible-playbook -i inventory main.yml
```

Caso precise descomissionar a aplicação, execute:

```bash
ansible-playbook -i inventory remove.yml
```

### Executando Workflow

Esse repositório usa um [self-hosted runner]() baseado em `rhel-8`, mas poderia ser usado com o runner nativo (`ubuntu-latest`) sem problemas. A única coisa que precisa ser feita é a reversão do commit #087ef042e565bf0b34d1a0d8562a36a4b3810839.
