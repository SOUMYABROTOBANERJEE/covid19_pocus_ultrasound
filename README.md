# Automatic Detection of COVID-19 from *Ultrasound* Data

We develop a **computer vision** approach for the diagnosis of **COVID-19** infections
from **Point-of-care Ultrasound** (POCUS) recordings. Find the arXiv preprint
[here](https://arxiv.org/abs/2004.12084). This is the **first
approach to automatically detect COVID-19 from ultrasound**. Next to the code
for our model and our [website (https://pocovidscreen.org)](https://pocovidscreen.org), we also make a
**dataset**
available. This complements the current data collection initiaves that only focus
on CT or X-Ray data. The data includes a total of ~60 videos (> 1000 images) of COVID 19 patients, as well
as pneumonia and healthy lungs. 
**Please help growing the database!**


## Motivation:
From the machine learning community, ultrasound has not gained much attention in the context of COVID-19 so far, in contrast to CT and X-Ray scanning.
Many voices from the medical community, however, have advocated for a more prominent role of ultrasound in the current pandemic.
#### Why imaging?
Biomedical imaging has the potential to complement conventional diagnostic procedures for COVID (such as RT-PCR or immuno assays). It can provide a fast assessment and guide downstream diagnostic tests, in particular in triage situations. In the current pandemic, prognostic predictions were already shown to help saving the scarce time of doctors by reducting the time spent to make the right decision [(Shan et. al., 2020)](https://arxiv.org/abs/2003.04655).
Two studies reported that CT imaging can detect COVID-19 at higher sensitivity rate compared to RT-PCR (98% vs 71%, [Fang et. al., 2020](https://pubs.rsna.org/doi/full/10.1148/radiol.2020200432) and 88% vs. 59% [Ai et. al., 2020](https://pubs.rsna.org/doi/full/10.1148/radiol.2020200642)).
#### Why ultrasound?
However, ultrasound data was shown to be highly
[**correlated with CT**](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7165267/), the gold standard for lung diseases. Instead of CT,
ultrasound is **non-invasive**, **cheap**, **portable** (bedside execution),
**repeatable** and **available in almost all medical facilities**. But even for
trained doctors detecting COVID-19 from ultrasound data is challenging and
time-consuming. Since their time is scarce, there is an urgent need to simplify,
fasten & automatize the detection of COVID-19.

This project is a **proof of concept**, showing that a CNN is able to learn to distinguish between COVID-19,
Pneumonia and healthy patients with an **accuracy of 89%** and **sensitivity for
COVID of 96\%**.

### Evidence for ultrasound
   - Peer-reviewed publications from the medical community suggesting to use more **ultrasound
     for COVID-19**:
      - ["COVID-19 outbreak: less stethoscope, more ultrasound" in *The Lancet
        respiratory medicine* (IF:
        22)](https://www.thelancet.com/journals/lanres/article/PIIS2213-2600(20)30120-X/fulltext?fbclid=IwAR2kDbxpYTSjoj3Nl_B-nOhLZL66mQLUBVBCdzn6zEG5ObLKq9oXhPZDXHQ)
      - [[Smith et. al., 2020] in *Anaesthesia*](https://onlinelibrary.wiley.com/doi/abs/10.1111/anae.15082)
      - [[Sofia et. al., 2020] *Journal of
        Ultrasound*](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7159975/)
      - [[Soldati et. al., 2020] in *Journal of ultrasound in medicine*](https://onlinelibrary.wiley.com/doi/full/10.1002/jum.15284)
   - Ultrasound can evidence the same symptoms as CT: ([Point-by-point correspondance of CT
     and ultrasound findings through COVID-19 disease process](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7165267/)) 
   - [NIH launched an initiative to use POCUS for risk stratificaton of COVID-19
     patients.](https://clinicaltrials.gov/ct2/show/NCT04338100)
   - [**Read our full paper**](https://arxiv.org/abs/2004.12084)

<p align="center">
	<img src="pocovidnet/plots/overview.png" alt="photo not available" width="70%" height="70%">
	<br>
   <em>Example lung ultrasound images. (A): A typical COVID-19 infected lung, showing small subpleural consolidation and pleural irregularities. (B): A pneumonia infected lung, with dynamic air bronchograms surrounded by alveolar consolidation. (C) Healthy lung. 
The lung is normally aerated with horizontal A-lines.</em>
</p>


## Contribute!
- You can donate your lung ultrasound recordings directly on our website: [](https://pocovidscreen.org)
- Please help us to find more data! Open an
  [issue](https://github.com/jannisborn/covid19_pocus_ultrasound/issues) if you
  identified a promising data source. Please check [here](https://docs.google.com/spreadsheets/d/1t-tLMjMod6W-nAjkuxmO0CLsiyalFIOp92k_XD_yeo8/edit#gid=1181682638) whether the data is
  already included. Useful contributions are:
   - Publications with ultrasound images/videos
   - Images/Videos that are available via Creative Commens license (e.g. CC
     BY-NC-SA) in the web or on YouTube.
   - Possible sources are:
      - https://thepocusatlas.com
      - https://radiopaedia.org/
      - https://grepmed.com 
- We are mostly looking for *healthy* lung recordings (at the moment we have *more* data for COVID than for healthy
  lungs)


## Learn more about the project

- [arXiv Paper](https://arxiv.org/abs/2004.12084)
- Web Interface ([https://pocovidscreen.org](https://pocovidscreen.org))
- [DevPost](https://devpost.com/software/automatic-detection-of-covid-19-from-pocus-ultrasound-data)   
- Watch this [video](https://www.youtube.com/watch?v=1hJaVLGvzng) (2min pitch)

## Infrastructure
<img src=".ddev/doc/pocovidscreen_arch.png" width="600"/>

### Screening process
<img src=".ddev/doc/screen_process.png" width="600"/>

## Installation

To get more information about how to train the model with the dataset check inside the [pocovidnet](pocovidnet/README.md)
folder.

To use the trained model with our web application *locally* follow those steps :

- Clone the repo
- Start the containers with [ddev](https://ddev.readthedocs.io/en/stable/) (will automatically install composer dependencies)

```bash
ddev start
```

- Install npm dependencies

```bash
cd pocovidscreen 
npm install
```

- Copy .env.example to .env

```bash
cp .env.example .env
```

- Generate app key

```bash
ddev exec php artisan key:generate
```

- Run database migration

```bash
ddev exec php artisan migrate:fresh
```

- Generate JWT secret

```bash
ddev exec php artisan jwt:secret
```

- Start npm watcher to start coding
```bash
npm run watch
```

- Or run a build for production
```bash
npm run prod
```

- Visit https://covidscreen.ddev.site/

## Contact 
- If you experience problems with the code, please open an
[issue](https://github.com/jannisborn/covid19_pocus_ultrasound/issues).
- If you have questions about the project, please reach out: `jborn@ethz.ch`.


## Citation
The paper is available [here](https://arxiv.org/abs/2004.12084).

If you build upon our work or find it useful, please cite our paper:
```bib
@article{born2020pocovidnet,
    title={POCOVID-Net: Automatic Detection of COVID-19 From a New Lung Ultrasound Imaging Dataset (POCUS)},
    author={Jannis Born and Gabriel Brändle and Manuel Cossio and Marion Disdier and Julie Goulet and Jérémie Roulin and Nina Wiedemann},
    year={2020},
    eprint={2004.12084},
    archivePrefix={arXiv},
    primaryClass={eess.IV}
}
```
