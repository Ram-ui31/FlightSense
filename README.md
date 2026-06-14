# FlightSense ✈️📱📊

**Transforming passenger-side smartphone sensor data into flight performance insights.**

FlightSense is an open-source project that explores what can be learned about commercial flights using only consumer-grade smartphone sensors and open aviation models.

Using data recorded from a passenger seat with the **phyphox** smartphone sensor app, FlightSense reconstructs flight phases, estimates fuel burn, analyzes turbulence patterns, and generates visual flight summaries.

The goal is simple:

> **Can we build meaningful aviation analytics using nothing more than a phone in economy class and open scientific tools?**

---

## Features

* 📍 GPS-based trajectory reconstruction
* ✈️ Automatic flight phase detection (climb, cruise, descent)
* ⛽ Dynamic fuel burn estimation using OpenAP
* 🌪️ Turbulence characterization using EDR proxies derived from accelerometer measurements
* 📉 Fuel consumption analysis under varying turbulence conditions
* 📊 Publication-ready visualizations and dashboards
* 📂 Support for multi-flight analysis and future dataset expansion

---

## Example Study

**Flight:** JetBlue Airbus A321

**Route:** JFK → MCO (New York → Orlando)

**Duration:** 128 minutes

**Sensor Platform:** Smartphone running phyphox

### Fuel Burn Estimation

| Metric                   | Value        |
| ------------------------ | ------------ |
| FlightSense estimate     | **4,700 kg** |
| Distance-based reference | **4,725 kg** |
| Difference               | **0.5%**     |

### Turbulence Analysis

* Approximately **81% of airborne time** was classified as light turbulence.
* A concentrated turbulence corridor was identified during cruise over the Carolinas.
* Moderate turbulence conditions were associated with increased modeled cruise fuel burn rates.

---

## Methodology

FlightSense combines smartphone measurements with open aviation models.

### Data Collection

Sensor data are collected using **phyphox**, including:

* GPS position
* Ground speed
* Accelerometer measurements
* Gyroscope measurements
* Device orientation

Sampling rates depend on device capabilities and recording settings.

---

### Flight Phase Detection

Flight phases are identified using **OpenAP's FlightPhase classifier**, enabling automatic segmentation of:

* Climb
* Cruise
* Descent

No manually defined altitude thresholds are required.

---

### Fuel Burn Modeling

Fuel consumption is estimated using **OpenAP**, an open-source aircraft performance framework developed by researchers at **TU Delft**.

The model incorporates:

* Aircraft performance characteristics
* Phase-dependent fuel flow estimates
* **Dynamic mass depletion**, allowing aircraft mass to decrease continuously as fuel is consumed

This approach captures how changing aircraft weight influences subsequent fuel requirements.

---

### Turbulence Analysis

Vertical acceleration measurements are processed to derive an **EDR-inspired turbulence proxy**.

The pipeline includes:

* Signal cleaning
* Outlier removal
* Takeoff and landing exclusion
* Turbulence categorization

The resulting metrics enable exploratory analysis of turbulence patterns experienced by passengers.

---

## Repository Structure

```text
FlightSense/
├── data/               # Raw and processed sensor recordings
├── notebooks/          # Exploratory analyses and case studies
├── src/                # Core analysis pipeline
├── figures/            # Generated plots and dashboards
├── outputs/            # Processed results
├── requirements.txt
└── README.md
```

---

## Technology Stack

* Python
* NumPy
* Pandas
* Matplotlib
* SciPy
* OpenAP
* phyphox

---

## Important Limitations

FlightSense is a **research and educational project**.

It does **not** use airline operational data, certified flight data recorder information, or manufacturer-provided performance records.

Fuel consumption estimates should therefore be interpreted as **model-derived approximations**, not operational measurements.

Similarly, turbulence estimates are based on passenger-side smartphone measurements and should not be interpreted as certified aviation turbulence observations.

---

## Roadmap

* [ ] Expand the dataset to additional routes and aircraft types
* [ ] Release a standardized FlightSense dataset format
* [ ] Package the analysis pipeline into an installable Python library
* [ ] Develop automated reporting tools
* [ ] Investigate machine learning approaches for turbulence characterization

---

## Acknowledgements

FlightSense would not have been possible without the open tools developed by the broader scientific community.

Special thanks to:

* **phyphox** for making smartphone-based physics experiments accessible.
* **OpenAP** and the researchers at **TU Delft** for providing open aircraft performance models.

---

## Citation

If you use FlightSense in your work, please cite this repository and the underlying tools that make it possible.

---

## License

MIT License

---

> *Most people on a flight watch Netflix.*
>
> *FlightSense asks what happens if you collect data instead.*
