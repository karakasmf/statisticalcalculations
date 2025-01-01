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

tp = [];
fp = [];
fn = [];
tn = [];

for i=1:size(conf_mat, 1)
        tp(i)=conf_mat(i,i);
        fp(i)=sum(conf_mat(:,i))-conf_mat(i,i);
        tn(i)=sum(conf_mat(:))-sum(conf_mat(i,:))-sum(conf_mat(:,i))+conf_mat(i,i);
        fn(i)=sum(conf_mat(i,:))-conf_mat(i,i);
end

% Consusion Matrix Statistical Calculations

prec = tp ./ (tp + fp); % precision
sens = tp ./ (tp + fn); % sensitivity, recall
spec = tn ./ (tn + fp); % specificity
acc = (tp + tn)  ./ (tp + fp + tn + fn); % accuracy
f1 = (2 .* prec .* sens) ./ (prec + sens); % f1score


% Table Row Names
name = ["true_positive"; "false_positive"; "false_negative"; "true_negative"; ...
    "precision"; "sensitivity"; "specificity"; "accuracy"; "F-measure"];

% Table Column Names
varNames = ["name"; "classes"];

% Each Class Values
values = [tp; fp; fn; tn; prec; sens; spec; acc; f1];

% OUTPUT: final table
stats = table(name, values,'VariableNames',varNames);
if verbose
    stats
end
end
