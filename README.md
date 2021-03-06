# Demonstração de Ansible Engine (CLI) com GitHub Actions

Esse repositório contém os artefatos usados na demonstração de Ansible Engine (Ansible CLI) como camada de automação de deployment (Continuous Deployment - CD) integrado a um fluxo de GitHub Actions.

Para exemplificar a aplicação, estamos usando um fork do código desenvolvido pela [Código Fonte TV](https://www.youtube.com/user/codigofontetv) no [episódio #34](https://www.youtube.com/watch?v=ooLEpm4CXBY) escrito em JavaScript (frontend) e Deno (backend).

## Instruções

Como esse repositório faz uso de Git Submodules, ao clonar você precisa usar:

```bash
git clone https://github.com/davivcgarcia/demo-ansible-github.git --recursive
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

E depois execute o playbook de implantação e depois o de validação:

```bash
ansible-playbook -i inventory playbook_deploy.yml
ansible-playbook -i inventory playbook_verify.yml
```

Caso precise descomissionar a aplicação, execute:

```bash
ansible-playbook -i inventory playbook_remove.yml
```

### Executando Workflow

Ao clonar esse repositório é esperado que os fluxos de Continuous Integration (CI) funcionem sem nenhum tipo de modificação. Já para o de Continuous Deployment (CD), basta configurar os seguintes secrets:

- **SSH_PRIVATE_KEY**: Conteúdo da chave privada de SSH para acessar o servidor externo.
- **INVENTORY**: Conteúdo do arquivo de inventário (mesmo formato usado na execução manual)

Caso tenha alguma dificuldade, por favor reporte problema que eu tento ajudar! =D
