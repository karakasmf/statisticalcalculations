# statisticalcalculations
Statistical Calculations From Confusion Matrix MATLAB

function stats = statisticalcalculations(conf_mat, verbose)

% % % % % % % % % % INPUTS % % % % % % % % % % 
% conf_mat -> Computed confusion matrix Matlab Function
% conf_mat=confusionmat(known_labels,predicted_labels);
% verbose -> For showing geneterated table in command window
% if verbose= 1 show in command window
% if verbose= 0 no show in command window

% % % % % % % % % % OUTPUT % % % % % % % % % % 
% stats 
% Table of statistical calculations class based
% tp
% fp
% tn
% fn
% precision
% sensitivity
% specifity
% accuracy
% f1 score
