# Explaining the purpose of the notebooks found in VIRA_beg_classifier/Notebooks.

# session2_HW.ipynb
This notebook did not actually contribute anything to the goal of classifier training, but in it I learned how to load audio and opensoundscape, load raven selection tables, visualize audio (both .mp3 and .WAV, field and target recordings).
# Extract_targetneg_XC_snapshot.ipynb  
This notebook was mostly writen by Satiago Ruiz Guzman, with small edits for functionality by me. This notebook was modified from Santiago's original notebook to work with my goal of providing a specific list of species I want from the Xeno Canto Birdset Snapshot. In this notebook I create a .pkl file with my BirdSet clip negatives.
# homework2_onehotfiles.ipynb  
This notebook copies a lot of code from session2_HW.ipynb, but critically includes cells where I make the .pkl file in one-hot format for my positives. 
# combine_negpos_pkl2.ipynb 
In this notebook I combine the posiitve and negative data frames created in te previous two notebooks, plus doing a bunch of checks on the dataframes to make sure everything looks right. This merge did require some adding of columns and inserting NA values.
# grab_field_negatives.ipynb 
Sam suggested I add some negatives from field data, so I did that in this notebook by generating a list of random field audio files from rloc2025a, one from each recorder, then creating a .pkl file with each hour split into 1.5 second chunks, then matching the df format of the train and val dfs. Finally, I integrate that field_negatives.pkl into my existing dataset (at that point, /home/brg226/projects/vira_beg/training_data/update1_fulltrain.pkl). This resulted in my final data frame ready to be split, /home/brg226/projects/vira_beg/training_data/update2_fulltrain_with_field.pkl. 
# dataset_split_attempt2.ipynb 
As you can probably guess, attempt 1 didnt go so well, so I started over in a new notebook. In this notebook I split my big boy data frame into a train and validation data frame for classifier training. The challenge here was to ensure splitting was not done on the recording level, and also manually assign audio files to the val dataset ensuring that recordings of the same bird did not end up in the val dataset, since there is only three (lol rip). Also had to slim the train and val df to just one "virail" column and not a column for each XC species.
# upsample_Train_01.ipynb  
Steps in this notebook:
1. Set multi-index on train and val df
2. Upsample positives in train df
3. Create CNN object
4. Visualize tensors
5. Train model (and initiate WandB logging) 
This notebook was used for the first training attempt on December 3rd, 2025.


  
