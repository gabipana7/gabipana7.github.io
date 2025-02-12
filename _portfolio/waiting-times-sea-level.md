---
title: "Waiting times for sea level variations"
excerpt: "Waiting times for sea level variations in the port of Trieste"
header:
  image: /assets/images/port_of_trieste_header_resized.png
  teaser: assets/images/port_of_trieste_header_resized.png
sidebar:
  # - title: "Gabriel"
  #   image: /assets/images/profile-pic.jpeg
  #   image_alt: "logo"
  #   text: "Data Scientist"
  - title: "Tech stack"
    text: "Julia, Python, SQL"
  - title: "Skills"
    text: "Data processing, data acquisition, data cleaning, data visualization, time series analysis, waiting times analysis"
# gallery:
#   - url: /assets/images/unsplash-gallery-image-1.jpg
#     image_path: assets/images/unsplash-gallery-image-1-th.jpg
#     alt: "placeholder image 1"
#   - url: /assets/images/unsplash-gallery-image-2.jpg
#     image_path: assets/images/unsplash-gallery-image-2-th.jpg
#     alt: "placeholder image 2"
#   - url: /assets/images/unsplash-gallery-image-3.jpg
#     image_path: assets/images/unsplash-gallery-image-3-th.jpg
#     alt: "placeholder image 3"
---

This project aims to apply the waiting times algorithm on a sea level dataset

---
Dataset: Sea level measurements in the Port of Trieste https://www.seanoe.org/data/00516/62758/

---
Waiting times algorithm
![Image](https://github.com/user-attachments/assets/77c1fd72-5098-4dbd-b2d2-160d692ca74a)

---
Results:


Parameter dependence of the power-law exponent depending on the waiting times parameter
![Image](https://github.com/user-attachments/assets/ea230ae6-4776-4468-af00-529af5021f99)

Waiting times which are best fitted with a power law
![Image](https://github.com/user-attachments/assets/df0c1ced-f52b-47a1-b070-6c9513d40587)


Transition to an exponential-like distribution of waiting times at high values of the delta parameter (or simply high waiting times)
![Image](https://github.com/user-attachments/assets/97d0c101-6858-4e1b-8748-b6b8ce111612)


### De-trending

We applied a de-trending method by applying a rolling average of 28 days to factor out the influence of the moon on the tides

At low waiting times, the power-law holds
![Image](https://github.com/user-attachments/assets/7961be22-65bb-4f07-a723-c8a3611931c4)

At high waiting times, transition to Pareto-Tsallis
![Image](https://github.com/user-attachments/assets/1cd3907b-cfb8-4c93-9e59-823d176c5730)
![Image](https://github.com/user-attachments/assets/8bd3db9a-bd38-4292-bef2-44cbb94c5d19)

---
This project represents the toolbox support for our scientific article: Waiting times for sea level variations in the Port of Trieste: a computational datadriven study

Cite as:

Gabriel Pană, Paul-Adrian Gogîtă, and Alexandru Nicolin-Żaczek, Waiting times for sea level variations in the Port of Trieste: a computational datadriven study, Romanian Journal of Physics 69, 7-8, 111 (2024), https://doi.org/10.59277/RomJPhys.2024.69.111.