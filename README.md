# runtime_railway
Runtime estimation for Railway Timetabling

Estimation of runtime for proper railway timetabling is important for judicious use of railway resources.

The sharing of data files is not allowed due to strict instructions from Konkan Railway Officials. The codes would not run
without the data files. However the codes can be read to know how Central Limit Theorem and Maximum Likelihood estimation are implemend in
python.

Calculated runtime means runtime calculated by CLT and MLE
Computed runtime mean runtime computed for KRCL
WTT runtime means runtime present in working timetable

Inside the performance evaluation folder of the reprository:
Individual_train_cal: file calculates runtime of each train in one block section by first removing the outliers then generate a CLT data
which has less standard deviation and a parametric distribution (its parameter can be found). Next we fit a t-distribtuion to it and using
this parameter generate new points (no of points = no of CLT points). Now maximum of this t-dist is set as runtime to be alloted. But if no. of points > 100 we add 10% and give ceiling value if first decimal value is 3 and reduce 10% if points less 100 and apply ceiling if first decimal value is 5. This was done b/c >100 points have low std. dev. and <100 have large std. dev.

We save the values as cal_d i.e. runtime calculated for down direction

Individual_train_comp: file takes the computed runtime for that halt type in WTT and save in comp_d etc

Individual_train_mode_value: same thing for mode of realised runtime and save as mode_d etc.

Individual_train_save_comparison_1point5: it calculates the mean delay for each train in each block section for calculated runtime
computed runtime, mode assigned as runtime and WTT time. And save these as cal_u_delay.csv, comp_u_delay, mode_u_delay, wtt_u_delay etc.
Here delay was calculated using runtime was subjected to 1.5 quantile outlier removed data

Individual_train_save_comparison_3per: .....3 quantile of data. But runtime was always calculated using 1.5 quantile of data.

Individual_train_save_comparison_1point5: compare the computed, mode and wtt runtime as excess percentage of delay of calculated runtime.

Note: files will be updated with comments soon
