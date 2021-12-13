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


![jtg](https://user-images.githubusercontent.com/90511014/145742245-dc42a20f-8837-473c-87ce-3ae6021eb6d1.png)![dtg](https://user-images.githubusercontent.com/90511014/145742255-edbe8a2e-df70-4f3e-a285-bf00fd1ac706.png)


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


![JuneDecription](https://user-images.githubusercontent.com/90511014/145742297-48b461ad-042a-4301-8537-68aecb323a77.png)![DecemberDescription](https://user-images.githubusercontent.com/90511014/145742303-b1e80277-f7de-4768-b17a-0e687eeb386c.png)






## Summary
In both months the mean and median is the same this means that the temperature is consistent and not skewed and does not have any outliers. The standard deviation and the range in December is larger. While the max is only 2 degress lower the minimum is 9 degrees lower. The means that the distance from the mean is also larger. While some days in December will be as warm as June others will be much colder. Below are two further considerations. 
### June and December Precipitation

     j_p = session.query(Measurement.date,Measurement.prcp).\
        filter(func.strftime("%m", Measurement.date) == "06").all()
 

![jp](https://user-images.githubusercontent.com/90511014/145733222-a26edb46-de51-4e45-84b9-0467aa39b367.png)![jpg](https://user-images.githubusercontent.com/90511014/145733241-f7f095c0-6ff5-418e-882d-547a0e9c5b28.png)


    d_p = session.query(Measurement.date,Measurement.prcp).\
        filter(func.strftime("%m", Measurement.date) == "12").all()
   
 ![dp](https://user-images.githubusercontent.com/90511014/145742661-96371cf2-7a2d-4f5a-8856-c08cb9232f8e.png)![dpg](https://user-images.githubusercontent.com/90511014/145742498-c29c2251-f088-48fd-aa01-75739c08778d.png)


The above queries shows the precipitation in June and December. For the most part it is low participation but there are some outliers that are a bit higher. December also has a slightly higher precipitation that June. This shows that rain should not be an issue.  
    
### June and December Precipitation by Station
    j_p_s = session.query(func.avg(Measurement.prcp), func.min(Measurement.prcp),func.max(Measurement.prcp), Measurement.station).\
        filter(func.strftime("%m", Measurement.date) == "06").\
        group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()
        ﬁ
   ![jps](https://user-images.githubusercontent.com/90511014/145733571-80c3de3f-b406-4381-ba56-7f13970d2b4f.png)!


        
    d_p_s = session.query(func.avg(Measurement.prcp), func.min(Measurement.prcp),func.max(Measurement.prcp), Measurement.station).\
        filter(func.strftime("%m", Measurement.date) == "12").\
        group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()  
![dps](https://user-images.githubusercontent.com/90511014/145733518-e5aade88-7349-40f1-be17-bd9f73b9564f.png)


The above queries show the precipitation by station. Station USC00519397 has an average precipitation of .02 in June and .07 December. This is the lowest average and the best location to open the shop. 
        
