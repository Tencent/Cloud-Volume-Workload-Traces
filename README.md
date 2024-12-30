# Tencent Cloud Virtual Disk Traces

These traces are published by Tencent Cloud to help researchers understand workloads in the cloud block storage systems, which includes subscription information and I/O traces for approximately 16,000 cloud virtual disks (CVD).

These traces were collected from a production cluster of Tencent Cloud’s block storage service. Specifically, 16,000 CVDs ware sampled from 10 warehouses in the Shanghai data center.

# <small> Download </small>

This repository contains all the compressed trace files in **Cloud_Disk_dataset.zip**.

**Notes :**  The total size of data is about 1.3 GB compressed and 7.3 GB uncompressed.

# <small> Schema </small>

The directory structure of the dataset is as follows:

    /dataset
    ├── README.md
    ├── disk_subscription_info
    └── disk_load_data
        ├── 0a0a7b84-2279-405e-9cbc-b395c725e01a
        ├── 0a0c1dea-723a-4484-a89c-53c02fc4b107
        └── ...

**disk_subscript_info**

Each row of disk_subscript_info describes the subscription features of a CVD:

| Feature | Example | Description |
| ---- | ---- | ---- |
| disk_uid | 0a0a7b84-2279-405e-9cbc-b395c725e01a | A unique identifier for the CVD. |
| disk_attr | 0 | Product attributes corresponding to different service levels. The dataset includes two categories (0 and 1). |
| disk_type | 1 | Indicates whether the CVD is a data disk (0) or a system disk (1). |
| user_type | 0 | Indicates whether a user is an occasional (0) or regular (1) purchaser of cloud services. |
| vm_cpu | 4 | Number of CPU cores in the virtual machine attached to the CVD. |
| vm_memory | 32 | Memory size of the virtual machine attached to the CVD (GB). |
| disk_capacity | 50 | Subscribed capacity of the CVD (GB). |

**disk_load_data**

Each file in disk_load_data records the load of a CVD over a period of up to two months. The file name corresponds to the disk_uid. Each row in the file provides load information collected at 300-second intervals:

| Column | Example | Description |
| ---- | ---- | ---- |
| timestamp | 1593748800 | The collected timestamp, in microseconds. |
| read_IOPS | 11 | Read IOPS of the CVD at the time. |
| read_bandwidth | 50 | Read throughput of the CVD at the time (KB/s). |
| write_IOPS | 7 | Write IOPS of the CVD at the time. |
| write_bandwidth | 12 | Write throughput of the CVD at the time (KB/s). |
| disk_usage | 3360 | Disk usage of the CVD at the time (MB). |

# <small> Acknowledgements </small>

We thank Difan Tan and Jiawei Li of Huazhong University of Science and Technology for their analysis and anonymization of the data.

# <small> Citation </small>

The trace is a subset of the workload described in ["TELA: A Temporal Load-Aware Cloud Virtual Disk Placement Scheme"](https://doi.org/10.1145/3669940.3707252) in ASPLOS’25. When using this trace in your research, please make sure to cite the paper appropriately.

# <small> License </small>

The trace data and document are licensed under [CC-4.0](https://creativecommons.org/licenses/by/4.0).