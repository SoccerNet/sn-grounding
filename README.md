# SoccerNet - Replay Grounding

Welcome to the SoccerNet Development Kit for the Replay Grounding Task and Challenge. This kit is meant as a help to get started working with the soccernet data and the proposed task. More information about the dataset can be found on our [official website](https://soccer-net.org/).

SoccerNet Replay Grounding is part of the SoccerNet-v2 dataset, which is an extension of SoccerNet-v1 with new and challenging tasks including
action spotting, camera shot segmentation with boundary detection, and a novel replay grounding task.

<p align="center"><img src="Images/GraphicalAbstract-SoccerNet-V2-1.png" width="640"></p>

The Action Spotting dataset consists of 500 complete soccer games including:
 - Full untrimmed broadcast videos in both low and high resolution.
 - Pre-computed features such as ResNET-152.
 - Annotations of camera changes and replays with live action spot (Labels-cameras.json).

Participate in our upcoming Challenge in the [CVPR 2022 International Challenge on Activity Recognition Workshop](http://activity-net.org/challenges/2021/index.html) and try to win up to 500$ sponsored by [SportRadar](https://www.sportradar.com/)! All details can be found on the [challenge website](), or on the [main page](https://soccer-net.org/).

The participation deadline is fixed at the 30th of May 2022.
The official rules and guidelines are available on [ChallengeRules.md](ChallengeRules.md).

<a href="https://youtu.be/T8Qc39FcQ7A">
<p align="center"><img src="Images/Thumbnail.png" width="720"></p>
</a>

### 2021 Challenge leaderboard

This table summarizes the current performances on the 2021 challenge. 
For the leaderboard on the 2022 challenge, please visit EvalAI [test](https://eval.ai/web/challenges/challenge-page/761/leaderboard/2072) and [challenge](https://eval.ai/web/challenges/challenge-page/761/leaderboard/2074) leaderboards.

| Model     | tight Avg-AP (challenge)  | Avg-AP (challenge) | tight Avg-AP (test)  | Avg-AP (test) |
| ----------| -------- | -------- | -------- | -------- |
|[Baidu Research](https://arxiv.org/pdf/2106.14447.pdf)| TBD | 71.90% | TBD | 76.00% |
|[OPPO]()| TBD | 63.91% | NA | NA |
|[Xinhuazhiyun]()| TBD | 41.08% | NA | NA |
|[CALF_more_negatives](Benchmarks)| TBD | 40.75% | NA | NA |
|[CALF](Benchmarks)| TBD | 31.28 | TBD | 32.39% |
|[NetVLAD](Benchmarks)| TBD | 25.13% | TBD | 24.57% |

### Published research benchmark

This table summarizes the current performances of published methods only.  Last update January 2022.

| Model     | tight Avg-AP (challenge)  | Avg-AP (challenge) | tight Avg-AP (test)  | Avg-AP (test) |
| ----------| -------- | -------- | -------- | -------- |
|[CALF_more_negatives](Benchmarks)| TBD | 40.75% | NA | NA |
|[CALF](Benchmarks)| TBD | 31.28 | TBD | 32.39% |
|[NetVLAD](Benchmarks)| TBD | 25.13% | TBD | 24.57% |

## How to download the dataset

A [SoccerNet pip package](https://pypi.org/project/SoccerNet/) to easily download the data and the annotations is available. 

To install the pip package simply run:

<code>pip install SoccerNet</code>

Then use the API to downlaod the data of interest:

```
from SoccerNet.Downloader import SoccerNetDownloader
mySoccerNetDownloader = SoccerNetDownloader(LocalDirectory="/path/to/SoccerNet")
mySoccerNetDownloader.downloadGames(files=["Labels-cameras.json"], split=["train","valid","test"])
```

If you want to download the videos, you will need to fill a NDA to get the password.

```
mySoccerNetDownloader.password = input("Password for videos?:\n")
mySoccerNetDownloader.downloadGames(files=["1_224p.mkv", "2_224p.mkv"], split=["train","valid","test","challenge"])
mySoccerNetDownloader.downloadGames(files=["1_720p.mkv", "2_720p.mkv", "video.ini"], split=["train","valid","test","challenge"])
```
We provide several features including ResNET (used for our [benchmarks](Benchmarks)), and last year's winners features from [Baidu Research](https://arxiv.org/pdf/2106.14447.pdf). Check out our [pip package](https://pypi.org/project/SoccerNet/) documentation for more features.
```
mySoccerNetDownloader.password = input("Password for videos?:\n")
mySoccerNetDownloader.downloadGames(files=["1_ResNET_TF2_PCA512.npy.mkv", "2_ResNET_TF2_PCA512.npy.mkv"], split=["train","valid","test","challenge"])
mySoccerNetDownloader.downloadGames(files=["1_baidu_soccer_embeddings.npy", "2_baidu_soccer_embeddings.npy.mkv", "video.ini"], split=["train","valid","test","challenge"])
```
## How to extract video features 

As it was one of the most requested features on SoccerNet-V1, check out the [action spotting repository](https://github.com/SoccerNet/sn-spotting/Features) to extract the features.

## Benchmark Implementations

This repository contains several [benchmarks](Benchmarks) for replay grounding, which are presented in the [SoccerNet-V2 paper](https://arxiv.org/pdf/2011.13367.pdf). You can use these codes to build upon our methods and improve the performances.


## Evaluation

This repository and the pip package provide evaluation functions for the proposed tasks based on predictions saved in the JSON format. See the [Evaluation](Evaluation) folder of this repository for more details.

## Visualizations

Finally, this repository provides the [Annotation tool](Annotation) used to annotate the camera changes and replays. This tool can be used to visualize the information. Please follow the instruction in the dedicated folder for more details.

## Citation

For further information check out the paper and supplementary material:
https://openaccess.thecvf.com/content/CVPR2021W/CVSports/papers/Deliege_SoccerNet-v2_A_Dataset_and_Benchmarks_for_Holistic_Understanding_of_Broadcast_CVPRW_2021_paper.pdf

Please cite our work if you use our dataset:
```bibtex
@InProceedings{Deliège2020SoccerNetv2,
      title={SoccerNet-v2 : A Dataset and Benchmarks for Holistic Understanding of Broadcast Soccer Videos}, 
      author={Adrien Deliège and Anthony Cioppa and Silvio Giancola and Meisam J. Seikavandi and Jacob V. Dueholm and Kamal Nasrollahi and Bernard Ghanem and Thomas B. Moeslund and Marc Van Droogenbroeck},
      year={2021},
      booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
      month = {June},
}
```
