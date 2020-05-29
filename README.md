# Introduction

Detect malicious TLS flows by Machine Learning.

# How to use

1. install [scikit-learn](https://scikit-learn.org/stable/)、[LightGBM](https://github.com/microsoft/LightGBM) and the newest [tensorflow](https://www.tensorflow.org/)
2. install bro: sudo apt install bro  
Suppose that you are analyzing a pcap file, and you find that a TLS flow is suspected.
3. bor -r *.pcap and generate log files
4. create a folder named *dataset*
5. in the *dataset* folder,  create a folder named *Malicious*
6. in the *Malicious* folder, create a folder named anyting. For example, we create a folde named *2020-04-15-Hancitor-infection-2nd-run*, just the same as the analyzed pcap file name.
7. in the *2020-04-15-Hancitor-infection-2nd-run* folder, create a floder named *bro*
8. copy all log files (x509.log、ssl.log、dns.log and conn.log) to the folder *bro*
9. in the floder  *bro*, create a text file named *IPadr.txt*
10. in the *IPadr.txt*,  we add contents  as:  
Malicious  
IP address  
the IP address is the dst IP address of the suspected flow.

11. run feature_extract/__label__.py
12. run feature_extract/__main__.py
13. run detection/detect_lightGBM.py or detection/detect_randomforest.py

# Results
For the TLS flow (dst IP address is 166.62.28.102)  in  *2020-04-15-Hancitor-infection-2nd-run.pcap*, the virustotal checking result is:
![VirusTotal checking result](https://github.com/HeGaofeng/malicious-TLS-detection-by-ML/blob/master/virustotal.jpg)

The detection result of lightGBM is:
![Detection result of lightGBM](https://github.com/HeGaofeng/malicious-TLS-detection-by-ML/blob/master/detect-result.jpg)

