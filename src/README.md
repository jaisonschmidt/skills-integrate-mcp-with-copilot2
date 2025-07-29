# API de Atividades da Academia Excellence

Uma aplicação FastAPI que permite aos estudantes visualizar e se inscrever em atividades extracurriculares da Academia Excellence.

## Funcionalidades

- Visualizar todas as atividades extracurriculares disponíveis
- Inscrever-se e cancelar inscrições em atividades
- **Personalização do título da escola** - Sistema configurável para nome, subtítulo e informações da instituição
- Interface responsiva em português brasileiro

## Primeiros Passos

1. Instale as dependências:

   ```
   pip install fastapi uvicorn
   ```

2. Execute a aplicação:

   ```
   python app.py
   ```

3. Abra seu navegador e vá para:
   - Aplicação principal: http://localhost:8000
   - Documentação da API: http://localhost:8000/docs
   - Documentação alternativa: http://localhost:8000/redoc

## Endpoints da API

| Método | Endpoint                                                          | Descrição                                                           |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Obter todas as atividades com seus detalhes e contagem atual de participantes |
| POST   | `/activities/{activity_name}/signup?email=student@academiaexcellence.edu` | Inscrever-se em uma atividade                                       |
| DELETE | `/activities/{activity_name}/unregister?email=student@academiaexcellence.edu` | Cancelar inscrição em uma atividade                                |
| GET    | `/api/school-info`                                               | **NOVO**: Obter informações da escola (nome, ano, subtítulo, etc.) |
| PUT    | `/api/school-info`                                               | **NOVO**: Atualizar informações da escola                          |

## Personalização da Escola

A aplicação agora suporta personalização completa das informações da escola através do endpoint `/api/school-info`:

- **Nome da escola**: Exibido no cabeçalho e título da página
- **Subtítulo**: Mostrado abaixo do nome principal
- **Ano**: Usado no rodapé
- **Descrição**: Informações adicionais sobre a instituição
- **Website**: Link para o site oficial

### Configuração Atual
- **Nome**: Academia Excellence (anteriormente Mergington High School)
- **Domínio de email**: academiaexcellence.edu
- **Interface**: Português brasileiro

## Modelo de Dados

A aplicação usa um modelo de dados simples com identificadores significativos:

1. **Atividades** - Usa o nome da atividade como identificador:
   - Descrição
   - Cronograma
   - Número máximo de participantes permitidos
   - Lista de emails de estudantes que estão inscritos

2. **Estudantes** - Usa email como identificador:
   - Nome
   - Nível da série

3. **Informações da Escola** - Configuração centralizadas:
   - Nome da instituição
   - Ano acadêmico
   - Subtítulo/slogan
   - Descrição institucional
   - Website oficial

Todos os dados são armazenados na memória, o que significa que os dados serão resetados quando o servidor reiniciar.
