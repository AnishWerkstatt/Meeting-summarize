# Meeting Summary Pipeline

This project is an automated tool designed to transcribe and summarize audio and video recordings from meetings. It leverages powerful transcription engines like **Whisper** and **Faster-Whisper**, and integrates with various Large Language Models (LLMs) such as **Google Gemini**, **OpenAI**, **Anthropic Claude**, **Groq**, and **Replicate** to generate concise summaries.

## Features

-   **Multi-Format Support**: Processes both video and audio files.
-   **Transcription Options**: Supports OpenAI's Whisper and Faster-Whisper for efficient transcription, including local execution with NVIDIA GPU acceleration.
-   **Flexible LLM Integration**: Configure summaries using your preferred LLM provider.
-   **Configurable Output**: Customize output folders and file naming conventions.

## Prerequisites

-   **Python 3.x**: Ensure Python is installed on your system.
-   **FFmpeg**: Required for audio processing. Make sure it's installed and added to your system's PATH.
-   **NVIDIA GPU (Optional)**: Recommended for faster local transcription using CUDA.

## Installation

1.  **Clone the Repository**:
    ```bash
    git clone <repository_url>
    cd Meeting_summary
    ```

2.  **Install Dependencies**:
    Install the required Python packages using pip:
    ```bash
    pip install -r requirements.txt
    ```

    > **Note for NVIDIA GPU Users**: If you wish to use CUDA for acceleration, you may need to install a specific version of PyTorch. Refer to [PyTorch's local installation guide](https://pytorch.org/get-started/locally/) or run:
    ```bash
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
    ```

## Configuration

### 1. API Keys (.env)

Create a `.env` file in the root directory to store your API keys. Add the keys for the services you intend to use:

```env
# Example .env file
GEMINI_API_KEY=your_gemini_key
OPENAI_API_KEY=your_openai_key
ANTHROPIC_API_KEY=your_anthropic_key
REPLICATE_API_TOKEN=your_replicate_token
GROQ_API_KEY=your_groq_key
```

### 2. Settings (config.yaml)

The `config.yaml` file controls the behavior of the pipeline. Key configurations include:

-   **`meeting_recordings_folder`**: Directory where you place input files (default: `meeting_recording_queue/Easy_Voice_Recorder`).
-   **`output_structure`**: Define how output files are organized (e.g., by Date, Summary Type).
-   **`llm`**: Select your provider (`gemini`, `openai`, `anthropic`, etc.) and model parameters.
-   **`transcription_engine`**: Choose between `whisper` or `faster_whisper`.
-   **`whisper` / `faster_whisper`**: specific settings for the chosen engine (model size, device, etc.).

## Usage

1.  **Prepare Input**: Place your meeting video or audio files into the `meeting_recording_queue` folder (or the folder specified in `config.yaml`).

2.  **Run the Pipeline**:
    Execute the main script:
    ```bash
    python main.py
    ```

3.  **Check Results**:
    Once processing is complete, check the `summaries` folder (or your configured output folder) for the generated transcripts and summaries.

## Project Structure

-   `main.py`: Entry point of the application. Orchestrates the processing pipeline.
-   `config.yaml`: Configuration file for all settings.
-   `requirements.txt`: Python dependencies.
-   `Scripts/`: Contains core logic for file processing and configuration handling.
-   `meeting_recording_queue/`: Default input directory for recordings.
-   `summaries/`: Default output directory for results.
