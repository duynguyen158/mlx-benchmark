# ⚡️ mlx-benchmark ⚡️

Results on a 64 GB MacBook Pro M3 Max:

```zsh
Running benchmarks on mlx_gpu (1/5)
100%|██████████████████████████████████████████████████████████████████| 85/85 [00:21<00:00,  4.04it/s]

Running benchmarks on mlx_gpu_compile (2/5)
100%|██████████████████████████████████████████████████████████████████| 85/85 [00:19<00:00,  4.38it/s]

Running benchmarks on mlx_cpu (3/5)
100%|██████████████████████████████████████████████████████████████████| 85/85 [03:42<00:00,  2.61s/it]

Running benchmarks on mps (4/5)
100%|██████████████████████████████████████████████████████████████████| 85/85 [10:33<00:00,  7.46s/it]

Running benchmarks on cpu (5/5)
100%|██████████████████████████████████████████████████████████████████| 85/85 [01:55<00:00,  1.36s/it]

Detailed benchmark:
| Operation                                       | mlx_gpu | mlx_gpu_compile | mlx_cpu | mps    | cpu    | mlx_gpu_compile/mlx_gpu speedup | mlx_gpu/mps speedup | mlx_gpu/mlx_cpu speedup |
| ----------------------------------------------- | ------- | --------------- | ------- | ------ | ------ | ------------------------------- | ------------------- | ----------------------- |
| Argmax / dim=64x1024x128 axi=0                  | 1.54    | 1.68            | 9.03    | 1.18   | 20.89  | -8%                             | -23%                | +485%                   |
| Argmax / dim=64x1024x128 axi=1                  | 1.54    | 1.67            | 9.00    | 0.56   | 2.45   | -7%                             | -63%                | +486%                   |
| Argmax / dim=64x1024x128 axi=2                  | 1.53    | 1.65            | 8.92    | 0.67   | 1.68   | -7%                             | -55%                | +484%                   |
| Argmax / dim=64x128x1024 axi=2                  | 1.54    | 1.65            | 9.17    | 0.60   | 1.48   | -6%                             | -61%                | +495%                   |
| BCE / dim=1000000 dim=1000000                   | 0.25    | 0.43            | 6.16    | 0.27   | 1.21   | -42%                            | +10%                | +2408%                  |
| BCE / dim=100000x32 dim=100000x32               | 0.46    | 0.28            | 21.01   | 0.38   | 2.56   | +64%                            | -16%                | +4462%                  |
| BCE / dim=100000x64x2 dim=100000x64x2           | 1.74    | 0.78            | 81.32   | 0.61   | 8.00   | +122%                           | -65%                | +4585%                  |
| BCE / dim=128x100000 dim=128x100000             | 1.74    | 0.77            | 81.20   | 0.46   | 7.79   | +125%                           | -73%                | +4570%                  |
| Concat / dim=1000000x64 dim=1000000x32 axi=1    | 2.97    | 2.67            | 82.78   | 2.42   | 18.03  | +11%                            | -18%                | +2691%                  |
| Concat / dim=1000000x64 dim=1000000x128 axi=1   | 4.53    | 5.09            | 156.55  | 4.59   | 40.24  | -11%                            | +1%                 | +3354%                  |
| Concat / dim=1000000x64 dim=1000000x64 axi=0    | 3.46    | 3.06            | 45.71   | 3.14   | 21.39  | +13%                            | -9%                 | +1220%                  |
| Concat / dim=64x1000000 dim=64x1000000 axi=0    | 3.09    | 3.08            | 68.54   | 3.12   | 21.60  | +0%                             | +0%                 | +2119%                  |
| Conv1d / dim=100x256x3 dim=8x3x3                | 0.31    | 0.25            | 0.30    | 0.23   | 2.45   | +25%                            | -25%                | -3%                     |
| Conv1d / dim=100x256x256 dim=8x3x256            | 1.16    | 1.09            | 6.35    | 0.76   | 67.74  | +7%                             | -34%                | +446%                   |
| Conv1d / dim=16x1000x80 dim=128x11x80           | 1.06    | 0.99            | 2.85    | 0.93   | 504.67 | +7%                             | -12%                | +168%                   |
| Conv1d / dim=16x1000x3 dim=128x11x3             | 0.43    | 0.27            | 0.43    | 0.36   | 54.18  | +55%                            | -16%                | +0%                     |
| Conv2d / dim=100x256x256x3 dim=8x3x3x3          | 2.56    | 2.55            | 796.90  | 1.84   | 116.92 | +0%                             | -28%                | +31032%                 |
| Conv2d / dim=10x256x256x12 dim=8x3x3x12         | 4.30    | 4.49            | 321.79  | 1.01   | 17.71  | -4%                             | -76%                | +7388%                  |
| Conv2d / dim=1x256x256x128 dim=8x3x3x128        | 0.42    | 0.43            | 516.80  | 1.01   | 16.63  | -3%                             | +141%               | +123451%                |
| Conv2d / dim=100x28x28x3 dim=8x3x3x3            | 0.20    | 0.20            | 8.82    | 0.46   | 1.25   | 0%                              | +127%               | +4241%                  |
| Conv2d / dim=1000x28x28x3 dim=8x3x3x3           | 0.52    | 0.55            | 86.42   | 0.64   | 7.45   | -5%                             | +22%                | +16464%                 |
| Gather / dim=64x256 dim=10                      | 0.29    | 0.16            | 0.02    | 0.43   | 0.00   | +84%                            | +45%                | -92%                    |
| Gather / dim=64x256 dim=1000                    | 0.17    | 0.17            | 0.04    | 0.20   | 0.02   | +2%                             | +16%                | -77%                    |
| Gather / dim=64x256 dim=1000000                 | 5.73    | 4.98            | 16.35   | 41.42  | 35.96  | +15%                            | +622%               | +185%                   |
| Gather / dim=1024x32 dim=10                     | 0.16    | 0.16            | 0.02    | 0.19   | 0.00   | +0%                             | +18%                | -89%                    |
| Gather / dim=1024x32 dim=1000                   | 0.15    | 0.15            | 0.02    | 0.16   | 0.02   | 0%                              | +5%                 | -86%                    |
| Gather / dim=1024x32 dim=1000000                | 0.94    | 0.94            | 5.05    | 5.27   | 4.71   | 0%                              | +460%               | +437%                   |
| LeakyReLU / dim=128x16x1024                     | 0.19    | 0.21            | 0.51    | 0.29   | 0.37   | -11%                            | +57%                | +172%                   |
| LeakyReLU / dim=64x128x1024                     | 0.35    | 0.34            | 1.01    | 0.48   | 1.40   | +5%                             | +33%                | +185%                   |
| Linear / dim=100x1024x32 dim=32x1024 dim=1024   | 2.20    | 1.79            | 15.63   | 1.51   | 29.22  | +22%                            | -31%                | +611%                   |
| Linear / dim=100x1024x64 dim=64x1024 dim=1024   | 2.04    | 2.05            | 19.23   | 2.04   | 32.83  | 0%                              | 0%                  | +841%                   |
| Linear / dim=100x1024x256 dim=256x1024 dim=1024 | 5.15    | 5.15            | 30.29   | 5.72   | 44.51  | 0%                              | +11%                | +488%                   |
| Linear / dim=100x1024x512 dim=512x1024 dim=1024 | 9.72    | 9.73            | 48.41   | 10.50  | 64.25  | 0%                              | +8%                 | +397%                   |
| Linear / dim=100x1x51200 dim=51200x1 dim=1      | 0.54    | 0.45            | 0.21    | 0.38   | 0.19   | +19%                            | -29%                | -61%                    |
| MatMul / dim=32x1x1000 dim=32x1000x128          | 0.17    | 0.23            | 0.09    | 0.26   | 0.17   | -26%                            | +53%                | -49%                    |
| MatMul / dim=1000x64x256 dim=256x32             | 0.44    | 0.45            | 1.36    | 5.00   | 1.68   | -1%                             | +1031%              | +208%                   |
| MatMul / dim=1000x64x1024 dim=1000x1024x32      | 1.32    | 1.38            | 9.64    | 1.45   | 12.71  | -4%                             | +9%                 | +632%                   |
| MatMul / dim=1000x1024x64 dim=1000x64x256       | 5.63    | 5.57            | 39.25   | 5.07   | 110.43 | +0%                             | -9%                 | +597%                   |
| MatMul / dim=64x1000000 dim=1000000x32          | 2.74    | 2.77            | 7.37    | 376.20 | 7.63   | 0%                              | +13627%             | +168%                   |
| MatMul / dim=1000000x64 dim=64x1024             | 21.96   | 15.88           | 83.77   | 971.32 | 306.95 | +38%                            | +4323%              | +281%                   |
| PReLU / dim=128x16x1024 dim=1                   | 0.26    | 0.23            | 1.22    | 0.40   | 0.37   | +11%                            | +54%                | +369%                   |
| PReLU / dim=64x128x1024 dim=1                   | 0.35    | 0.36            | 4.56    | 0.46   | 1.46   | -4%                             | +31%                | +1210%                  |
| ReLU / dim=128x16x1024                          | 0.27    | 0.20            | 0.21    | 0.22   | 0.35   | +39%                            | -17%                | -22%                    |
| ReLU / dim=64x128x1024                          | 0.34    | 0.34            | 0.79    | 0.47   | 1.49   | 0%                              | +38%                | +135%                   |
| Scatter / dim=64x16 dim=10                      | 0.13    | 0.16            | 0.02    | 0.12   | 0.00   | -18%                            | -7%                 | -85%                    |
| Scatter / dim=64x16 dim=1000                    | 0.15    | 0.16            | 0.08    | 0.11   | 0.02   | -1%                             | -29%                | -47%                    |
| Scatter / dim=64x16 dim=1000000                 | 0.31    | 0.31            | 53.08   | 2.74   | 3.07   | +2%                             | +774%               | +16864%                 |
| Scatter / dim=1024x32 dim=10                    | 0.16    | 0.15            | 0.02    | 0.13   | 0.00   | +4%                             | -20%                | -87%                    |
| Scatter / dim=1024x32 dim=1000                  | 0.16    | 0.15            | 0.13    | 0.12   | 0.03   | +3%                             | -23%                | -20%                    |
| Scatter / dim=1024x32 dim=1000000               | 0.49    | 0.47            | 100.24  | 5.52   | 3.80   | +3%                             | +1033%              | +20504%                 |
| ScatterSum / dim=64x16 dim=10                   | 0.03    | 0.03            | 0.02    | nan    | 0.00   | -4%                             | nan%                | -41%                    |
| ScatterSum / dim=64x16 dim=1000                 | 0.03    | 0.03            | 0.02    | nan    | 0.00   | +0%                             | nan%                | -38%                    |
| ScatterSum / dim=64x16 dim=1000000              | 0.03    | 0.03            | 0.02    | nan    | 1.19   | +2%                             | nan%                | -41%                    |
| ScatterSum / dim=1024x32 dim=10                 | 0.03    | 0.03            | 0.02    | nan    | 0.01   | +2%                             | nan%                | -41%                    |
| ScatterSum / dim=1024x32 dim=1000               | 0.03    | 0.03            | 0.02    | nan    | 0.01   | -1%                             | nan%                | -41%                    |
| ScatterSum / dim=1024x32 dim=1000000            | 0.03    | 0.03            | 0.02    | nan    | 5.98   | -2%                             | nan%                | -42%                    |
| ScatterMax / dim=64x16 dim=10                   | 0.03    | 0.03            | 0.02    | nan    | 0.00   | -2%                             | nan%                | -39%                    |
| ScatterMax / dim=64x16 dim=1000                 | 0.03    | 0.03            | 0.01    | nan    | 0.00   | -4%                             | nan%                | -47%                    |
| ScatterMax / dim=64x16 dim=1000000              | 0.03    | 0.03            | 0.01    | nan    | 1.18   | 0%                              | nan%                | -49%                    |
| ScatterMax / dim=1024x32 dim=10                 | 0.03    | 0.03            | 0.01    | nan    | 0.01   | +3%                             | nan%                | -51%                    |
| ScatterMax / dim=1024x32 dim=1000               | 0.03    | 0.03            | 0.02    | nan    | 0.01   | +2%                             | nan%                | -37%                    |
| ScatterMax / dim=1024x32 dim=1000000            | 0.03    | 0.03            | 0.02    | nan    | 6.18   | +0%                             | nan%                | -44%                    |
| SeLU / dim=128x16x1024                          | 0.39    | 0.23            | 1.66    | 0.29   | 0.78   | +71%                            | -27%                | +322%                   |
| SeLU / dim=64x128x1024                          | 0.36    | 0.36            | 6.34    | 0.39   | 3.02   | +0%                             | +7%                 | +1652%                  |
| Sigmoid / dim=128x16x1024                       | 0.16    | 0.19            | 1.58    | 0.34   | 0.70   | -14%                            | +105%               | +858%                   |
| Sigmoid / dim=64x128x1024                       | 0.35    | 0.35            | 5.99    | 0.49   | 2.44   | -1%                             | +40%                | +1621%                  |
| Softmax / dim=64x1000000 axi=-1                 | 5.87    | 4.42            | 40.93   | 3.05   | 19.11  | +32%                            | -48%                | +597%                   |
| Softmax / dim=1000000x64 axi=-1                 | 5.79    | 4.44            | 40.30   | 3.14   | 18.50  | +30%                            | -45%                | +595%                   |
| Softmax / dim=64x16x32x1024 axi=-1              | 3.16    | 2.42            | 21.48   | 1.77   | 8.58   | +30%                            | -43%                | +579%                   |
| Softmax / dim=128x16x32x1024 axi=-1             | 6.07    | 4.64            | 42.35   | 3.26   | 19.21  | +30%                            | -46%                | +597%                   |
| Softmax / dim=1024x16x32x128 axi=-1             | 6.08    | 4.61            | 42.53   | 3.18   | 19.76  | +31%                            | -47%                | +599%                   |
| Softmax / dim=1024x64x32x8 axi=-1               | 1.70    | 1.35            | 10.64   | 1.15   | 11.17  | +26%                            | -32%                | +525%                   |
| Softplus / dim=128x16x1024                      | 0.33    | 0.24            | 11.16   | 0.34   | 1.39   | +39%                            | +1%                 | +3243%                  |
| Softplus / dim=64x128x1024                      | 0.40    | 0.39            | 44.73   | 0.51   | 4.89   | +1%                             | +26%                | +11101%                 |
| Sort / dim=64x128x1024 axi=0                    | 0.72    | 0.76            | 228.28  | 11.12  | 59.75  | -4%                             | +1441%              | +31554%                 |
| Sort / dim=64x128x1024 axi=1                    | 0.73    | 0.76            | 228.43  | 9.83   | 32.25  | -3%                             | +1253%              | +31356%                 |
| Sort / dim=64x128x1024 axi=2                    | 0.72    | 0.74            | 228.24  | 6.69   | 35.38  | -2%                             | +826%               | +31536%                 |
| Sum / dim=64x128x128x128 axi=0                  | 1.56    | 1.53            | 6.43    | 1.78   | 11.86  | +2%                             | +13%                | +312%                   |
| Sum / dim=64x128x128x128 axi=1                  | 1.55    | 1.57            | 6.46    | 1.72   | 9.36   | -1%                             | +11%                | +316%                   |
| Sum / dim=64x128x128x128 axi=2                  | 1.55    | 1.59            | 6.47    | 1.78   | 5.48   | -2%                             | +15%                | +318%                   |
| Sum / dim=64x128x128x128 axi=3                  | 1.54    | 1.57            | 6.44    | 1.73   | 5.24   | -1%                             | +12%                | +318%                   |
| SumAll / dim=64x128x128x128                     | 1.58    | 1.56            | 6.44    | 1.85   | 4.63   | +1%                             | +17%                | +309%                   |
| SumAll / dim=1000000                            | 0.17    | 0.17            | 0.06    | 0.21   | 0.05   | +1%                             | +23%                | -62%                    |
| SumAll / dim=1000000x128                        | 1.50    | 1.49            | 6.21    | 1.58   | 4.44   | +0%                             | +5%                 | +313%                   |
| SumAll / dim=128x1000000                        | 1.51    | 1.50            | 6.16    | 1.55   | 4.52   | +0%                             | +2%                 | +308%                   |

 Average benchmark:
| Operation  | mlx_gpu | mlx_gpu_compile | mlx_cpu | mps    | cpu    | mlx_gpu_compile/mlx_gpu speedup | mlx_gpu/mps speedup | mlx_gpu/mlx_cpu speedup |
| ---------- | ------- | --------------- | ------- | ------ | ------ | ------------------------------- | ------------------- | ----------------------- |
| Argmax     | 1.53    | 1.66            | 9.03    | 0.75   | 6.62   | -7%                             | -50%                | +488%                   |
| BCE        | 1.05    | 0.56            | 47.42   | 0.43   | 4.89   | +85%                            | -58%                | +4437%                  |
| Concat     | 3.51    | 3.47            | 88.40   | 3.32   | 25.32  | +1%                             | -5%                 | +2417%                  |
| Conv1d     | 0.74    | 0.65            | 2.48    | 0.57   | 157.26 | +14%                            | -23%                | +235%                   |
| Conv2d     | 1.60    | 1.65            | 346.15  | 0.99   | 31.99  | -2%                             | -38%                | +21534%                 |
| Gather     | 1.24    | 1.09            | 3.58    | 7.94   | 6.79   | +13%                            | +540%               | +188%                   |
| LeakyReLU  | 0.27    | 0.27            | 0.76    | 0.38   | 0.89   | 0%                              | +41%                | +181%                   |
| Linear     | 3.93    | 3.83            | 22.75   | 4.03   | 34.20  | +2%                             | +2%                 | +479%                   |
| MatMul     | 5.38    | 4.38            | 23.58   | 226.55 | 73.26  | +22%                            | +4114%              | +338%                   |
| PReLU      | 0.30    | 0.30            | 2.89    | 0.43   | 0.91   | +2%                             | +41%                | +851%                   |
| ReLU       | 0.30    | 0.27            | 0.50    | 0.35   | 0.92   | +13%                            | +13%                | +65%                    |
| Scatter    | 0.23    | 0.23            | 25.59   | 1.45   | 1.15   | +0%                             | +524%               | +10883%                 |
| ScatterSum | 0.03    | 0.03            | 0.02    | nan    | 1.20   | 0%                              | nan%                | -41%                    |
| ScatterMax | 0.03    | 0.03            | 0.02    | nan    | 1.23   | 0%                              | nan%                | -45%                    |
| SeLU       | 0.38    | 0.30            | 4.00    | 0.34   | 1.90   | +27%                            | -10%                | +960%                   |
| Sigmoid    | 0.26    | 0.27            | 3.79    | 0.41   | 1.57   | -5%                             | +61%                | +1376%                  |
| Softmax    | 4.78    | 3.65            | 33.04   | 2.59   | 16.05  | +31%                            | -45%                | +591%                   |
| Softplus   | 0.37    | 0.32            | 27.94   | 0.42   | 3.14   | +15%                            | +15%                | +7524%                  |
| Sort       | 0.72    | 0.75            | 228.32  | 9.21   | 42.46  | -3%                             | +1174%              | +31481%                 |
| Sum        | 1.55    | 1.56            | 6.45    | 1.75   | 7.98   | -1%                             | +13%                | +316%                   |
| SumAll     | 1.19    | 1.18            | 4.72    | 1.30   | 3.41   | +0%                             | +9%                 | +296%                   |
```

