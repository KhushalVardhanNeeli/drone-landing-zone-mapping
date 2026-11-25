# Drone landing zone mapping

Given an overhead photograph and a target pixel, the program searches for a nearby patch that can fit a delivery footprint. It labels the terrain, estimates relative depth, and ranks candidate patches by distance, roughness, and the terrain penalties for the mission. The result is a proposed location drawn on the image.

## Follow one image through the code

1. [main.py](src/main.py) loads the image and models.
2. [geometry.py](src/geometry.py) searches candidate footprints. [semantic_brain.py](src/semantic_brain.py) interprets the mission settings.
3. [utils.py](src/utils.py) draws the result and analysis panels.

## Run an evaluation

From the repository root, install the dependencies. Run the Python scripts from `src` so their relative paths resolve.

```sh
python -m pip install -r requirements.txt
cd src
python main.py path/to/aerial-image.jpg 400 300
```

Replace the image path and coordinates with a pixel in your image. Inference requires `best_model.pth` in the working directory and the MiDaS depth model. For training, extract the TU Graz Semantic Drone Dataset under `semantic_drone_dataset/` at the repository root, then run `python split_data.py` and `python train.py` from `src`. Check the paths in [the split script](src/split_data.py) before starting.

## Project credits

BITS Pilani Hyderabad, CS F407 Artificial Intelligence, Assignment II. Team members were Anurag Padhy (lead), Khushal Vardhan Neeli, and Harshit Verma.
