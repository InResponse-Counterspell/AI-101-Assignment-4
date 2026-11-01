# AI-101-Assignment-4

User Prompts vs. Internal Prompts & Project Challenges
1. User Prompts vs. Internal Prompts

    User Prompts: These are the high-level instructions, goals, and corrections that you write in the chat interface (e.g., requesting a scatter plot map, asking to remove markdown asterisks, or demanding this prompt summary). They set the overarching objective, scope, and stylistic preferences of the project.
    Internal / API Prompts: These are the precise, structured instruction templates configured inside the Python cells (such as in FU92XCGpuUeD) which format the raw data (like CSV records) into structured prompts for the Gemini API call. They handle payload serialization, prompt wrapping, and direct variable injection.

2. Key Challenges Overcome in This Project

Throughout the construction of this notebook, we resolved several technical constraints to ensure the desired outcome:

    API Rate & Token Limits: Initially, loading the entire raw dataset into a text payload hit the input token limits. We overcame this by using pandas to selectively read and serialize only a clean 100-row sample of the dataset, protecting our token limits while keeping the analytics statistically representative.
    Parsing Model Outputs: Converting natural language markdown tables from model responses into tabular data with raw asterisks (**) was messy. We implemented custom parsing logic to strip formatting characters dynamically and cleanly structure the target parameters as a standard Pandas DataFrame (df_metrics).
    Network Sandbox Isolation: When rendering the spatial scatter plot on a map background, external static map tile services (Mapbox, Wikimedia, and OpenStreetMap APIs) failed with unauthorized, bad request, or lookup errors due to sandbox network limitations. We bypassed this by writing custom geometric vector rendering instructions to construct the landmass of Manhattan, Central Park, and the surrounding water bodies natively within Matplotlib, creating a beautiful, independent, and high-fidelity output image.

