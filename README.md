# app-temporal-filtering

Repository of a Brainlife App that filters raw or epoched MEG signals using the MNE function: 
[`mne.io.Raw.filter`](https://mne.tools/stable/generated/mne.io.Raw.html#mne.io.Raw.filter) or [`mne.Epochs.filter`](https://mne.tools/stable/generated/mne.Epochs.html?highlight=mne%20epochs#mne.Epochs.filter).

# app-temporal-filtering documentation

1) Filter MEG signals
2) Apply a bandpass, highpass, or lowpass filter
3) Input file is:
    * a MEG file in `.fif` format,
    * an optional fine calibration file in `.dat`,
    * an optional crosstalk compensation file in `.fif`,
    * an optional head position file in `.pos`,
    * an optional destination file in `.fif`,
    * an optional event file in `.tsv`.
4) Input parameters are:
    * epoched_data: `bool`, if True, the data to be filtered is epoched, else it is continuous. Default is False.
    * l_freq: `float`, optional, for FIR filters, the lower pass-band edge; for IIR filters, the lower cutoff frequency. If `None` the data are only low-passed.  
    * param_h_freq: `float`, optional, for FIR filters, the upper pass-band edge; for IIR filters, the upper cutoff frequency. If `None` the data are only high-passed.
    * param_picks: `str`or `list`, optional, channels to include. Default is `None`.
    * param_length: `str`, length of the FIR filter to use in human-readable time units. Default is `auto`. 
    * param_l_trans_bandwidth: `float` or `str`, width of the transition band at the low cut-off frequency in Hz. Default is `auto`.
    * param_h_trans_bandwidth: `float` or `str`, width of the transition band at the high cut-off frequency in Hz. Default is `auto`.
    * param_n_jobs: `int`, number of jobs to run in parallel. Default is 1. 
    * param_method: `str`, 'fir' will use overlap-add FIR filtering, 'iir' will use IIR forward-backward filtering. Default is 'fir'.
    * param_iir_params: `dict`, optional, dictionary of parameters to use for IIR filtering. To know how to define the dictionary go 
        [there](https://mne.tools/stable/generated/mne.filter.construct_iir_filter.html#mne.filter.construct_iir_filter). Default is `None`.
    * param_phase: `str`, phase of the filter. Default is 'zero'.
    * param_fir_window: `str`, the window to use in FIR design. Default is 'hamming'.
    * param_fir_design: `str`. Default is `firwin`.
    * param_skip_by_annotation: `str` or `list of str`, if a string (or list of str), any annotation segment that begins with the given string will not be included in
        filtering, and segments on either side of the given excluded annotated segment will be filtered separately. Default is `["edge", bad_acq_skip"]`.
    * param_pad: `str`, the type of padding to use for raw data. Default is 'reflect_limited' for raw data and 'edge' for epoch data. 
 
This list along with the parameters' default values correspond to the 0.22.0 version of MNE Python.  

5) Ouput files are:
    * a `.fif` MEG file after filtering,
    * an `.html` report containing figures.

### Authors
- [Aurore Bussalb](aurore.bussalb@icm-institute.org)

### Contributors
- [Aurore Bussalb](aurore.bussalb@icm-institute.org)
- [Maximilien Chaumon](maximilien.chaumon@icm-institute.org)

### Funding Acknowledgement
brainlife.io is publicly funded and for the sustainability of the project it is helpful to Acknowledge the use of the platform. We kindly ask that you acknowledge the funding below in your code and publications. Copy and past the following lines into your repository when using this code.

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)

### Citations
1. Avesani, P., McPherson, B., Hayashi, S. et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. Sci Data 6, 69 (2019). [https://doi.org/10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Running the App 

### On Brainlife.io

This App has not yet been registered in Brainlife.io.

### Running Locally (on your machine)

1. git clone this repo
2. Inside the cloned directory, create `config.json` with the same keys as in `config.json.example` but with paths to your input 
   files and values of the input parameters. For instance:

```json
{
  "fif": "rest1-raw.fif"
}
```

3. Launch the App by executing `main`

```bash
./main
```

## Output

The output files are a MEG file in `.fif` format and an `.html` report.
