# Machine Learning optical spectra from Independent Particle Approximation calculations (ML_IPA)

Code for reproducing the results of Ref. [1], i.e. to predict the frequency-resolved imaginary part of the dielectric function and the real part of the refractive index of a broad class of materials from their crystal structure using data from calculations based on the Independent Particle Approximation.    
Small sections of the graph creation algorithm were adapted from the code published with Ref. [2].

**REQUIREMENTS:** 

The version numbers are the versions that were tested - other versions might work, but success is not guaranteed.
- Python v3.12.2
    - Installed the following packages (plus their dependencies) with miniconda:
        - pytorch v2.3.0 with CUDA v12.1 
        - pytorch_geometric v2.5.3
        - pymatgen v2024.5.1

**USAGE:**
1. Place the downloaded .json files in the "database_100" and "database_300" directories, according to the broadening (specified in the filename of the database).
2. Run the "database_to_graphs.ipynb" notebook to convert the structures stored in the database to graphs. They are stored as .pckl files in the graphs folder. The metadata is stored in the "data" folder.
3. Run the notebook "evaluation.ipynb" to load the models stored in the "models" folder, evaluate them on the test set, and generate the figures shown in Ref. [1].
4. Run the notebook "periodic_table.ipynb" to create the periodic table plots shown in the SM.
5. Optionally, you can verify the correct execution of the training/validation/test split by inspecting the **_set.txt files. The IDs of the materials contained in the splits used to train/validate/test the models in [1] are stored there. The correct execution of the split depends on the seed specified in "evaluation.ipynb", which is identical to the one used in [1].

The data is available at [figshare](https://www.doi.org/10.6084/m9.figshare.27440652).

**REFERENCES:**

[1] M. Grunert, M. Großmann and E. Runge, **Deep learning of spectra: Predicting the dielectric function of semiconductors**, *Phys. Rev. Materials* (2024)
[2] J. Schmidt, L. Pettersson, C. Verdozzi, S. Botti and M. Marques, **Crystal graph attention networks for the predictionof stable materials**, *Sci. Adv.* **7**, eabi7948 (2021)