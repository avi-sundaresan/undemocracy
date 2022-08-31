# Undemocracy

This project aims to predict the outcome of US Congressional elections based on per-district *demographics* and *incumbency* information alone, with no polling data whatsoever. The highest performing NAS-generated MLP yields a 97% val accuracy on the dataset. 

## The data

The data directory hosts the raw data for the project. The historical election results data was obtained from MIT Election Lab (see citation below). 
The data_curation directory hosts the data preprocessing notebook and the fully-processed data CSV. 

MIT Election Data and Science Lab, 2017, "U.S. House 1976–2020", https://doi.org/10.7910/DVN/IG0UN2, Harvard Dataverse, V11, UNF:6:ry6R0P1KRBhWkIfZzKiM8A== [fileUNF]. 

## The models

The models can be found in the notebooks directory. I use a logistic regression as a baseline (which has mediocre performance, perhaps unsurprisingly), and compare it to a vanilla MLP, which significantly improves performance (by ~30%). 

## Neural Architecture Search 

I used a neural architecture search (NAS) to find the best performing MLP structure on the dataset. The NAS uses an LSTM RNN controller to generate potential (encoded) MLP architectures (constrained to 3 layers and <48 neurons), which are then trained for a few epochs on the dataset. The val accuracies of the generated architectures are incorporated in a loss function based on the REINFORCE gradient, which informs the training of the controller. Credit to Anuj Sable's Paperspace post for the source code: https://blog.paperspace.com/overview-of-neural-architecture-search/. 






