# Molecular Classification
Model for identification and quantification of molecules from different lab tests:
- **Mass Spectrometry Classification**
  
PSEUDO CODE:

*Function*: detect_molecule(reference_sheet, mz_data, intensity_data, intensity_threshold=1, distance_threshold=10, mz_threshold=0.1, num_peak_threshold=5)
<br>function that identifies the molecules present in an MS spectrum and their quantities
<br>
<br>detect all peaks in the spectrum with intensity above intensity_threshold=1% and with at least a distance of <br>distance_threshold=10 m/z between each other (to represent the fragmentation pattern)
<br>for all molecules in reference sheet:
<br> &nbsp; &nbsp; &nbsp; &nbsp; check if there is a peak at the molecular weight +- 1 +- mz_threshold=0.1
<br> &nbsp; &nbsp; &nbsp; &nbsp; (e.g. for molecular weight of 286.4, need a peak between m/z of 285.3 and 285.5 or 286.3 and 286.5 or 287.3 and 287.5)
<br> &nbsp; &nbsp; &nbsp; &nbsp; if no peak at molecular weight:
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; molecule is not present in spectrum
<br> &nbsp; &nbsp; &nbsp; &nbsp; if there is peak:
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pull all the molecule’s standard m/z’s from reference sheet
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; check if there are peaks at those m/z’s +- 1 +- mz_threshold=0.1 
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if there are greater than or equal to num_peak_threshold=5 of those peaks in spectrum:
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if 2 of the 3 highest peaks are the mol ion peak and the base ion peak
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; molecule is present in spectrum
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; output top 3 peaks' m/z and intensity values
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; otherwise:
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; molecule is not present in spectrum
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; otherwise:
<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; molecule is not present in spectrum

- **Chromatography Classification**
