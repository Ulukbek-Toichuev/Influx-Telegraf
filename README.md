# Influx-Telegraf
How to monitor Linux system with Influx-Telegraf
## Install Influx
1. You need install **influxdb** and **influxdb client**
```console
sudo apt install influxdb influxdb-client
```
3. Unmask influx service and check deamon status
```console
sudo systemctl unmask influxdb.service
```
```console
systemctl status influxdb
```
5. Run influx CLI
```console
influx
```
6. Create database for telegraf and create user telegraf
```console
CREATE DATABASE telegraf
```
```console
CREATE USER admin WITH PASSWORD 'passwd' WITH ALL PRIVILEGES
```
![image](https://user-images.githubusercontent.com/67442103/159889854-9d7b36f5-f92d-4c0c-9e6c-c9af8279b181.png)

## Install Telegraf
1. Download **Telegraf**
```console
wget https://dl.influxdata.com/telegraf/releases/telegraf_1.22.0-1_amd64.deb
```
2. Install downloaded deb package
```console
sudo dpkg -i telegraf_1.22.0-1_amd64.deb
```
3. Check telegraf service status
```console
systemctl status telegraf
```
![image](https://user-images.githubusercontent.com/67442103/159897684-da4f0122-44d3-402f-9e15-228af4458848.png)

4. Configure your Influx config file
```console
sudo nano /etc/influxdb/influxdb.conf
```
![image](https://user-images.githubusercontent.com/67442103/159904651-0f425e21-9cdc-41e2-8d77-83b0958fbebe.png)

5. Configure your Telegraf config file
```console
sudo nano /etc/telegraf/telegraf.conf
```
![image](https://user-images.githubusercontent.com/67442103/159906636-3650f5af-47dd-49cf-a442-e26db9434e84.png)

6. **And don`t forgot restart Influx, Telegraf services**
```console
sudo systemctl restart telegraf influxdb
```

## Select the Port Forwarding

1. You must forward port for connect to influxdb in Virtual Box

![image](https://user-images.githubusercontent.com/67442103/159911090-e5f86482-f7ef-4b4f-95d3-328836d192f6.png)


![image](https://user-images.githubusercontent.com/67442103/159910789-38bdfff7-2abc-4f7d-ace5-7f8aaf0aacdb.png)


## Connect to Grafana

Grafana addres: http://127.0.0.1:3000/
1. Choose datasource

![image](https://user-images.githubusercontent.com/67442103/159908075-048b5abd-52a9-456f-aaa7-5f56bbe49ca2.png)

2. Set name

![image](https://user-images.githubusercontent.com/67442103/159908296-4e79a1a0-f2cb-484f-b6b9-6356ff07e5fd.png)

3. Set HTTP properties

![image](https://user-images.githubusercontent.com/67442103/159908395-dbeb479a-a96e-4f77-a778-df3f00dd59a1.png)

4. Set db and user properties

![image](https://user-images.githubusercontent.com/67442103/159908503-bdc53730-29c6-46d1-bdb4-b6b9cbb51d53.png)

5. Send this query to see available memory

![image](https://user-images.githubusercontent.com/67442103/159910275-9018354a-1237-45ac-89bb-f342d6785bc3.png)


![image](https://user-images.githubusercontent.com/67442103/159910357-0d520df1-c1fc-4ae0-a80e-18d285f32ad3.png)
