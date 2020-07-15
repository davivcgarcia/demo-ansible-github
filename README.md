# Demonstração para Código Fonte TV

Esse reposiório contém os artefatos usados na demonstração de Ansible Engine (Ansible CLI) como ferramenta de CD complementar ao Ansible Tower (AWX) e GitHub Actions para o vídeo da Código Fonte TV (YouTube).

## Instruções

Como esse repositório faz uso de Git Submodules, ao clonar você precisa usar:

```bash
git clone https://github.com/davivcgarcia/demo-codigofonte.git --recursive
```

### Executando a Aplicação (api + public)

Mais informações [aqui](app-src/README.md).

### Executando Automação Ansible

Para execução local do Ansible, primeiro crie seu inventário, seguindo o modelo abaixo:

```bash
cd infra-src
cat <<<EOF > inventory
[frontend]
servidor  ansible_host=192.168.2.30 ansible_user=usuario

[backend]
servidor  ansible_host=192.168.2.30 ansible_user=usuario
EOF
```

E depois execute o playbook de deployment:

```bash
cd infra-src
ansible-playbook -i inventory main.yml
```
