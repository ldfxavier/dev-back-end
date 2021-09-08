# Dev. Back-End

Sua tarefa é construir uma API e banco de dados para a aplicação FILMES.
A aplicação é um simples repositório para gerenciar ferramentas com seus respectivos nomes, links, descrições e tags. 
Utilize um repositório Git (público, de preferência) para versionamento e disponibilização do código.

A aplicação deve ser construída utilizando LARAVEL e MySQL.

## O que será avaliado

Queremos avaliar sua capacidade de desenvolver um back-end para uma aplicação. Serão avaliados:

- Código bem escrito e limpo;
- Quais ferramentas foram usadas, como e porquê, além do seu conhecimento das mesmas;
- Seu conhecimento em banco de dados, requisições HTTP, APIs REST, etc;
- Sua capacidade de se comprometer com o que foi fornecido;

## O mínimo necessário

- Uma aplicação contendo uma API real simples, sem autenticação, que atenda os requisitos descritos abaixo, 
fazendo requisições à um banco de dados para persistência;
- README.md contendo informações básicas do projeto e como executá-lo;

## Bônus

Os seguintes itens não são obrigatórios, mas darão mais valor ao seu trabalho 
(os em negrito são mais significativos para nós)

- Uso de ferramentas externas que facilitem o seu trabalho;
- Cuidados especiais com otimização, padrões, entre outros;
- Migrations ou script para configuração do banco de dados utilizado;
- **Conteinerização da aplicação**;
- **Autenticação e autorização** (**OAuth, JWT**);
- **Deploy em ambientes reais, utilizando serviços de cloud externos (AWS, Heroku, GCP, etc);**

# Requisitos

## 1: Deve haver uma rota para listar todas as ferramentas cadastradas

`GET /tools`

Resposta:

    [
        {
            id: 1, // ou qualquer outro identificador
            title: "Homem de Ferro",
            link: "https://www.imdb.com/title/tt0371746/",
            description: "Depois de ficar preso em uma caverna afegã, o engenheiro multimilionário Tony Stark cria uma armadura única para combater o mal.",
            tags: [
                "Iron man",
                "Marvel",
                "Filmes",
                "Ação"
            ]
        },
        {
            id: 2,
            title: "Capitão América",
            link: "https://www.imdb.com/title/tt0103923/?ref_=fn_al_tt_1",
            description: "Congelado por décadas, o Capitão América é libertado para combater o criminoso "Red Skull".",
            tags: [
                "Capitão América",
                "Marvel",
                "Filmes",
                "Ação"
            ]
        },
        {
            id: 3,
            title: "O Justiceiro",
            link: "https://www.imdb.com/title/tt5675620/?ref_=nv_sr_srsg_0",
            description: "Depois de ser atingido por um raio, Barry Allen acorda de seu coma para descobrir que recebeu o poder da super velocidade, tornando-se o próximo Flash, lutando contra o crime em Central City",
            tags: [
                "O Justiceiro",
                "Marvel",
                "Filmes",
                "Ação"
            ]
        }
    ]

## 2: Deve ser possível filtrar ferramentas utilizando uma busca por tag

`GET /tools?tag=Justiceiro`   (*Justiceiro* é a tag sendo buscada neste exemplo)

Resposta:

    [
        {
            id: 3,
            title: "O Justiceiro",
            link: "https://www.imdb.com/title/tt5675620/?ref_=nv_sr_srsg_0",
            description: "Depois de ser atingido por um raio, Barry Allen acorda de seu coma para descobrir que recebeu o poder da super velocidade, tornando-se o próximo Flash, lutando contra o crime em Central City",
            tags: [
                "O Justiceiro",
                "Marvel",
                "Filmes",
                "Ação"
            ]
        }
    ]

## 3: Deve haver uma rota para cadastrar uma nova ferramenta

O corpo da requisição deve conter as informações da ferramenta a ser cadastrada, sem o ID (gerado automaticamente pelo servidor). A resposta, em caso de sucesso, deve ser o mesmo objeto, com seu novo ID gerado.

`POST /tools
Content-Type: application/json`

    {
        "title": "Capitã Marvel",
        "link": "https://www.imdb.com/title/tt4154664/?ref_=nv_sr_srsg_0",
        "description": "Um piloto da força aérea se torna uma das heróis mais poderosas do universo quando a Terra é capturada no meio de uma guerra galáctica entre duas raças alienígenas",
        "tags":["Capitã Marvel", "Marvel", "Filmes", "Ação"]
    }

Resposta:

`Status: 201 Created`

`Content-Type: application/json`

    {
        "title": "Capitã Marvel",
        "link": "https://www.imdb.com/title/tt4154664/?ref_=nv_sr_srsg_0",
        "description": "Um piloto da força aérea se torna uma das heróis mais poderosas do universo quando a Terra é capturada no meio de uma guerra galáctica entre duas raças alienígenas",
        "tags":["Capitã Marvel", "Marvel", "Filmes", "Ação"],
        "id": 4
    }

## 4: O usuário deve poder remover uma ferramenta por ID

`DELETE /tools/:id`

Resposta:

`Status: 204 No Content`

## Critérios de Aceitação

- A API deve ser real e escrita por você. Ferramentas que criam APIs automaticamente (Loopback, json-server, etc) não são aceitas;
- Todos os requisitos acima devem ser cumpridos, seguindo o padrão de rotas estabelecido;
- Se você julgar necessário, adequado ou quiser deixar a aplicação mais completa (bônus!) você pode adicionar outras rotas, métodos, meios de autenticação com usuários, etc.

---
