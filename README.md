# humidwise-data

Open data behind [Humidwise](https://humidwise.com/), an independent U.S. dehumidifier comparison built on public data. Updated 2026-10-07.

| File | What it holds | Rows |
| --- | --- | --- |
| [dehumidifiers.csv](dehumidifiers.csv) | Every ENERGY STAR® certified dehumidifier on the EPA list that is sold in the United States, one row per model, grouped the way Humidwise groups them. `also_sold_as` lists the same model’s other listings and brand names | 476 |
| [state-study.csv](state-study.csv) | Humid months a year and the yearly cost to run a dehumidifier, for the 50 states and DC | 51 |
| [noaa-stations.csv](noaa-stations.csv) | Normal dew point for each month and humid months a year, for each NOAA station used | 445 |

## Sources

- **EPA**: ENERGY STAR Certified Dehumidifiers, [data.energystar.gov](https://data.energystar.gov/d/mgiu-hu4z). List updated 2026-10-04, read 2026-10-05. Pints a day come from the DOE 2019 test (10 CFR 430, Appendix X1). Yearly energy use is left blank for whole-house units: their EPA yearly figures don’t follow one method that we can cite.
- **NOAA**: Palecki, M.; Durre, I.; Applequist, S.; Arguez, A.; Lawrimore, J. (2021). U.S. Climate Normals 2020: U.S. Hourly Climate Normals (1991-2020). NOAA National Centers for Environmental Information. https://doi.org/10.25921/e3zh-ag77 (accessed 2026-10-05).
- **EIA**: Electric Power Monthly, Table 5.6.A, average residential price by state, 2026-07.

## How the columns are computed

- `humid_months`: months whose normal dew point gives more than 60% relative humidity once the outdoor air is brought to 65°F, as in a cool basement. In `state-study.csv`, the middle value across the state’s stations, so 6.5 or 3.5 means an even count of them. The District of Columbia has no NOAA station in these normals, so its `humid_months` and `summer_dew_point_f` are blank.
- `summer_dew_point_f`: the June–August average of the normal dew point, middle value across the state’s stations.
- `yearly_cost_usd`: 520 kWh a year (the median certified 45–50 pint portable on the EPA list) times the state’s residential price. The EPA’s yearly figure is the same in every state. In a humid state, a unit runs longer, so the real bill is likely higher.
- `epa_figures_agree`: “no” for the 9 portables whose pints, kWh, and IEF on the EPA list don’t agree with each other. Humidwise shows them as listed and leaves them out of its rankings and medians.
- `wifi`: the EPA’s “connected” field. A blank `refrigerant` means the EPA list doesn’t give one.
- `humidwise_page`: the model’s page on Humidwise.

The state study method, and its limits, are on the [state study page](https://humidwise.com/dehumidifier-humidity-and-cost-by-state/). How Humidwise compares models is at [How we compare](https://humidwise.com/how-we-compare/).

## License and credit

To the extent Julien Fourel holds rights in the compilation and the computed columns, they are licensed under [CC BY 4.0](LICENSE): free to quote, chart, and republish, including commercially. Please credit “Humidwise” with a link to https://humidwise.com/, and cite the EPA, NOAA, and the EIA. Data from U.S. federal sources is generally in the public domain; we claim no rights in it. Brand and model names belong to their owners. ENERGY STAR and the ENERGY STAR mark are registered trademarks owned by the U.S. EPA. Humidwise is independent and is not affiliated with or endorsed by the EPA or the ENERGY STAR program.

Corrections: https://humidwise.com/report-an-error/
