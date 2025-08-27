# Benchmark Results for Many Single-Shot HDF5 Files

Content in this folder:

* The Jupyter notebook [bench-analysys.ipynb](./bench-analysis.ipynb) holds all the detailed explanation of the HDF5 files, benchmarks, and benchmark analysis results.
* The benchmark script [run-bench.py](./run-bench.py).
* Benchmark results when HDF5 files are in:
    * AWS EC2 instance local file system [ec2-local.csv](./ec2-local.csv)
    * AWS S3 [ec2-s3.csv](./ec2-s3.csv)
    * AWS S3 but accessed with the new ROS3 driver's backend [ec2-s3-libaws.csv](./ec2-s3-libaws.csv)
