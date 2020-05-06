# KSU fertility calculator

__Name:__ Bryan Rutter  
__Semester:__ Spring 2020  
__Project Area:__ Soil Fertility/Agronomy  

## Objective:

Create function(s) that automate the calculation of lime and fertilizer application rates based on soil test results from the KSRE Soil Testing Laboratory.

## Rationale:

Fertilizer ammendments are often required to correct nutrient deficiencies in agricultural production systems. Over-fertilization increases the risk of eutrophication of surface water, while under-fertilization can lead to reduced crop yield, quality, and farm profitability. Fertilizer application rates are often based on a yield goal or in-season estimate of yield potential, but should be guided by soil tests to improve their accuracy when possible. However, these calculations may involve several variables and may be cumbersome to calculate by hand. The KSRE Soil Testing Lab provides soil testing services and fertilizer recommendations to Kansas homeowners and producers. Fertilizer recommendations are reported via PDF and excel documents which are computed and compiled by proprietary third-party software. The equations used to calculate fertilizer application rates are freely available, but third party software can often be a _black box_ and may be difficult to troubleshoot for lab employees to diagnose. Creating a Python program to automate these calculations could serve as a useful validation and troubleshooting tool for lab workers, and make it easier to commonicate potential problems with the STRS software developers.

# Function inputs

Input data consists of a combination of user inputs and soil measurements. Soil measurements include soil pH, buffer pH, soil organic matter, and plant available-P, -K, and -N, and must be imported as a csv file generated by the lab's data management system. Context parameters including tillage practice, crop type, yield goal, and sampling depth are also required. Equations used to compute fertilizer application rates are sourced from the KSU Fact Sheet MF-2586. Note: Recent changes to the STRS software allow for tillage, crop type, yield goal, and sampling depth to be exported with soil test data directly by STRS. The only user input required is whether to save the output or not.

# Function input variable descriptions
_OrderNo_: The order number for a particular customer's samples. Used for lab reference only.  
_LabNo_: The lab number assigned to each soil sample. Used for lab reference only.  
_Crop_: String or factor indicating the intended crop to be grown (e.g. "Corn", "Soybeans", etc.)  
_YieldGoal_: Numeric value providing an estimation of average yield potential of the intended for the specific field  
_Tillage_: String or factor indicating what tillage management practices are employed.  
_PrevCrop_: String or factor indicating the previously grown crop. Used to adjust N-rate calculations.  
_OM_: Numeric value representing the soil organic matter concentration of the soil (%). Required for N-rate calculations.  
_NO3_: Numeric value representing the KCl extractable nitrate content of the soil (ppm or mg kg^-1^). Required for N-rate calculations.  
_P_: Numeric value representing the concentration of Bray-1 or Mehlich-3 extractable P in the soil (ppm or mg kg^-1^). Required for P fertilizer rate calculations.  
_K_: Numeric value representing the concentration of ammonium acetate or Mehlich-3 extractable K in the soil (ppm or mg kg^-1^). Require for K fertilizer rate calculations.  
_pH_: Numerica value representing the pH of the soil.
_BUFpH_: Numerical value representing the Sikora buffer pH of the soil. 

# Function output variable descriptions

_OrderNo_: The order number for a particular customer's samples. Used for lab reference only.  
_LabNo_: The lab number assigned to each soil sample. Used for lab reference only.  
_Crop_: The intended crop to be grown (e.g. "Corn", "Soybeans", etc.)  
_LimeApp_: Lime application rate as computed by STRS (lbs 100% ECCE aglime ac^-1^)  
_Lime_rec_KSU_: Lime application rate according to MF-2586  
_NApp1_: Nitrogen application rate computed by STRS (lbs N ac^-1^)  
_N_KSU_Rec_: Nitrogen application rate according to MF-2586  
_P2O5App_: Phosphorus application rate computed by STRS (lbs P2O5 ac^-1^)  
_P2O5_Rec_KSU_: Phosphorus application rate according to MF-2586 (lbs P2O5 ac^-1^)  
_K2OApp_: Potassium application rate computed by STRS (lbs K2O ac^-1^)  
_K2O_Rec_KSU_: Potassium application rate according to MF-2586 (lbs K2O ac^-1^)  

## Sketch
<img src="Project_schematic.png" alt="workflow" width="750"/>

## References

Agronomy Department, Kansas State University (2015). _Soil Test Inerpretations and Fertilizer Recommendations (MF-2586)_. Retrieved from https://bookstore.ksre.ksu.edu/pubs/mf2586.pdf

Missouri Agricultural Experiment Station SB 1001 (2015). _Recommended Chemical Soil Test Procedures for the North Central Region (NCERA No. 221-Revised)_. Retrieved from https://extensiondata.missouri.edu/pub/pdf/specialb/sb1001.pdf