### A comprehensive benchmark of MLX ops.

This repo aims to benchmark Apple's MLX operations and layers, on all Apple Silicon chips, along with some GPUs.

**Contributions:** Everyone can contribute to the benchmark! If you have a missing device or if you want to add a missing layer/operation, please read the [contribution guidelines](CONTRIBUTING.md).

Current M chips: `M1`, `M1 Pro`, `M1 Max`, `M2`, `M2 Pro`, `M2 Max`, `M2 Ultra`, `M3`, `M3 Pro`, `M3 Max`.

Current CUDA GPUs: `RTX4090`, `Tesla V100`.

Missing devices: `M1 Ultra`, and `other CUDA GPUs`.

> [!NOTE]
> You can submit your benchmark even for a device that is already listed, provided you use a newer version of MLX. Simply submit a PR by overriding the old benchmark table. Also, most of the existing benchmarks do not include the `mx.compile` feature, which has been recently added to mlx-benchmark.

## Benchmarks 🧪

Benchmarks are generated by measuring the runtime of every `mlx` operations on GPU and CPU, along with their equivalent in pytorch with `mps`, `cpu` and `cuda` backends. On MLX with GPU, the operations compiled with `mx.compile` are included in the benchmark by default. To not benchmark the compiled functions, set `--compile=False`. 

