# Azure Translator Jupyter Project  

This repository contains a Jupyter notebook demonstrating how to call the Azure Translator Text API from a Jupyter environment running on an Azure Machine Learning compute instance.  

## Overview  

The notebook shows how to import the `azure-ai-translation-text` SDK, configure a client with environment variables, and translate a sample string. Secrets (keys and endpoints) are read from environment variables rather than being hard‑coded in the notebook.  

## Challenges Encountered  

While setting up this project, I ran into a couple of issues:  

- **Environment variable visibility** – When running the notebook on an Azure ML compute instance, environment variables exported in the terminal aren’t automatically visible to an already running Jupyter kernel. The solution was to restart the Jupyter server after exporting the variables (or add them to the instance’s `~/.bashrc`). I avoided hard‑coding any keys in the notebook; instead, I set `AZURE_TRANSLATOR_KEY` and `AZURE_TRANSLATOR_REGION` in the terminal.  

- **Notebook server errors** – At one point, the JupyterLab session displayed a “Server Connection Error” with a 500 status code from the `notebook-instance-proxy`. This turned out to be a transient issue with Azure ML’s notebook proxy. Restarting (or stopping and starting) the compute instance resolved the error.  

These notes are captured in the README to document the troubleshooting steps.  

## Next Steps  

You can explore the notebook (`translator.ipynb`) to see the working example. To reuse this code, set your own Azure Translator key and region as environment variables before launching Jupyter. 
