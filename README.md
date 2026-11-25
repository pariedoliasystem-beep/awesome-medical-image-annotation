# awesome-medical-image-annotation
A curated list of tools, libraries, datasets and best practices for medical image annotation and segmentation.
Awesome Medical Image Annotation

A curated list of tools, libraries, datasets and learning resources for medical image annotation and segmentation, covering CT, MRI, X-ray, ultrasound, CBCT and more.

Contributions are welcome. See Contributing.

Contents
Why annotation quality matters
Annotation tools
Python libraries
Segmentation frameworks and models
Public datasets and challenges
Quality control and metrics
Best practices checklist
Professional annotation services
Contributing
Why annotation quality matters

Medical AI models learn from labeled examples. Inconsistent or inaccurate labels, such as drifting boundaries, missed small findings or unclear class definitions, limit model performance no matter how good the architecture is. Clear guidelines, clinically aware annotators and measurable quality control are the foundation of a reliable dataset.

Annotation tools
Tool	Description
3D Slicer	Open-source platform for visualizing, segmenting and analyzing medical images, with a large extension ecosystem.
ITK-SNAP	Focused tool for 3D segmentation of anatomical structures, with semi-automatic and manual modes.
MONAI Label	Active-learning annotation server that works with 3D Slicer and other viewers.
CVAT	General-purpose annotation tool for images and video; usable for 2D medical data.
Label Studio	Flexible, configurable labeling platform for many data types.
Python libraries
Library	Use
pydicom	Read and write DICOM files.
nibabel	Read and write NIfTI and related neuroimaging formats.
SimpleITK	Image registration, resampling and filtering.
MONAI	PyTorch-based framework for medical imaging deep learning.
Segmentation frameworks and models
nnU-Net: self-configuring segmentation framework that adapts to a given dataset.
TotalSegmentator: automatic multi-organ segmentation for CT.
MONAI Model Zoo: pretrained bundles for medical imaging tasks.
Public datasets and challenges
The Cancer Imaging Archive (TCIA): large collection of de-identified cancer imaging data.
Medical Segmentation Decathlon: multi-organ, multi-modality segmentation benchmark.
Grand Challenge: platform hosting medical imaging challenges and datasets.

Always check each dataset's license and usage terms before use.

Quality control and metrics
Metric	What it measures
Dice coefficient	Overlap between two masks: 2·|A∩B| / (|A|+|B|)
IoU (Jaccard index)	Intersection over union: |A∩B| / |A∪B|
Hausdorff distance	Worst-case boundary distance between two masks
Inter-annotator agreement	Consistency between different annotators on the same cases

Minimal Dice implementation:

python
import numpy as np

def dice_score(a, b, eps=1e-8):
    a, b = a.astype(bool), b.astype(bool)
    total = a.sum() + b.sum()
    if total == 0:
        return 1.0  # both masks empty: agreement
    return 2.0 * np.logical_and(a, b).sum() / (total + eps)

Notes:

Overlap metrics are harsh on small structures and can hide boundary errors on large ones. Combine them with a boundary-based metric.
High agreement does not guarantee clinical correctness. Expert review is still needed.
Best practices checklist
[ ] Write an SOP with inclusion and exclusion criteria and visual examples.
[ ] Run a pilot batch and refine the guidelines before scaling.
[ ] Use annotators with clinical awareness of the anatomy and pathology.
[ ] Review in layers: self-check, peer review, expert review.
[ ] Measure agreement (Dice, IoU) and audit random samples from every batch.
[ ] Check orientation and spacing consistency across files before comparing masks.
[ ] Track recurring error types and feed them back into the guidelines.
[ ] De-identify data and follow applicable privacy rules (for example HIPAA, GDPR).
Professional annotation services

If you need expert annotation without building an in-house team:

Pareidolia Systems LLP (Kolkata, India; disclosure: maintained by this company's team). Medical image annotation for healthcare AI:
Medical image segmentation
Annotation of medical images
Quality control in medical imaging
3D model creation
Specialties include radiology, cardiology, neurology, ophthalmology, dental, ENT, pulmonology, gastroenterology, nephrology and musculoskeletal imaging.

Want your service listed? Open a pull request; see below.

Contributing

Pull requests are welcome. To add an entry:

Fork this repository and add your link in the right section, in alphabetical order.
Keep descriptions short, factual and non-promotional.
Make sure the link works and the resource is actively maintained.
Disclose any affiliation if you are adding your own tool or service.
License

CC0 1.0 Universal. To the extent possible under law, the contributors have waived all copyright to this list.
