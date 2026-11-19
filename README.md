# Massaciuccoli Digital Twin Reactive

## Run the chatbot

Prerequisites: Git, Docker, and Docker Compose (`docker compose`). The system requires a local LLM to generate explanations.

Clone the repository and enter the directory containing the Compose configuration:

```bash
git clone https://github.com/cybprojects65/MassaciuccoliDigitalTwinReactive.git
cd MassaciuccoliDigitalTwinReactive/Massaciuccoli_simulator
```

Start Ollama:

```bash
docker compose up -d ollama
```

Download the language model and embedding model:

```bash
docker exec -it ollama ollama pull llama3.2:3b
docker exec -it ollama ollama pull nomic-embed-text
```

To select a different LLM, edit the model name and server address in `LLM.env`:

```bash
nano LLM.env
```

If you change the model name, pull that model with `docker exec -it ollama ollama pull <model-name>` before starting the application. Use the address that the application container can reach.

Start the chatbot application:

```bash
docker compose up -d ollama massaciuccoli_app
```

To check that the services started, run:

```bash
docker compose ps
docker compose logs -f massaciuccoli_app
```

For a one-off invocation of the application service, use `docker compose run --rm massaciuccoli_app`. This starts a separate container; it is not required after `docker compose up -d` for a continuously running service.
