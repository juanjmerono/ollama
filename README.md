# Trying Ollama

This is a simple test using different LLM models locally, are you ready to stress your computer?

```
docker-compose up -d
```

Go to test using web UIs, if you want to do everything via Web UI

## Download models manually

You have to download some models the first time you run ollama, with these commands:

```
docker-compose exec ollama ollama pull mistral
docker-compose exec ollama ollama pull llama2
docker-compose exec ollama ollama pull codellama:7b
```

You can also check [ollama model library](https://ollama.ai/library) to find appropiate model to test.

## Create custom models manually

You can create custom models based on previous ones, using some Modelfile's:

```
docker-compose exec ollama ollama create spanish-llama2 -f /custom/models/Modelfile-spanish
docker-compose exec ollama ollama create sentiments-mistral -f /custom/models/Modelfile-sentiments
docker-compose exec ollama ollama create devops-mistral -f /custom/models/Modelfile-devops
docker-compose exec ollama ollama create java-codellama -f /custom/models/Modelfile-java
docker-compose restart
```

# Test using Web UIs

## Ollama Web UI [ollama-webui](https://github.com/ollama-webui/ollama-webui)

Fully functional web UI, you can test, download and custimize models using this UI:

http://localhost:8080/

## Chatbot Ollama [chatbot-ollama](https://github.com/ivanfioravanti/chatbot-ollama)

You can test models previously downloaded or generated manually or via Web UI

http://localhost:3000/

## Talk to your documents [fully-local-pdf-chatbot](https://github.com/jacoblee93/fully-local-pdf-chatbot)

You can also have some conversations against PDF documents using this web app:

https://webml-demo.vercel.app/

The information you upload will never leave your browser, it will be processed inside the browser, and you will connect to your local running instance of ollama to ask mistral model about the content of the PDF, so you can potentially run without internet connection, after the web app is loaded !

# Stop the environment

To stop the environment:

```
docker-compose down -v
```

You can remove models tested inside .ollama folder.

# Test models in a simple console:

You could also test any of the models in a single console, you must run docker-compose to download the model first.
Now you can stop the environment and use the models located in the volume to test it directly:

```
docker run --rm -d -e OLLAMA_MODELS=/ollama/models -v ${PWD}/models:/ollama/models --name ollama ollama/ollama
docker exec -it ollama ollama run llama2
docker stop ollama
```
