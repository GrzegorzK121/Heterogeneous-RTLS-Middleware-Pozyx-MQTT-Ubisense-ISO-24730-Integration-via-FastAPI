# Hardware-Setup-Physical-Infrastructure-RTLS

## 🛠️ Hardware Infrastructure & Real-World Setup

This project wasn't just about writing software—it required extensive physical engineering, hardware modifications, and precise spatial calibration in a real-world test environment. 

Below is a behind-the-scenes look at the deployment of the heterogeneous RTLS infrastructure:

### 1. Precision Calibration
![Precision Calibration Room](IMG_1162.jpg)
*Setting up the reference coordinate system. A green laser level was used in the calibration room to ensure millimeter-perfect alignment and geometry for the RTLS anchors.*

### 2. Hardware Modifications
![Server PC Soldering](IMG_1390.jpg)
*The central server PC required custom hardware modifications. Here, I am soldering a voltage booster to ensure stable power delivery for the system components.*

### 3. Network Infrastructure
![PoE Switch](IMG_1371(1).jpg)
*A dedicated PoE (Power over Ethernet) switch installed in the suspended ceiling to power and connect the UWB tracking nodes.*

### 4. Ubisense Node Deployment
![Ubisense Node](IMG_1375.jpg)
*One of the Ubisense Dimension4 sensors mounted to the ceiling infrastructure in the test corridor.*

### 5. Pozyx Node Deployment
![Pozyx Nodes](IMG_9569.jpg)
*Pozyx UWB anchors mounted near the window in the test area, completing the heterogeneous hardware setup.*

### 6. Dynamic Movement Simulation
![Tag on a Fan](IMG_1433.jpg)
*To test the custom handover algorithm and system responsiveness, a Ubisense tag was attached to a rotating fan mounted on a surveying tripod. This creative solution provided consistent, predictable dynamic movement for testing the data pipeline.*

### 7. Software Configuration & Mapping
![Ubisense Config](image_719a1d.jpg)
*The Ubisense Location System Config software displaying the mapped 2D test corridor and monitoring real-time location events.*
