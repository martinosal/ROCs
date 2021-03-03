# ROCs

ROC_maker

To run it: 

open a new jupyter-notebook in the same directory of the ROC_maker.ipynb, with:

jupyter-lab

then add the following line:

%run ROC_maker.ipynb

To produce ROCs, first of all set a path pointing to your file 
(it has to be a file processed by my root DAOD_selector, see https://github.com/martinosal/root_selector).

So, add the following line in your notebook:

path='<your_path_to_file>'

file='<actual_name_of_the_file>'

algos=[0,1,1,1,0,1]#ip2d,ip3d,rnnip,sv1,jf,DL1

The latter alg list tells the ROC_maker to produce data for ip3d,rnnip,sv1,dl1. For other custom configurations you need small modifications to the ROC_maker; please contact me.

To run the ROC_maker just:

ROC_collection=algs(path,file,algos)

This will create the objet "ROC_collections" with all the data you need; it may take a while to finish its job. Don't worry if it gives the "divide by zero" warning.

Now you can produce the plots with

x_int=[0.4,0.9]

roc_lrej(ROC_collection,'<name_of_you_collection>',x_int)


This will produce the light-jet rejection ROC in the interval [0.4,0.9]. For c-jet rejection just use the roc_cjet equivalent function.

To produce comparison plots you need to run at least twice the algs class on two different files file1 and file2, namely:

ROC_collection_1=algs(path,file1,algos)

ROC_collection_2=algs(path,file2,algos)

Then:

rec_lconf(ROC_collection_1,'<name_of_you_collection_1>',ROC_collection_2,'<name_of_you_collection_2>',x_int)

rec_cconf(ROC_collection_1,'<name_of_you_collection_1>',ROC_collection_2,'<name_of_you_collection_2>',x_int)
