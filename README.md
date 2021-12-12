# Surf's Up Analysis

## Overview
We used a SQLlite file to analyze the weather patterns on the island of Oahu to dertime if the weather would be detrimental to the plan of opening a surf and shake shop. The analysis was also put into a flask app to make it eaiser for other shareholders to read. We also pulled the temperatures for the months of June and December to ensure that this shop could be operational year round. 

### Resorces and Tools
- hawaii.sqlite file
- Jupyter Lab
- Python
- Flask
- Visual Studio Code

## Results

![dp](https://user-images.githubusercontent.com/90511014/145733318-4ea43490-8a3e-4833-a455-a17cfce23ac8.png)![jp](https://user-images.githubusercontent.com/90511014/145733377-c873551f-3fa1-48e8-b888-3e09af97bf65.png)


### Mean
- The mean temperature for June is 75.
- The mean temperature for December is 71.

### Median
- The Median temperature for June is 75
- The Median temperature for December is 71
- As both of these number are the same as the mean the temperatures are very consistent with out any outliers. 
### Minimum and Maximum
- June temperatures range from 64 to 85
- December temperatures range from 56 to 83 


![JuneDecription](https://user-images.githubusercontent.com/90511014/145729117-4cb850b8-ee28-43fd-adc6-baafb11880a8.png)![DecemberDescription](https://user-images.githubusercontent.com/90511014/145729127-9c4ed08d-0d6e-402a-b865-0c40c0f22b89.png)



## Summary
In both months the mean and median is the same this means that the temperature is consistent and not skewed and does not have any outliers. The standard deviation and the range in December is larger. While the max is only 2 degress lower the minimum is 9 degrees lower. The means that the distance from the mean is also larger. While some days in December will be as warm as June others will be much colder. Below are two further considerations. 
### June and December Precipitation

     j_p = session.query(Measurement.date,Measurement.prcp).\
        filter(func.strftime("%m", Measurement.date) == "06").all()
 

![jp](https://user-images.githubusercontent.com/90511014/145733222-a26edb46-de51-4e45-84b9-0467aa39b367.png)![jpg](https://user-images.githubusercontent.com/90511014/145733241-f7f095c0-6ff5-418e-882d-547a0e9c5b28.png)


    d_p = session.query(Measurement.date,Measurement.prcp).\
        filter(func.strftime("%m", Measurement.date) == "12").all()
   ![dp](https://user-images.githubusercontent.com/90511014/145733410-3f50540f-3f0e-4f5c-8bbb-173922c4a11c.png)![dpg](https://user-images.githubusercontent.com/90511014/145733415-6f54f93c-0ddf-404c-a49b-7bc07db49675.png)


    
### June and December Precipitation by Station
    j_p_s = session.query(func.avg(Measurement.prcp), func.min(Measurement.prcp),func.max(Measurement.prcp), Measurement.station).\
        filter(func.strftime("%m", Measurement.date) == "06").\
        group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()
        ﬁ
   ![jps](https://user-images.githubusercontent.com/90511014/145733571-80c3de3f-b406-4381-ba56-7f13970d2b4f.png)

        
    d_p_s = session.query(func.avg(Measurement.prcp), func.min(Measurement.prcp),func.max(Measurement.prcp), Measurement.station).\
        filter(func.strftime("%m", Measurement.date) == "12").\
        group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()  
![dps](https://user-images.githubusercontent.com/90511014/145733518-e5aade88-7349-40f1-be17-bd9f73b9564f.png)

        
