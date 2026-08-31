

<!-- Start of picture text -->
This message is shown once a day. To disable it please create the<br>/home/ianaja/.hushlogin file.<br>:~$ cd /mnt/c/tools/proyek_spark<br>: $ sudo apt update<br><!-- End of picture text -->



<!-- Start of picture text -->
Fetched 10.8 MB in 5s (2298 kB/s)<br>Reading package lists... Done<br>Building dependency tree... Done<br>Reading state information... Done<br>252 packages can be upgraded. Run ‘apt List --upgradable' to see them.<br>8 $ sudo apt install python3-pip -y<br>Deo din ar + Don<br><!-- End of picture text -->



<!-- Start of picture text -->
Set-Content -Path “proses_parquet.py” -Value ‘import pandas as pd<br>import pyarrow as pa<br>import pyarrow.parquet as pq<br>import os<br>def main():<br>print("--- 1. Menyiapkan Data Awal ---")<br>data = {<br>"Ip": [1, 2, 3, 4, 5],<br>“Nama”: ["Christiano”, “Imanuel", "Silooy", "Andi", “Budi"],<br>“Jurusan”: [“Informatika", “Sistem Informasi”, “Teknik Elektro”, “Informatika”, “Manajemen"],<br>“Nilai": [85, 98, 78, 92, 65]<br>}<br># Membuat DataFrame Pandas<br>df = pd.DataFrame(data)<br>print(df)<br># Transformasi data: Menambahkan kolom Status kelulusan<br>df["Status"] = df["Nilai"].apply(lambda x: “Lulus" if x >= 75 else "Remedial")<br>print("\n--- 2. Data Setelah Transformasi ---")<br>print(df)<br># Menyimpan ke format Apache Parquet (Columnar & Sangat Hemat Ruang)<br>output_dir = “output_data_parquet”<br>os.makedirs(output_dir, exist_ok=True)<br>file path = os.path.join(output_dir, “data_sirkulasi.parquet”)<br>print(#"\n--- 3. Menyimpan ke format Apache Parquet ke: {file_path} ---")<br>table = pa.Table.from_pandas(df)<br>pq-write_table(table, file_path)<br># Membaca Kembali Data dari Parquet<br>print(“\n. 4. Membaca Kembali Data dari Parquet ")<br>table_read = pq-read_table(filepath)<br>df_read = table_read.to_pandas()<br>print(df_read)<br># Menampilkan informasi ukuran file<br>file_size = os.path.getsize(filepath)<br>print(#"\nUkuran file Parquet sangat ringkas: {file size} bytes”)<br>if __mame_ == "_main_":<br>main()'|<br><!-- End of picture text -->



<!-- Start of picture text -->
Processing triggers for man-db (2.12.0-Ubuild2) ...<br>; $ nano proses_parquet.py<br>; $ spark-submit proses_parquet .py<br><!-- End of picture text -->



<!-- Start of picture text -->
26/08/31 01:01:54 INFO DAGScheduler: Job 7 finished: showString at NativeMethodAccessorImpl.java:0, took 401.593107 ms<br>4---4----------4+----------------+-----| ID] Nama | Jurusan|Nilai|+ --------+Status]<br>4---+----------4+----------------4-----+--------+<br>| 2] Imanuel|Sistem Informasi] 90] Lulus|<br>| 1)]Christiano] Informatika] 85] Lulus|<br>| 3] Silooy| Teknik Elektro| 78] Lulus|<br>| 4l Andi] Informatika] 92] Lulus|<br>| 5] Budi| Manajemen| 65|Remedial|<br>4---4----------+----------------¢-----=== +<br><!-- End of picture text -->

- —-- Skema Data Parquet —-root |-- ID: long (nullable = true) |-- Nama: string (nullable = true) |-- Jurusan: string (nullable = true) 

|-- Nilai: long (nullable = true) |-- Status: string (nullable = true) 26/08/3126/08/31 01:01:5401:01:55 INFOINFO SparkContext:SparkUI: StoppedSparkContextSpark web isUI stoppingat http://192.168.60.118:40uU0with exitCode ® from stop at NativeMethodAccessorImpl.java:0. 26/08/31 01:01:55 INFO MapOutputTrackerMasterEndpoint: MapOutputTrackerMasterEndpoint stopped! 26/08/31 01:01:55 INFO MemoryStore: MemoryStore cleared 26/08/31 01:01:55 INFO BlockManager: BlockManager stopped 26/08/31 01:01:55 INFO BlockManagerMaster: BlockManagerMaster stopped 26/08/31 01:01:55 INFO OutputCommitCoordinator$OutputCommitCoordinatorEndpoint: OutputCommitCoordinator stopped! 26/08/31 01:01:55 INFO : SparkContext: Successfully$ ae SparkContext (Uptime: 64U65 ms) 

