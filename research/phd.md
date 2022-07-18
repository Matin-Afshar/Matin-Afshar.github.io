---
layout: page
title: My PhD Project
tags: child
---

* **Title**: Mathematical and Computational Modeling of Biodegradation Behavior of Personalized Printed Implants

* **Summary**: Beside mechanical functionality and stability, biodegradation plays an important role in implant design and optimization. In this project, we will develop a 3D mathematical model of biodegradation of printed implants, which provides a framework for assessment of degradation and corrosion of implants in bioreactor (in-vitro) and body (in-vivo) environments. In addition, chemical and biological interaction of the implant with the bioreactor environment will be modeled. The mathematical models will be simulated using proper numerical schemes. The developed code will be linked with structure optimization models to obtain more accurate predictions of the implant behavior over time.

* **Glimpse into the results**: The following visualization is a typical output of simulations that I perform using the model I have developed (it's an interactive ParaView Glance session, so you can explore it using your mouse buttons and modify it using the panel on the left).

<script>
    var app = "https://kitware.github.io/paraview-glance/app";
    var datadir = "https://raw.githubusercontent.com/mbarzegary/datasets-and-scenes/main/";
    var file = "degrading_screw.vtkjs";

    document.write("<iframe src='" + app + "?name=" + file + "&url=" +datadir + file + "' id='iframe' width='1100' height='900'></iframe>");
</script>