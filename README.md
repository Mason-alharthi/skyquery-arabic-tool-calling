# SkyQuery: Arabic Natural-Language Querying of Aerial Object-Detection Results

NLP course project (KAUST Academy AI Diploma). **Topic 6 (Your Own Project), Option A: fine-tune the project's own model.** The topic is to be agreed with the instructor at registration.

## Project

A small language model (**Qwen3-1.7B**, fine-tuned with a **QLoRA** adapter) turns one Arabic request, in Modern Standard Arabic or Saudi/Gulf dialect, into one structured JSON tool call over stored aerial object-detection results. It may also return a *no-tool* decision or a *clarification* request.

The call is validated against the tool schema and run by read-only SQLite tools. An Arabic Streamlit app with right-to-left layout shows the result. Every number shown comes from the database.

The model reads text only and never processes images. The project does not train or improve the object detector. The detection records come from our Computer Vision course project.

### Tools

| Tool | Purpose |
| --- | --- |
| `count_detections` | Counts detection records, optionally filtered by class, environment and minimum confidence |
| `class_distribution` | Returns the detected object classes and their counts |
| `compare_environments` | Compares detection results between two environments |
| `list_detections` | Returns filtered detection records, up to a result limit |
| `get_image_detections` | Returns the detection records of one image |

Fields, class labels and environment names will be fixed after inspecting the actual CV output files.

## Team

| Member | Role |
| --- | --- |
| Abdulmohsen Alharthi (team leader) | Data, golden test, dataset card |
| Rayan Alsulami | Evaluation, error analysis, safety check, README |
| Abdulelah Alkhamis | Development pilot, QLoRA training, Hugging Face Hub release |
| Ziyad Almutairi | SQLite database, tools, pipeline, Streamlit app |

Each member presents their own part.

## Planned repository layout

```
data/      dataset card, selected training examples, data scripts
golden/    golden test (~100 examples) and annotation guide
scripts/   inspection, data selection, training and evaluation code
docs/      database schema and tool specifications
app/       Streamlit application
```

## Rules we follow

- The golden test is committed here **before** any training. The commit date is the proof.
- No golden test example appears in training data or prompts.
- The untuned model, the fine-tuned model and the full system are evaluated on the same frozen golden test, and results are reported as found.
- Dependencies are pinned, and the README will explain how to run everything from a clean clone.

## Status

Planning. No data, training or results yet.
