# [KitchenTwin: Semantically and Geometrically Grounded 3D Kitchen Digital Twins]

---

## Abstract
Embodied AI training and evaluation require object-centric digital twin environments with accurate metric geometry and semantic grounding. Recent transformer-based feedforward reconstruction methods can efficiently predict global point clouds from sparse monocular videos, yet these geometries suffer from inherent scale ambiguity and inconsistent coordinate conventions. This mismatch prevents the reliable fusion of these dimensionless point cloud predictions with locally reconstructed object meshes. We propose a novel scale-aware 3D fusion framework that registers visually grounded object meshes with transformer-predicted global point clouds to construct metrically consistent digital twins. Our method introduces a Vision-Language Model (VLM)-guided geometric anchor mechanism that resolves this fundamental coordinate mismatch by recovering an accurate real-world metric scale. To fuse these networks, we propose a geometry-aware registration pipeline that explicitly enforces physical plausibility through gravity-aligned vertical estimation, Manhattan-world structural constraints, and collision-free local refinement. Experiments on real indoor kitchen environments demonstrate improved cross-network object alignment and geometric consistency for downstream tasks, including multi-primitive fitting and metric measurement. We additionally introduce an open-source indoor digital twin dataset with metrically scaled scenes and semantically grounded and registered object-centric mesh annotations.

---

## Pipeline
The following is the overall architecture diagram of this system:

![Pipeline Image](./assets/pipeline.png)
*Figure 1: System Pipeline Diagram, illustrating the entire process from image input to digital twin model output.*

---

## Results

### 1. Visulization
![Results Image](./assets/results.png)
*Qualitative comparison of the assembled 3D digital twin. Left: The baseline fails to establish a metric space, resulting in floating, unscaled, and overlapping artifacts. Right: With geometric grounding, our method produces a physically plausible, Manhattan-aligned, and tightly registered object-centric scene without subsurface penetration.*

### 2. Data results
2.1 IoU Quantitative Comparison
Qualitative comparison of the assembled 3D digital twin. Left: The baseline fails to establish a metric space, resulting in floating, unscaled, and overlapping artifacts. Right: With geometric grounding, our method produces a physically plausible, Manhattan-aligned, and tightly registered object-centric scene without subsurface penetration.

|Method|Bottle 1|Fridge|Coffee M.|Cab. 1|DishW.|Coffee|Cab. 2|Stool|Cab. 3|Oven|Bottle 2|Cab. 4|mIoU ↑|
|SAM3D|0.0000|0.0000|0.0000|0.0000|0.2943|0.0000|0.0001|0.0000|0.0000|0.0000|0.0014|0.0000|0.0246|
|Ours|0.6321|0.6205|0.5751|0.1502|0.3979|0.7519|0.3079|0.6743|0.7798|0.5842|0.7283|0.6562|0.5715|

2.2 Geometric Registration & Mesh Complexity
Geometric registration metrics and mesh complexity. We report the TrICP Root Mean Square Error (RMSE), SAM3D-to-World Scale Factor (s), and topological complexity (Vertices and Faces) of the generated meshes for all 12 tracked objects in the scene.
Object,RMSE (m) ↓,Scale (s),Vertices,Faces
Bottle 1,0.0165,0.24,"3,970","7,028"
Bottle 2,0.0461,0.25,"5,156","9,058"
Coffee Maker,0.0482,0.43,"2,658","4,490"
Coffee,0.0910,0.43,"6,016","10,336"
Cabinet 3,0.1637,0.69,"4,165","7,054"
Step Stool,0.1699,0.45,"27,366","35,710"
Stove/Oven,0.1780,0.85,"37,162","56,524"
Cabinet 4,0.2072,0.84,"4,377","7,652"
Cabinet 2,0.2440,2.10,"5,618","8,594"
Fridge,0.3252,1.47,"2,439","4,554"
Dishwasher,0.3264,0.77,"10,303","17,975"
Cabinet 1,0.3657,1.25,"8,762","14,270"


---

Code will come soon
