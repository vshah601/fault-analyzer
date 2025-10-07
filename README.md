# Power System Fault Diagnosis Assistant

This project is a **Power System Fault Diagnosis Assistant** built with Python, Gradio, and OpenAI’s GPT models. It allows engineers or students to input three-phase current readings during a fault and get an analysis of likely fault types along with sequence components calculations.

---

## Features

- Parse and handle complex three-phase currents.
- Compute **sequence components** (I0, I1, I2) of the currents.
- Identify the **type of fault**:
  - Three-phase fault
  - Line-to-line fault
  - Line-to-ground or double-line-to-ground fault
- Stream results interactively using a Gradio interface.
- Provides a structured explanation of fault diagnosis steps.

---

## Architecture and Workflow

1. User inputs current readings (Ia, Ib, Ic) via through the interactive gradio interface.
2. A **system message** guides the GPT to act as an expert power engineer and is fed the user current data plus instructions on how to analyze the currents and how to organize its response.
3. The AI determines which **"tools"** to call: **compute_sequence_components_tool** returns the sequence components given the input currents, and **identify_fault_type_tool** returns the likely fault type given the sequence components.
4. Tool responses and tool calls are added into the **message history** so the GPT can use them in further calculations
5. Output is streamed back to the user. Includes sequence current magnitudes, likely fault type, possible solutions. 
  


## Requirements

- Python 3.10+
- OpenAI API key
