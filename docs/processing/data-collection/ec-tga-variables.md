# EC & TGA Logger Variables

This page documents output tables and variable structure for the eddy-covariance tower loggers and the TGA/flux-gradient logger. See [Met & Soil Logger Variables](met-soil-variables.md) for the remaining loggers.

## EC Tower Loggers (`Plot1_irgason` and `Plot3_irgason`)

The two EC tower programs appear to use the **same overall variable and table structure**. The main difference visible in the logger code is the tower-specific configuration, such as `CSAT3_AZIMUTH`. The data structure of the two EC logger programs is otherwise the same.

### Core high-frequency variable array

Both EC tower programs define a 13-element `sonic_irga` array with the following aliases:

| Array element | Alias | Interpretation |
| --- | --- | --- |
| `sonic_irga(1)` | `Ux_ir` | X wind component |
| `sonic_irga(2)` | `Uy_ir` | Y wind component |
| `sonic_irga(3)` | `Uz_ir` | Z wind component |
| `sonic_irga(4)` | `Ts_ir` | Sonic temperature |
| `sonic_irga(5)` | `diag_sonic_ir` | Sonic diagnostic |
| `sonic_irga(6)` | `CO2_uncorr_ir` | Uncorrected CO₂ |
| `sonic_irga(7)` | `H2O_ir` | Water vapor |
| `sonic_irga(8)` | `diag_irga_ir` | IRGA diagnostic |
| `sonic_irga(9)` | `cell_tmpr_ir` | IRGA cell temperature |
| `sonic_irga(10)` | `cell_press_ir` | IRGA cell pressure |
| `sonic_irga(11)` | `CO2_sig_strgth_ir` | CO₂ signal strength |
| `sonic_irga(12)` | `H2O_sig_strgth_ir` | H₂O signal strength |
| `sonic_irga(13)` | `CO2_ir` | Corrected / main CO₂ channel |

### Supporting meteorological variables

Both EC programs also define supporting variables/groups such as:

| Variable/group | Interpretation |
| --- | --- |
| `batt_volt`, `panel_temp` | Logger health / system status |
| `AirTC_H`, `RH_H` | Air temperature and relative humidity from HMP50-style input |
| `CNR1(1..7)` | Net radiometer-related channels (`CM3Up`, `CM3Dn`, `CG3Up`, `CG3Dn`, `CNR1TC`, `CG3UpCo`, `CG3DnCo`) |
| `Albedo` | Derived albedo term |
| `Hs`, `Fc_irga`, `LE_irga`, `tau`, `u_star` | Derived online flux / turbulence terms |

### Online covariance output array

Both programs define a 17-element `cov_out` array:

| Array element | Alias | Interpretation |
| --- | --- | --- |
| `cov_out(1)` | `cov_Uz_Uz` | Vertical wind variance |
| `cov_out(2)` | `cov_Ux_Uz` | Covariance of Ux and Uz |
| `cov_out(3)` | `cov_Uy_Uz` | Covariance of Uy and Uz |
| `cov_out(4)` | `cov_Ts_Uz` | Covariance of Ts and Uz |
| `cov_out(5)` | `cov_co2_co2` | CO₂ variance |
| `cov_out(6)` | `cov_co2_Uz` | CO₂–Uz covariance |
| `cov_out(7)` | `cov_h2o_h2o` | H₂O variance |
| `cov_out(8)` | `cov_h2o_Uz` | H₂O–Uz covariance |
| `cov_out(9)` | `Ts_mean` | Mean sonic temperature |
| `cov_out(10)` | `H2O_mean` | Mean H₂O concentration |
| `cov_out(11)` | `co2_mean` | Mean CO₂ concentration |
| `cov_out(12)` | `press_mean` | Mean pressure |
| `cov_out(13)` | `wnd_spd_compass` | Wind speed in compass coordinates |
| `cov_out(14)` | `wnd_dir_compass` | Wind direction in compass coordinates |
| `cov_out(15)` | `wnd_spd` | Wind speed |
| `cov_out(16)` | `wnd_dir_csat3` | CSAT3-relative wind direction |
| `cov_out(17)` | `std_wnd_dir` | Standard deviation of wind direction |

