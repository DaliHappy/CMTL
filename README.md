# CMTL
We will upload all the codes and datasets after the paper is confirmed to be accepted. The following is the introduction to the usage instructions of the paper codes.
1. Data preprocessing file
Public datasets
The data preprocessing file of the public dataset is: aliexpress.py file under the datasets folder [you can also directly download the preprocessed dataset and use it directly]] The download address of AliEpress raw data is originaoriginaldataset [https://tianchi.aliyun.com/dataset/dataDetail? datald = 74690]] The download address after AliExpress processing: Processed dataset Google DriveProcessed Data 7 Baidu Netdisk [https://pan.baidu.com/s/1AfXoJSshjW-PILXZ6019FA? pwd = 4u0r]]
Build your own dataset
The data preprocessing files of the self-built dataset are dataprocess_ali2.ipynb and dataprocess_tecent2_gpu_random. ipynb. The folder contains the collected data files [detailed comments in the code]]. The main operations for processing data sets include: Data Classification, data numerical, data buckets, adding Resource Data label columns, negative data sampling (sampling ratio: 1:99), and data set Division (8:2 ratio of training set and test set). Examples of processed data are as follows: 

It should be noted that price-related data is used only in the part of price constraints, and experimental verification shows that there is a strong correlation between "instance" data columns and results. Therefore, this column was not used in subsequent experiments.
2. Multi-task learning model (matching requirements and computing power)
You can run the main.py file directly, and there are detailed comments in the code.
If you need to generate the weight file, change the parameter of function 'main()' in main.py to 'test'.
parser.add_argument('--state', default='test')

	In addition, if you use public data sets, you need to modify the model corresponding to the data set in the main.py at the top of the reference model. For example, when the dataset is AliExpress_ES, the referenced model is modified to mymodel_ES.
from models.mymodel_ES import MyModel


3. Price constraints
You can run the main_price.py file directly. There are comments for this part in the code.

4. Explanation of the Generated Part
You can run the explain.py file directly, and there are comments for this part in the code.
Open Al needs to be installed before running, which calls the DeepSeek API interface. For more details, please see: https://platform.deepseek.com/sign_in
5. Operating environment and experimental parameter configuration
Operating environment
* Python 3.6
* PyTorch > 1.10
* pandas
* numpy
* tqdm
Experimental parameter settings
- dataset_name: choose a dataset in ['Ali', 'Tencent', ], default for `Ali`
- dataset_path: default for `./data`
- model_name: choose a model in ['singletask', 'sharedbottom', 'omoe', 'mmoe', 'ple', 'aitm', 'metaheac','stem','adat','mymodel'], default for `mymodel`
- epoch: the number of epochs for training, default for `50`
- task_num: the number of tasks, default for `4` (CPU、CPU、memory、PPS)
- expert_num:  default for `1`
- learning_rate: default for `0.001`
- batch_size: default for `256`
- weight_decay: default for `1e-6`
- device: the device to run the code, default for `cuda:0`
- save_dir: the folder to save parameters, default for `chkpt`
