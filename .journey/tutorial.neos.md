<!--markdownlint-disable MD024 MD033 MD036 MD041 -->
<walkthrough-metadata>
  <meta name="title" content="Build a Travel Helper Agent using ADK on Google Cloud" />
  <meta name="description" content="Learn how to build and run a Travel Helper Agent using the Agent Development Kit (ADK) directly in Google Cloud Shell." />
  <meta name="keywords" content="ADK, AI, Agents, Google Cloud, Cloud Shell, Vertex AI, Travel Agent" />
</walkthrough-metadata>

# Build a Travel Helper Agent using ADK on Google Cloud

## Let's get started

![Tutorial header image](https://raw.githubusercontent.com/NucleusEngineering/serverless/main/.images/run.jpg)

Welcome! In this tutorial, you will learn how to build and run a **Travel Helper Agent** using the Agent Development Kit (ADK) directly in **Google Cloud Shell**. This guide is perfect for developers who want to explore building AI agents using Google Cloud's powerful tools.

This AI agent helps plan trips by gathering information like visa rules, weather, and currency exchange rates by orchestrating a team of specialized sub-agents.

<walkthrough-tutorial-difficulty difficulty="3"></walkthrough-tutorial-difficulty>

Estimated time:
<walkthrough-tutorial-duration duration="30"></walkthrough-tutorial-duration>

To get started, click **Start**.

## Project Setup

First, make sure you have the correct Google Cloud project selected for building your agent.

<walkthrough-project-setup billing="true"></walkthrough-project-setup>

Next, enable the required Google APIs for this tutorial. We need the Vertex AI API to power our agent's intelligence.

<walkthrough-enable-apis apis="aiplatform.googleapis.com"></walkthrough-enable-apis>

## Clone the Repository

We need to clone the repository containing the Travel Helper Agent code built with ADK.

Run the following command in your Cloud Shell to clone the repository and navigate into the project directory:

```bash
git clone https://github.com/alper-sari/bwai-ramadan-03.git
cd adk-demos
```

## Set Up Your Development Environment

We will create a Python virtual environment to keep our ADK tools and dependencies organized.

Run the following commands to create and activate a virtual environment, then install the required Agent Development Kit (ADK) packages:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Configure the Agent

The ADK framework requires access to Vertex AI models and needs your project details to initialize the agent correctly.

Create your `.env` file by copying the provided template:

```bash
cp dotenv .env
```

Now, edit the file to insert your Project ID:

```bash
nano .env
```

Inside the editor, update the file to include your Project ID. It should look like this:

```env
GOOGLE_GENAI_USE_VERTEXAI=TRUE
GOOGLE_CLOUD_PROJECT=YOUR_PROJECT_ID
GOOGLE_CLOUD_LOCATION=us-central1
```

*Tip: To save and exit nano, press `Ctrl+O`, `Enter`, and then `Ctrl+X`.*

## Run the Travel Helper Agent

The Travel Helper is a "Root Agent" built with ADK that orchestrates multiple sub-agents (for searching the web, checking weather, and converting currency). You can interact with your newly built agent in two ways.

### Option 1: Chat in the Terminal (CLI)

Use the `adk run` command to start a text-based chat right in your terminal:

```bash
adk run ./travel_helper
```

*Try asking: "Hi, I'm from Turkey and I'm traveling from Istanbul to Berlin. Can you help me plan?"*

### Option 2: Use the Web Interface (Port Forwarding)

Cloud Shell allows you to preview web applications running on specific ports. The ADK comes with a built-in web UI. Let's run the agent on **port 8000**.

1. Start the web UI:
   ```bash
   adk web --port 8000
   ```

2. **Preview the Application:**
   * Click the **Web Preview** button (an eye icon) in the Cloud Shell toolbar.
   * Select **Change port**.
   * Type `8000` and click **Change and Preview**.
   * A new browser tab will open. Select your agent from the list and start chatting!

## Summary

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

You have successfully:
- Set up an AI development environment in Cloud Shell.
- Enabled the Vertex AI API for your project.
- Configured your environment to use Google Cloud models.
- Used the Agent Development Kit (ADK) to run a multi-agent system.
- Interacted with your Travel Helper Agent via CLI and Web UI.

<walkthrough-inline-feedback></walkthrough-inline-feedback>

## Clean up

To avoid cluttering your Cloud Shell environment, you can deactivate your virtual environment and delete the cloned repository if you no longer need them.

```bash
deactivate
cd ..
rm -rf adk-demos
```