### EC output tables

| Table | Interval | Contents |
| --- | --- | --- |
| `RawData` | 100 msec | 13 high-frequency `sonic_irga` channels |
| `ProcssData` | 30 min | Means, standard deviations, diagnostics, covariance samples, wind metrics, derived flux/turbulence terms, logger status, CNR1 averages, HMP variables |
| `comp_cov` | 30 min | Working covariance calculations, mean scalar values, wind vector terms |

## TGA / FG Logger (`TGAsampling`)

The TGA CR3000 program is more complex than the other loggers because it controls the analyzer and valve sequencing in addition to data storage. For that reason, it is more useful to organize the variable description by **functional group** rather than listing every field in a single long table.

### Functional role

This logger manages:

- TGA communication
- pressure control
- valve sequencing
- sample / bypass flow monitoring
- system-status messaging
- high-frequency and averaged storage tables

### Main variable groups

| Variable group | Examples | Interpretation |
| --- | --- | --- |
| Sequence control | `ValveSequence`, `OnTime`, `OmitTime`, `omit_cnts`, `seq_ACTIVE` | Defines and manages valve switching logic |
| Status / messaging | `latest_note`, `mode_status`, `system_status`, `TGA_status`, `diag_system` | Operational state and troubleshooting messages |
| Flow and pressure | `SampleFlow`, `ExcessFlow`, `SamplePress`, `BypassPress`, `SampleP_control`, `BypassP_control`, `TGAPress_control` | Core pneumatic / control variables |
| TGA analyzer array | `TGAData(...)` | Main analyzer outputs, depends on gas configuration |
| Power / logger health | `panel_tmpr`, `batt_volt`, `buff_depth` | Logger/system state |
| Optional interfaces | `Li64...`, `CO2mixerData` | Optional external interfaces if enabled |

### `TGAData` analyzer variables for the current gas setting

The program is configured with:

- `GAS_TYPE = GAS_N2OnCO2`
- `SEQ_TYPE = SEQ_GRADIENT_Seq`

For this gas type, the visible `TGAData` aliases include:

| Alias | Interpretation |
| --- | --- |
| `Conc12C`, `Conc13C`, `Conc18O` | Concentration-style analyzer outputs `[VERIFY!]` |
| `TGAStatus` | Analyzer status code |
| `TGAPressure` | Internal TGA pressure |
| `LaserTemp` | Laser temperature |
| `DCCurrentA`, `DCCurrentB`, `DCCurrentC` | DC currents for scan ramps |
| `TGAAnalog1` | General analog input / monitor |
| `TGATemp1`, `TGATemp2` | Internal temperatures |
| `LaserCooler` | Laser cooling control / state |
| `RefDetSigA/B/C`, `RefDetTransA/B/C`, `RefDetTemp`, `RefDetCooler`, `RefDetGainOffset` | Reference detector diagnostics |
| `SmpDetSigA/B/C`, `SmpDetTransA/B/C`, `SmpDetTemp`, `SmpDetCooler`, `SmpDetGainOffset` | Sample detector diagnostics |
| `TGATemp1DutyCycle`, `TGATemp2DutyCycle` | Temperature-control duty-cycle terms |

### TGA output tables

| Table | Trigger / interval | Contents |
| --- | --- | --- |
| `RawData` | 10 Hz | High-frequency raw analyzer / control data |
| `OneSec` | 1 sec | One-second averaged diagnostic / analyzer table |
| `SiteAvg` | One record per completed site / valve step | Primary site-average output table; includes valve number, number of samples, averaged TGA data, flows, pressures, controls, battery/panel state, standard deviations |
| `TimeInfo` | Small configuration table | Sequence length, sequence time, sync interval, valve sequence, on-times, omit-times |
| `message_log` | Logged status messages | Troubleshooting / system messages |
| `CO2mixerOneSec` | Optional | Only used if CO₂ mixer interface is enabled |