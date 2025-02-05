[Artificial Intelligence for Robotics II](https://corsi.unige.it/en/off.f/2022/ins/60237?codcla=10635)<br>
[M.Sc Robotics Engineering](https://corsi.unige.it/corsi/10635)<br>
[University of Genoa (UniGe)](https://unige.it/en)<br>
**Supervisor:** [Prof. Fulvio Mastrogiovanni](https://rubrica.unige.it/personale/UkNHWFhr) & [Prof. Antony Thomas](https://scholar.google.it/citations?hl=it&user=aPSLBVUAAAAJ)

# AI4RO2_Assignment2: Task and Motion Planning for Robotics in Coffee Shop Scenario

The work is based on Task and Motion Planning which involves the demon- stration of a coffee shop. This deals with the movement of a mobile robot in a constrained environment.

* Requirements for the assignment [click here](https://github.com/ankurkohli007/Artificial_Intelligent_4_Robotics_2_Assignment_II/blob/master/Task%20Motion%20and%20Planning%20Assignemnt_Group%20I_Ankur%20Kohli_Awais%20Tahir_Subhransu%20Sourav%20Priyadarshan/Assignment2.pdf).
* Report of the assignment [click here](https://github.com/ankurkohli007/Artificial_Intelligent_4_Robotics_2_Assignment_II/blob/master/Task%20Motion%20and%20Planning%20Assignemnt_Group%20I_Ankur%20Kohli_Awais%20Tahir_Subhransu%20Sourav%20Priyadarshan/Task%20Motion%20and%20Planning%20Assignemnt_Group%20I_Ankur%20Kohli_Awais%20Tahir_Subhransu%20Sourav%20Priyadarshan_Report.pdf).

## Before building the project - dependencies

Before running the project make sure the dependencies on the system.

**Compatibility**

The project is compatible with the ***Ubuntu version*** ***16.04*** & ***18.0***. To instal **Ubuntu 16.04** follow the [link](https://ubuntu.com/tutorials/install-ubuntu-desktop-1604#1-overview) and for **Ubuntu 18.04** follow the [link](https://ubuntu.com/tutorials/install-ubuntu-desktop-1804#1-overview). It doesn't work with **Ubuntu 20** or later version because of lack of retro-compatibility with some components needed to build and run the project.

## Popf-tif Planner

The project uses the extensible temporal planner **popf-tif**. Here is the link to the [repository](https://github.com/popftif/popf-tif) to install the popf-tif planner. 

## Troubleshooting during installation 

* Here are the links to troubleshoot the errors which will incurs while installing the planner.
      <ul>
      <li>[Link 1](https://github.com/popftif/popf-tif/issues/2)</li>
      <li>[Link 2](https://github.com/popftif/popf-tif/issues/1)</li>
      </ul>

## Building and Running

## Building

Clone the project from the the given repository [link](https://github.com/ankurkohli007/Artificial_Intelligent_4_Robotics_2_Assignment_II.git). 

After cloning, 

* Configure the sources for building the project given below:
```sh
cd planner/src
./build-instructions.txt 
```

* Build the planner:
```sh
cd ../release
make popf3-clp 
```
After compiling the *popf-tif planner* there will be an executable ***popf3-clp*** is created in the folder popf.

## Running

Once bulding is done, now runn the planner by the following command:

```sh
./popf3-clp dom1.pddl prob1.pddl
```

To run the planner with the external solver:
```sh
./popf3-clp -x domainfile problemfile externalsolver [inputexternalsolver]
```

In our case, command to run the external solver is given below:
```sh
./popf3-clp -x /home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/domains/visits_domain/dom1.pddl /home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/domains/visits_domain/prob1.pddl /home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/modules/visitmodules/build/libVisits.so /home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/domains/visits_domain/region_poses
```
In the aforementioned command, ```/home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/domains/visits_domain/dom1.pddl``` is the path of *domain file* whereas, ```/home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/domains/visits_domain/prob1.pddl``` is the path of *problem file*. Also, ```/home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/modules/visitmodules/build/libVisits.so``` is the path of external solver which contains ```.so``` file and lastly, ```/home/ankurkohli007/Desktop/AI4RO2/popf-tif/popf-tif/domains/visits_domain/region_poses``` is the path of file *region_poses* file which contain the mapping from a region to its corresponding waypoint.

## Expected Results

By using the default PDDL problem and domain file here presented the default scenario, the results obtained from the planner "popf-tif" is given below:

![alt text](image1.png)

After making a few changes , we get the following results:

![alt text](image2.png)

In figure below the change in cost value by the default scenario code (code givem as requiremnet file). In figure above the cost is 0.0 and after changes cost is 8.0 as shown in figure below:

![alt text](image3.png)

But tuning the distance-euc function in VisitSolver.cpp we calculated the actual cost i.e. Euclidian Distance between the two regions as shown in figure above.

Finally, after calculation euclidian distance between two regions and we got the final distance in the terms of cost i.e. 10.485 which is shown below in figure:

![alt text](image4.png)
