# Pytorch_benchmark

## Saving Data To Disk
To run the benchmark, first you have to run the data_saver.py with the following:
```
python data_saver.py --DATA_SAVE_FOLDER <location where you want to save your data>
```

Other options are:
```
--NUM_SAMPLES   Default is 8 * (5 + 50) = Batch Size * (Warm-up Rounds + Sample Size)
```

## Running the benchmark:
Once the data is saved, you can move on to run benchmark_models.py by running the following:
```
python benchmark_models.py --SAVED_DATA_FOLDER <location where you saved your data> --RESULT_SAVE_FOLDER <location where you want to save your results>
```
Currently only VGG and MOBILENET are enabled - you can uncomment the others depending on the hardware performance.
Other options are:
```
--BATCH_SIZE    The default batch size is 4. Change it to fit the hardware capacity.
--NUM_CLASSES   Number of classes to predict
--WARM-UP       Number of warm-up rounds before we start collecting training/inference durations
```
## Install and Example

```
git clone https://github.com/NGDSystems/NGD_CSD_benchmarking.git
cd NGD_CSD_benchmarking
mkdir data
mkdir results
source ./env.sh
python data_saver.py --DATA_SAVE_FOLDER data
python benchmark_models.py --SAVED_DATA_FOLDER data --RESULT_SAVE_FOLDER results
```

## OpenBLAS Warning : Detect OpenMP Loop and this application may hang. Please rebuild the library with USE_OPENMP=1 option.
To solve the OpenBLAS Warning, I have provided a shell script "env.sh".

```
cd NGD_CSD_benchmarking
source ./env.sh
python benchmark_models.py --SAVED_DATA_FOLDER data --RESULT_SAVE_FOLDER results
```


