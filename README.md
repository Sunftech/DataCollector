# DataCollector
Collect sensor data and nearby beacon info.

需要实现各传感器数据的采集、存储与上传功能  
###界面需求:  

- 界面需要一个按钮，进行开始/结束采集，结束采集时需要上传数据到指定网络位置。  
- 界面需要一个Label提示采集状态（“采集中”/“采集未开始”）

###采集内容需求:  
需要采集的内容包括  

- Accelerometer (raw[3 axes], gravity[3 axes], linear[3 axes])  
- Gyroscope (euler angle[3 axes], quanternions[4])  
- Magnetometer (raw[3 axes])  
- 设备周围的Beacon数据  

传感器采样频率为30Hz, Beacon扫描频率1Hz, 数据以传感器采样对齐  

### 数据格式、存储及上传:

- 采集时数据暂存到本地文件
- 每次传感器采样作为一行数据，每种传感器内容及最近的一次Beacon扫描结果作为一列, 每列以tab分割  
- 在requestb.in申请一个临时地址，结束采集时使用HTTP POST将数据作为body上传到该地址  