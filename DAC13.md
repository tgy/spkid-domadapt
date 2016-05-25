This folder contains Matlab workspaces with the ivectors (600 dim) that were
computed using only SWB data for the UBM and T matrix. All is done in a gender
independent way.

- The development i-vectors from out-of-domain are in:

    + SWB-hyper_data.mat -> Full set of SWB i-vectors

    + SWB-hyper_data_2phn.mat -> Reduced set with only the i-vectors from 2
    telephone numbers per speaker. This is lists makes it harder to estimate
    within-class variability.

    + SWB-hyper_data_1phn.mat -> Reduced set with only the i-vectors from 1
    telephone number per speaker. This is lists makes it very hard to estimate
    within-class variability.

- The development i-vectors from in-domain are in:

    + SRE-hyper_data.mat -> Full set of SRE i-vectors

    + SRE-hyper_data_2phn.mat -> Same explanation as in SWB

    + SRE-hyper_data_1phn.mat > Same explanation as in SWB

- The enrollment data (corresponds to SRE10 C2-extended):

    + Model_data_male_ext.mat

    + Model_data_female_ext.mat

- The test data (corresponds to SRE10 C2-extended):

test_male_data_ext.mat
test_female_data_ext.mat

Email questions to:
Daniel Garcia-Romero
dgromero@jhu.edu
