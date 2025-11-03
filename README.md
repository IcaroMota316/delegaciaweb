Delegacia Project

Sistema web para gerenciamento de ocorrências, suspeitos, vítimas, policiais e evidências, desenvolvido em Django.

Visão Geral

O projeto “Delegacia” permite gerenciar:

Policiais

Ocorrências

Vítimas

Suspeitos

Evidências (com upload de imagens)

O sistema possui autenticação de usuários, permitindo apenas usuários logados acessarem as funcionalidades.

Funcionalidades

Usuários

Login, logout e registro de usuários.

Exibição do usuário logado na barra de navegação.

Policiais

Listar, criar, editar e excluir policiais.

Ocorrências

Listar, criar, editar e excluir ocorrências.

Exibição de vítimas, suspeitos e evidências relacionados a cada ocorrência.

Paginação de registros.

Vítimas

Listar, criar, editar e excluir vítimas.

Suspeitos

Listar, criar, editar e excluir suspeitos.

Evidências

Listar, criar, editar e excluir evidências.

Possibilidade de anexar imagens.

Tecnologias Utilizadas

Python 3.11

Django 5.2

SQLite (banco de dados)

Bootstrap 5 (interface)

Estrutura de Pastas
delegacia_project/
│
├─ core/
│  ├─ migrations/
│  ├─ templates/
│  │  └─ core/
│  │     ├─ base.html
│  │     ├─ ocorrencia_list.html
│  │     ├─ suspeito_list.html
│  │     ├─ evidencia_list.html
│  │     ├─ form.html
│  │     └─ confirm_delete.html
│  ├─ forms.py
│  ├─ models.py
│  ├─ urls.py
│  └─ views.py
│
├─ delegacia_project/
│  ├─ settings.py
│  ├─ urls.py
│  └─ wsgi.py
│
└─ manage.py

Instalação

Clone o projeto:

git clone https://github.com/seuusuario/delegacia.git
cd delegacia


Crie e ative o ambiente virtual:

python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux / MacOS
source .venv/bin/activate


Instale as dependências:

pip install -r requirements.txt


Execute as migrations:

python manage.py migrate


Crie um superusuário:

python manage.py createsuperuser


Rode o servidor:

python manage.py runserver

URLs Principais
URL	Nome	Descrição
/	home	Página inicial
/login/	login_usuario	Login de usuário
/logout/	logout	Logout
/registrar/	registrar_usuario	Registrar usuário
/policiais/	listar_policiais	Listar policiais
/policial/novo/	criar_policial	Criar policial
/policial/<id>/editar/	editar_policial	Editar policial
/policial/<id>/excluir/	excluir_policial	Excluir policial
/ocorrencias/	listar_ocorrencias	Listar ocorrências
/ocorrencias/criar/	criar_ocorrencia	Criar ocorrência
/ocorrencias/editar/<id>/	ocorrencia_editar	Editar ocorrência
/ocorrencias/excluir/<id>/	ocorrencia_excluir	Excluir ocorrência
/vitimas/	listar_vitimas	Listar vítimas
/vitima/novo/	criar_vitima	Criar vítima
/vitima/<id>/editar/	editar_vitima	Editar vítima
/vitima/<id>/excluir/	excluir_vitima	Excluir vítima
/suspeitos/	listar_suspeitos	Listar suspeitos
/suspeito/novo/	criar_suspeito	Criar suspeito
/suspeito/<id>/editar/	editar_suspeito	Editar suspeito
/suspeito/<id>/excluir/	excluir_suspeito	Excluir suspeito
/evidencias/	listar_evidencias	Listar evidências
/evidencia/novo/	criar_evidencia	Criar evidência
/evidencia/<id>/editar/	editar_evidencia	Editar evidência
/evidencia/<id>/excluir/	excluir_evidencia	Excluir evidência
Models Principais

Policial

nome

matricula

posto

Ocorrencia

tipo

descricao

data

local

policial_responsavel (FK)

Vitima

nome

idade

ocorrencia (FK)

Suspeito

nome

idade

status

ocorrencia (FK)

Evidencia

descricao

imagem

ocorrencia (FK)

Templates

base.html – Layout base com barra de navegação e blocos para conteúdo.

ocorrencia_list.html – Lista de ocorrências com vítimas, suspeitos e evidências.

suspeito_list.html – Lista de suspeitos.

evidencia_list.html – Lista de evidências com imagens.

form.html – Template genérico para formulários de criação/edição.

confirm_delete.html – Confirmação de exclusão de registros.

Observações

Suspeitos agora podem ser criados sem necessariamente estar vinculados a uma ocorrência, assim como as vítimas.

Logout redireciona corretamente para a página de login.

Todos os formulários usam ModelForm do Django para simplificação.

Sistema suporta paginação em listas grandes de registros.
