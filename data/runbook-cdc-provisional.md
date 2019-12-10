### Runbook to extract and transform CDC Provisional Data

- Provisional data and CDC Wonder data differ in the following ways: https://www.cdc.gov/nchs/nvss/vsrr/drug-overdose-data.htm#differences_between_final_and_provisional_data
- There are some more differences:
  - Prov data captures yearly rolling totals of deaths
  - It includes data for all the months. CDC does not.
  - It uses a different code for Month, Year and Data Values than from how CDC WONDER reports it.
- So to use Prov data along with CDC, we needed to convert it to a form that's usable uniformly


Aim:
Calculate the deaths counts in Prov data for 2018 and 2019 using rolling year deltas and actual counts from CDC Wonder data for 2017. This is also explained in proj report 2

Steps:
1) Arrange Prov data by tuple of (Year, State Name, Month) - done in excel
2) Sort the CDC Wonder Data also by Year, State and Month 
3) Fill in all skipped months with the value 0: Code (https://github.com/vaguiar/capstone-project-2019/blob/master/src/explore/Normalize_2017_data.ipynb)
4) Copy over months in 2017 in the Prov data setup in 1
5) Extract deaths using the formula: (Also explained in Proj Report 2)
  ```
  extracted monthly deaths in Jan ‘18 = 
    provisional 12 mth data ending in Jan’18 - 
      (provisional 12 mth data ending in Dec ‘17  - CDC data for Jan ‘17)
  ```
  
The final version of our normalized data for 2017 - Apr 2019 is here: https://drive.google.com/drive/folders/1ACnl1VX7SD5Vf5G_fDcClVMpM2vHFWh1

We've then grouped by regions to get regional data here:
https://drive.google.com/drive/folders/1ACnl1VX7SD5Vf5G_fDcClVMpM2vHFWh1
