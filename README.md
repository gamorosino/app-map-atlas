<h1 align="center">Brain Atlas Mapping</h1>

<p align="center">
  Maps a retinotopic or cortical atlas (Benson14, Wang15, Glasser16 or Rosenke18) onto a FreeSurfer subject with neuropythy and outputs a volumetric parcellation, atlas maps and surface data.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.922"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.922-blue.svg" alt="Run on brainlife.io"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Maps a retinotopic or cortical atlas (Benson14, Wang15, Glasser16 or Rosenke18) onto a FreeSurfer subject with neuropythy and outputs a volumetric parcellation, atlas maps and surface data.**

Runs python -m neuropythy atlas on the FreeSurfer subject, converts the resulting volumes to NIfTI with FreeSurfer mri_convert and attaches a label.json for the chosen atlas. Use it to get visual-area or multimodal cortical labels in subject space without functional data. Requires a FreeSurfer license.

| | |
|---|---|
| **Inputs** | `neuro/freesurfer` · `neuro/anat/t1w` (optional) |
| **Outputs** | `neuro/parcellation/volume` · `neuro/maps` · `neuro/surface/vertices` |
| **Container** | `brainlife/dipy:1.4.1` |
| **Resources** | 2 CPUs · 20 GB memory · 4 h walltime |
| **Requires** | `FREESURFER_LICENSE` |
| **Run it** | [doi.org/10.25663/brainlife.app.922](https://doi.org/10.25663/brainlife.app.922) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `freesurfer` | `neuro/freesurfer` | yes | FreeSurfer subject directory. |
| `reference` | `neuro/anat/t1w` | no | Optional T1w reference image. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `parcellation` | `neuro/parcellation/volume` | Atlas labels as a volumetric parcellation with label.json. |
| `volumes` | `neuro/maps` | Atlas maps (e.g. eccentricity, polar angle for Benson14) as volumes. |
| `surfaces` | `neuro/surface/vertices` | Atlas data on the subject's surface vertices. |

<details>
<summary><b>Parameters</b> (1)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `atlas` | enum | `benson14` | Atlas to map: benson14, wang15, glasser16 or rosenke18. Options: `wang15`, `glasser16`, `rosenke18`, `benson14`. |

</details>

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.922](https://doi.org/10.25663/brainlife.app.922), choose `neuro/freesurfer`, `neuro/anat/t1w` from your project, set the parameters and press **Execute**. The results are saved to your project as `neuro/parcellation/volume`, `neuro/maps`, `neuro/surface/vertices`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlife/dipy:1.4.1`), [`jq`](https://jqlang.github.io/jq/), `FREESURFER_LICENSE`.

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "freesurfer": "/path/to/freesurfer/freesurfer",
       "t1": "/path/to/reference/t1",
       "atlas": "benson14"
   }
   ```

3. Run `./main`.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- Brain Atlas Mapping. brainlife.io App. [doi:10.25663/brainlife.app.922](https://doi.org/10.25663/brainlife.app.922)
- Fischl. FreeSurfer. *NeuroImage* 62:774-781 (2012). [doi:10.1016/j.neuroimage.2012.01.021](https://doi.org/10.1016/j.neuroimage.2012.01.021)
- Garyfallidis et al. Dipy, a library for the analysis of diffusion MRI data. *Frontiers in Neuroinformatics* 8 (2014). [doi:10.3389/fninf.2014.00008](https://doi.org/10.3389/fninf.2014.00008)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

Maintained by [@gamorosino](https://github.com/gamorosino).
