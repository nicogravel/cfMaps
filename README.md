# Optimization Strategies in Connective Field Mapping


*Benchmarks for different modelling procedures in cortical connective field (CF) mapping.*

Here we compare four flavors of population cortico-cortical connective field (CF) modeling. First, the former implementation in `mrVista` (using Matlab's `lscov`) which implemented a grid search approach [1,2]. Without further optimization, the parameter space revealed by this implementation matches predefined grid value predictions. Second, the implementation part of the *connective field* branch of the [prfpy](https://github.com/VU-Cog-Sci/prfpy) Python package [3]. Using Python scikit-learn optimization functions (implemented as part of the `prfpy` package), the parameter space `prfpy` provides also converges to predefined grid, although at a much faster rate (thanks to the CPU parallelization tool `joblib`). Third, a custom version of more recent CF modelling approach (by So-Hyeon et al. (2024) [4]) that implements a *derivative-free* parameter (CF size) refinement approach ([see here](https://nicogravel.github.io/cfMaps/html/cfmap.html#cfmap.CF_mapping.optimize_connfield_dfree)). Fourth, our custom Python implementation of *automatic differentiation*-powered [gradient descent](https://en.wikipedia.org/wiki/Gradient_descent) using `TensorFlow` and CUDA (partly inspired by the recent Python package [braincoder](https://braincoder-devs.github.io/) [5]) to achieve highly efficient gradient descent ([see here](https://nicogravel.github.io/cfMaps/html/cfmap.html#cfmap.CF_mapping.optimize_connfield_gdescent) and [here](https://nicogravel.github.io/cfMaps/html/cfmap.html#cfmap.CF_mapping.optimize_connfield_joint) for a joint optimization approach that optimizes both CF size and position). To coordinate this effort, we rely on widely used population receptive field mapping tools [6,7] and high-field 7T-MRI retinotopy data kindly made available by [NeuroSpin](https://joliot.cea.fr/drf/joliot/en/Pages/research_entities/NeuroSpin.aspx).

## Documentation

Please have a look [here](https://nicogravel.github.io/cfMaps/) for installation instructions, tutorials, and examples.


## How to cite 

If you use this code please cite using the following information:

Gravel, N., Zhan M., Renken, R., & Cornelissen, F. W. (2025). Optimization strategies in cortical connective field mapping. Zenodo. https://doi.org/10.5281/zenodo.17373320

Alternatively, use this BibTeX entry:

```bibtex
@misc{Gravel_optCF_2025,
  author       = {Gravel, Nicol{\'a}s and Renken, Remco and Cornelissen, Frans W},
  title        = {Optimization strategies in cortical connective field mapping},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.17373320},
  url          = {https://doi.org/10.5281/zenodo.17373320}
}
```

## References

[1] Haak, K. V., Winawer, J., Harvey, B. M., Renken, R., Dumoulin, S. O., Wandell, B. A., & Cornelissen, F. W. (2013). Connective field modeling. *NeuroImage*, 66, 376-384. https://doi.org/10.1016/j.neuroimage.2012.10.037

[2] Gravel, N., Harvey, B., Nordhjem, B., Haak, K. V., Dumoulin, S. O., Renken, R., Ćurčić-Blake, B., & Cornelissen, F. W. (2014). Cortical connective field estimates from resting state fMRI activity. *Front. Neurosci.*, 8, 339. https://doi.org/10.3389/fnins.2014.00339

[3] Knapen, T. (2021). Topographic connectivity reveals task-dependent retinotopic processing throughout the human brain. *Proceedings of the National Academy of Sciences*, 118(2), e2017032118. https://doi.org/10.1073/pnas.2017032118

[4] Yoo, S.-H., Kieslinger, A.-S., & Skeide, M. A. (2024). Population connective field modeling reveals proto-retinotopic visual cortex organization in the prenatal human brain. *bioRxiv*. https://doi.org/10.1101/2024.07.08.602507

[5] de Hollander, G., Renkert, M., Ruff, C. C., & Knapen, T. H. (2024). braincoder: A package for fitting encoding models to neural data and decoding stimulus features [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.10778413

[6] Dumoulin, S. O., & Wandell, B. A. (2008). Population receptive field estimates in human visual cortex. *NeuroImage*, 39(2), 647-660. https://doi.org/10.1016/j.neuroimage.2007.09.034

[7] Benson, N. C., Jamison, K. W., Arcaro, M. J., Vu, A. T., Glasser, M. F., Coalson, T. S., Van Essen, D. C., Yacoub, E., Ugurbil, K., Winawer, J., & Kay, K. (2018). The Human Connectome Project 7 Tesla retinotopy dataset: Description and population receptive field analysis. *Journal of Vision*, 18(13), 23. https://doi.org/10.1167/18.13.23