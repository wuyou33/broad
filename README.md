# Berlin Robust Orientation Estimation Assessment Dataset (BROAD)

This repository contains the data files and example code for the BROAD benchmark for inertial orientation estimation.

For more details, see the following publication:

> D. Laidig, M. Caruso, A. Cereatti, T. Seel. BROAD -- A Benchmark for Robust Inertial Orientation Estimation.
> *Submitted to Data.*

## Repository Contents

This repository includes the following:

- `data_hdf5`: IMU measurement data and OMC ground truth for all trials in HDF5 format.
- `data_mat`: IMU measurement data and OMC ground truth for all trials as Matlab data files.
- `example_code`: Python example code to calculate error metrics, process the data files with two orientation estimation
  algorithms, and re-generate the plots shown in the case study of the publication.
- `example_code/out`: Output generated by the example code (data files and plots).
- `animations`: Videos that visualize the IMU measurement data and performed motion for all trials.

Note that the data stored in `data_hdf5` and `data_mat` is identical.

## Running the Example Code

The example code is written in Python and requires Python (>=3.7), numpy, scipy, Cython and matplotlib. In order to run
the orientation estimation algorithms via Cython, a compatible C++ compiler must be available.

In order to re-create the results presented in the publications,

1. run `process_data.py` to run the orientation estimation algorithms with a parameter grid (possibly with the
   `--force` option if the files in `out/` already exists)
2. run `create_plots.py` to re-create the plots shown in the case study of the publication.

Additionally, the functions provided in `broad_utils.py` can also be used in other scripts, e.g. to calculate the error
metrics defined in the publication.

### Example commands on Linux using a virtual environment

~~~sh
# create virtual environment
python3 -m venv venv
# active the newly created virtual environment
source venv/bin/activate
# install required packages
pip install -r requirements.txt
# run the algorithms with different parameters and calculate errors
./process_data.py -f
# create plots
./create_plots.py
~~~

### Example commands on Windows using Anaconda

1. Install [Anaconda](https://www.anaconda.com/products/individual#Downloads).
2. Download the *Visual Studio Build Tools 2019* installer from <https://visualstudio.microsoft.com/downloads/> and in
   the installer, choose to install the *C++ build tools*.

   *Note:* You can skip this step if you already have the correct MSVC compiler installed. If the compiler is missing or
   not set up correctly, there will be a *"Unable to find vcvarsall.bat"* error message when running `process_data.py`. 

3. Open the *Anaconda Prompt* and use `cd` to navigate to the `example_code` folder
4. Run the following commands:

   ~~~sh
   # run the algorithms with different parameters and calculate errors
   python process_data.py -f
   # create plots
   python create_plots.py
   ~~~

   Alternatively, you can also run the scripts using Spyder or any other IDE.


## License

The BROAD dataset is available under the terms of the Creative Commons BY 4.0 license.

The provided example code is dual-licensed under the MIT license and under CC-BY-4.0. Note that the example code
directory also includes copies of the orientation estimation algorithm code used in the case study, for which no
licensing information is provided by the original authors.

Please see the respective LICENSE files for more details.

## Contact

Daniel Laidig, laidig at control.tu-berlin.de