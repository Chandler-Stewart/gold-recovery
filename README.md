# Gold Recovery

This project focuses on an end-to-end project where we are given a specific industrial process that may not be fully understandable to someone without some level of subject matter expertise; however, it can prove that the computer model should be able to out perform the model creator.

We have information on over 16,000 observations of gold recovery parameters. We also have a testing dataset that we have nearly 6,000 setup example processes to predict.

## What to know about this project:

**The Aim** - The goal of this project is to create a model that will predict the amount of gold recovered from gold ore based on process parameters.

Strategies include:
- Data Preprocessing
- Exploratory Data Analysis
- Linear Regression
- sMAPE Evaluation

## The Gold Recovery Process

The process starts with foltation where a gold ore mixture is fed into float banks to obtain rougher Au concentrate and rougher tails (product residues with a low concentration of valuable metals).

Then the rougher concentrate undergoes two stages of purification. After purification, we have the final concentrate and new tails.

**Technological process**
- Rougher feed — raw material
- Rougher additions (or reagent additions)
    - Xanthate — promoter or flotation activator
    - Sulphate — sodium sulphide for this particular process
    - Depressant — sodium silicate.
- Rougher process — flotation
- Rougher tails — product residues
- Float banks — flotation unit
- Cleaner process — purification
- Rougher Au — rougher gold concentrate
- Final Au — final gold concentrate

**Parameters of stages**
- air amount — volume of air
- fluid levels
- feed size — feed particle size
- feed rate

## Functions
**Recovery**:
$`\begin{equation}
Recovery = \frac{C\times(F-T)}{F\times(C-T)} \times 100\%
\end{equation}`$

where:  
C — share of gold in the concentrate right after flotation (for finding the rougher concentrate recovery)/after purification (for finding the final concentrate recovery)  
F — share of gold in the feed before flotation (for finding the rougher concentrate recovery)/in the concentrate right after flotation (for finding the final concentrate recovery)  
T — share of gold in the rougher tails right after flotation (for finding the rougher concentrate recovery)/after purification (for finding the final concentrate recovery)

**sMAPE**:

The evaluation metric will be symmetric Mean Absolute Percentage Error, or sMAPE

$\begin{equation}
sMAPE = \frac{1}{N}\sum_{i=1}^{N}\frac{|y_i-\hat{y_i}|}{(|y_i| + |\hat{y_i}|)/2}
\end{equation}$

where:  
$N$ — number of observations  
$`y_i`$ — Value of target  
$\hat{y_i}$ — Value of prediction  

$\begin{equation}
\text{Final sMAPE} = 25\% \times \text{ sMAPE(rougher) } + 75\% \times \text{ sMAPE(final) }
\end{equation}$  

**The Data** - The data files below is where our input for the project comes from. The files contain different non-identifying information on people associated with their phone and internet contracts. The following characteristics are in the file:

The `gold_recovery_train.csv` table - contract information  
The `gold_recovery_test.csv` table - the client's personal data  
The `gold_recovery_full.csv` table - information about Internet services  

The feature nomenclature is as follows:
`[stage].[parameter_type].[parameter_name]`

Possible values for `[stage]`:  
*rougher* — flotation  
*primary_cleaner* — primary purification  
*secondary_cleaner* — secondary purification  
*final* — final characteristics  

Possible values for `[parameter_type]`:  
*input* — raw material parameters  
*output* — product parameters  
*state* — parameters characterizing the current state of the stage  
*calculation* — calculation characteristics  