For each operation, we measure the runtime of multiple experiments. We propose 2 benchmarks based on these experiments:

* [Detailed benchmark](benchmarks/detailed_benchmark.md): provides the runtime of each experiment. 
* [Average runtime benchmark](benchmarks/average_benchmark.md): computes the mean of experiments. Easier to navigate, with fewer details.


## Installation 💻


### Installation on Mac devices

Running the benchmark locally is straightforward. Create a new env with `osx-arm64` architecture and install the dependencies.

```shell
CONDA_SUBDIR=osx-arm64 conda create -n mlx_benchmark python=3.10 numpy pytorch torchvision scipy requests -c conda-forge

pip install -r requirements.txt
```


### Installation on other devices
Other operating systems than macOS can only run the torch experiments, on CPU or with a CUDA device. Install a new env without the `CONDA_SUBDIR=osx-arm64` prefix and install the torch package that matches your CUDA version. Then install all the requirements within `requirements.txt`, except `mlx`.

Finally, open the `config.py` file and set:
```
USE_MLX = False
```
to avoid importing the mlx package, which cannot be installed on non-Mac devices.

## Run the benchmark 🧑‍💻

### Run on Mac

To run the benchmark on mps, mlx and CPU:

```shell
python run_benchmark.py --include_mps=True --include_mlx_gpu=True --include_mlx_cpu=True --include_cpu=True
```

### Run on other devices

To run the torch benchmark on CUDA and CPU:

```shell
python run_benchmark.py --include_mps=False --include_mlx_gpu=False --include_mlx_cpu=False --include_cuda=True --include_cpu=True
```

### Run only compiled functions

If you're interested in benchmarking only operations against operations compiled with `mx.compile`, you can run:

```shell
python run_benchmark.py --include_mps=False --include_cpu=False --include_mlx_cpu=False
```

## Contributing 🚀

If you have a device not yet featured in the benchmark, especially the ones listed below, your PR is welcome to broaden the scope and accuracy of this project.
