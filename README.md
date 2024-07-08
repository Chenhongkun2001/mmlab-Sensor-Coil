# mmlab-Sensor-Coil

## Introduction

Inductive_displacement_sensor.epro is PCB based on LDC1612.  .epro means it is Jia-Li-Chuang EDA file, you have to use Jia-Li-Chuang to open it.  If you don't have this EDA, I put the schematic underneath, this schematic is refer to [Seeed studio](https://wiki.seeedstudio.com/Grove-2_Channel_Inductive_Sensor-LDC1612/).

![image-20240708154404527](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708154404527.png)



![image-20240708154419859](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708154419859.png)

Sensor_colis_examples.epro is sensor coils examples, this file obtains certain classic coil design, you can choose a proper coil according to your motor. If you want more, please utilize TI's calculator: [Coil Designer (ti.com)](https://webench.ti.com/wb5/LDC/#/spirals) . This calculator can help you derive the proper coils in Altium Designer or Cadence Allegro and so on. 

LDC1612_user_manual.pdf is TI's LDC1612/LDC1614 user manual, I put here to offer users to consult.

##  [Coil Designer (ti.com)](https://webench.ti.com/wb5/LDC/#/spirals) basic tutorial

1. When you click into this address, it should be look like this :

<img src="C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708155722639.png" alt="image-20240708155722639" style="zoom:50%;" />

2. Select LDC part : LDC1612 or LDC1614 (the difference between LDC1614 and LDC1612 is just the number of coils they can approve, LDC1614 can approve 4 coils in the same time, rather than 2 coils LDC1612 approve). We recommend select circular coil type, as this type can offer consistent accuracy and breadth.

   ![image-20240708160121956](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708160121956.png)

   3. Slide down, here you can select the parameters you want to design, of course, within a reasonable range, when beyond a reasonable range, the calculator will display red or orange in a column, warning you should not do this, at this time you just need to adjust some parameters to get a reasonable coil. You can also click on view more to see more parameters, here we recommend you click on view more.

      ![image-20240708160559013](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708160559013.png)

      ![image-20240708160616131](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708160616131.png)

      

      ![image-20240708160700816](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708160700816.png)

      ![image-20240708160741121](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708160741121.png)

   4. After correctly designing, you need to click on the right column.(If not properly designed, the left table still has red or orange columns, will not be able to perform the next operation), export your design, here we choose is Altium Designer.

      ![image-20240708161006835](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708161006835.png)

      ![image-20240708161052196](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708161052196.png)

      5. Click export, wait patiently for a while (please note that your network connection must be normal at this time), the following window will pop up, click download, your design will be downloaded in the form of a compressed package.

         ![image-20240708161220005](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708161220005.png)

         6. You can also view the physical properties of the coil you designed, and you can select the physical meaning of the x-axis and y-axis.

![image-20240708161552102](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708161552102.png)

## The problem you may face during learning and using

- **The coils that exported from Coil Designer can't be utilized **

- Solution: The coils that exported from Coil Designer look like this, the right side is the information of coil you have designed: 

  ![image-20240708163643026](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708163643026.png)

  

  At this time, we can see that the upper and lower layers of the coil have formed a open circuit because there is no hole, and the coil cannot work normally. At this point we only need to add holes where we want to change layers. After adding holes, the coils can work perfectly.

  ![image-20240708163743948](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708163743948.png)

  ![image-20240708163916315](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708163916315.png)

  

- **The address of LDC1612 or LDC1614 is uncertain.** 

- You must set the pull-up (access 3.3V) or pull-down (access GND) on the ADDR pin of LDC1612 or LDC1614, **must not float**. To be specify,  When the ADDR pin of LDC1612/LDC1614 is set low, the device I2C address is 0x2A; when the ADDR pin is set high, the I2C address  is 0x2B. So, when user design the hardware, this address is fixed.  In beneath figure and whole project, we use address 0X2B.

  ![image-20240708164346000](C:\Users\ChenHongKun\AppData\Roaming\Typora\typora-user-images\image-20240708164346000.png)
