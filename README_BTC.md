1

# JPEG AIC-3 BTC Subjective Study Data

This repository contains data from a study conducted as part of JPEG AIC-3 activities using boosted triplet comparisons (BTC). For more information about the JPEG AIC-3, see: [JPEG AIC-3](https://jpeg.org/aic/index.html).

For detailed information about the BTC experiment, see: [Link to the paper will be added here]

The study was conducted on Amazon Mechanical Turk (MTurk) from January 4 to January 10, 2024. The data includes responses from crowd workers to triplets of images with boosted distortions, as well as demographic information about the workers.

## Files in the Repository

1. `JPEG-AIC_BTC_final_response_data_2024.01.10.csv`
2. `JPEG-AIC_BTC_final_user_data_2024_01_10.csv`

### File 1: JPEG-AIC_BTC_final_response_data_2024.01.10.csv

This file contains the responses from workers who participated in the image quality evaluation study.

#### Column Descriptions

| Column Name       | Type        | Description                                                                                                                      |
|-------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `assignment`      | Categorical | Unique identifier for each assignment given to a worker.                                                                                                    |
| `worker`          | Numeric     | Unique identifier for each worker who participated in this study.                                                                                           |
| `method`          | Categorical | Method used for image comparisons (e.g., BTC).                                                                                                              |
| `task`            | Numeric     | Identifier for each task within the study.                                                                                                                  |
| `question_id`     | Numeric     | Unique identifier for each question presented to the workers.                                                                                               |
| `img_num`         | Numeric     | Unique identifier for each source image used in the study.                                                                                                  |
| `codec_left`      | Numeric     | Codec type used for compression of the left image in the triplet comparison.                                                                                |
| `codec_pivot`     | Numeric     | Codec type used for compression of the pivot image in the triplet comparison.                                                                               |
| `codec_right`     | Numeric     | Codec type used for compression of the right image in the triplet comparison.                                                                               |
| `dlevel_left`     | Numeric     | Distortion/compression level of the left image.                                                                                                             |
| `dlevel_pivot`    | Numeric     | Distortion/compression level of the pivot image.                                                                                                            |
| `dlevel_right`    | Numeric     | Distortion/compression level of the right image.                                                                                                            |
| `img_left`        | Categorical | Filename of the left image.                                                                                                                                 |
| `img_pivot`       | Categorical | Filename of the pivot image.                                                                                                                                |
| `img_right`       | Categorical | Filename of the right image.                                                                                                                                |
| `is_same`         | Logical     | Logical value indicating if the images in the triplet are compressed with the same codec (0 or 1).                                                          |
| `is_cross`        | Logical     | Logical value indicating if the triplet is a cross-codec comparison (0 or 1).                                                                               |
| `is_bias`         | Logical     | Logical value indicating if the triplet is a bias question (i.e., the distortion level and the codec of the left and right images are the same) (0 or 1).   |
| `is_trap`         | Logical     | Logical value indicating if the triplet is a trap question (i.e., the left or right image has distortion level of 10 and the other is the source) (0 or 1). |
| `question_order`  | Numeric     | Order of the question presented to the worker.                                                                                                              |
| `response`        | Categorical | Worker’s response to the question (e.g., left, not sure, right).                                                                                            |
| `submission_time` | Datetime    | Timestamp when the worker submitted the response.                                                                                                           |
| `response_time`   | Numeric     | Time taken by the worker to respond, in seconds.                                                                                                            |
| `reload_count`    | Numeric     | Number of times the worker reloaded the page during the task.                                                                                               |
| `resolution`      | Categorical | Screen resolution of the worker’s device during the task.                                                                                                   |

### File 2: JPEG-AIC_BTC_final_user_data_2024_01_10.csv

This file contains demographic information about the workers who participated in the study.

#### Column Descriptions

| Column Name      | Type        | Description                                                                                                          |
|------------------|-------------|----------------------------------------------------------------------------------------------------------------------|
| `worker`         | Numeric     | Unique identifier for each worker who participated in this study.                                                    |
| `age`            | Categorical | Age range of the worker (e.g., '18-25').                                                                             |
| `gender`         | Categorical | Gender of the worker (e.g., 'male', 'female').                                                                       |
| `time_zone`      | Categorical | Time zone of the location where the worker participated (e.g., 'America/Los_Angeles').                               |
| `display_size`   | Numeric     | Physical size of the worker's display device in inches (e.g., '[32]').                                               |
| `tasks`          | Numeric     | List of tasks completed by the worker (e.g., '[11,12]').                                                             |
| `assignments`    | string      | List of assignment IDs associated with the tasks completed by the worker.                                            |
| `completion_time`| Numeric     | List of completion times for the tasks, in seconds.                                                                  |
| `ishihara_test1` | Numeric     | Number submitted by the worker for the first Ishihara test (color blindness test). The ground truth number is 2.     |
| `ishihara_test2` | Numeric     | Number submitted by the worker for the second Ishihara test (color blindness test). The ground truth number is 16.   |

## Usage Notes

- Ensure that categorical data types are properly interpreted when reading the files into MATLAB or other software.
- Convert the necessary columns to categorical or logical if they are not automatically detected as such.
- The `submission_time` column in `JPEG-AIC_BTC_final_response_data_2024.01.10.csv` is in ISO 8601 format and may need to be parsed accordingly.

## Example Code to Read the CSV files in MATLAB

### Reading the Response Data

```matlab
file_name = 'JPEG-AIC_BTC_final_response_data_2024.01.10.csv';
opts = detectImportOptions(file_name);
opts = setvartype(opts, {'assignment', 'worker', 'method', 'img_left', 'img_pivot', 'img_right', 'response', 'resolution'}, 'categorical');
opts = setvartype(opts, {'is_same', 'is_cross', 'is_bias', 'is_trap'}, 'logical');

data = readtable(file_name, opts);
```

### Reading the User Data

```matlab
user_file_name = 'JPEG-AIC_BTC_final_user_data_2024_01_10.csv';
user_opts = detectImportOptions(user_file_name);
user_opts = setvartype(opts, {'age', 'gender', 'time_zone'}, 'categorical');

user_data = readtable(user_file_name, user_opts);
```

By following these instructions, users should be able to effectively work with the datasets and understand the purpose and type of each column included.

## License

TBD

## Contact

TBD
