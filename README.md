# Convert curve image to timestamp-points
This test aims to convert curve images into timestamped points, it may helpping in data analysis during its early stages when the data source is not yet ready.

----------------------------

 

## **Step 1: Prepare the curve image.**  
The image can be a photo of a hand-drawn curve or one captured from a webpage. If necessary, adjust the brightness and contrast using FastStone or other apps. If you're proficient with Pillow, you can automate these adjustments using your own formula. 

 
<p align="center">
<img src=<./Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/after recg.jpg width="600" >
<b>


## Step 2: Convert image to points 
>### 2.1 Image Recognition
>>The img_recg() function will generate points from the image. The number of points and their positional accuracy depend on the size of the picture. Typically, this will create thousands of    points. The number of points can be controlled by using:
  curve_coordinates = random.sample(list(curve_coordinates), max_points)


<p align="center">
<img src=./image/2.1a%20read%20points%20from%20csv.jpg width="600" >
<b>
<p align="center">
<img src=https://github.com/Plus-1000/Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/2.1%20read%20points%20from%20csv.jpg width="600" >
<b>

>>As I am not proficient in NumPy, all data functions are processed using pandas.

>>The recognized points plotted as below:


  
> ### 2.2 Delete Repeated Points
>> The del_extra() function will remove points whose X coordinates are the same as their neighbors.


<p align="center">
<img src=https://github.com/Plus-1000/Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/2.2a%20create%20splines%20from%20points.JPG width="600" 
<br/>

>>The sorted points plotted as below:
 
<p align="center">
<img src=https://github.com/Plus-1000/Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/2.2%20create%20splines%20from%20points.JPG width="600" >
</p>

<br/>

> ### 2.3 Point 2D Interpolation
>>X_step is the total number of points we ultimately want, which may differ from the number of points obtained from the previous process. At this stage, we introduce 2D point interpolation to achieve the desired number of points.

<b>
<p align="center">
<img src=https://github.com/Plus-1000/Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/2.3%20create%20through%20curves%20face%20from%20splines.jpg width="600" >
</p>

<b>

  >> x_new = np.linspace(x_array.min(), x_array.max(), steps)
>  > <br>
  >> f= interpolate.interp1d(x_array, y_array,kind="cubic")   ['linear','zero', 'slinear', 'quadratic', 'cubic']
>  > <br>
  >> y_new=f(x_new)


> ### 2.4 point coordinate value re-scale
>> The function will rescale point coordinate range, by X_start, X_end in X axis and  Y_start, Y_end in Y axis: 

<p align="center">
<img src=https://github.com/Plus-1000/Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/2.4%20face%20offset.jpg width="600" >
<br>


>>After All Steps, the point coordinates are written to current_folder/04_after_scale.csv.





## Step 3: Verify Points
Open the CSV file with Excel to double-check the points.

<p align="center">
<img src=https://github.com/Plus-1000/Learn-NX-Open-and-adaptive-machining-from-egg-engraving/blob/main/image/3%20compare%20toolpaths.jpg width="600" >


<br/>



Hope you like this try, for comments or suggestions, please leave messages at wjian88@gmail.com. Thank you.  

Wang Jian, 2024 Mar 30.    








