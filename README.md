# Quantitative Risk Calculator

A lightweight, browser-based quantitative risk calculator. Enter an asset value, an exposure factor and an annual rate of occurrence to get **SLE**, **ALE** and, optionally, the **ROSI** of a security control.

A single static HTML file. No build step, no dependencies, no server, no tracking.

> The user interface is currently in Bulgarian.

## Formulas

| Term | Meaning | Formula |
|---|---|---|
| **AV** | Asset Value | input |
| **EF** | Exposure Factor: share of the asset lost in one incident (0–100%) | input |
| **SLE** | Single Loss Expectancy: loss from one incident | `AV × EF` |
| **ARO** | Annualized Rate of Occurrence: incidents per year | input |
| **ALE** | Annualized Loss Expectancy: expected loss per year | `SLE × ARO` |
| **ROSI** | Return on Security Investment | `(ALE before − ALE after − annual control cost) / annual control cost` |

### Example

An online shop worth 80,000 €, hit by a DDoS attack that causes about 15% loss, twice a year:

- SLE = 80,000 × 0.15 = **12,000 €**
- ALE = 12,000 × 2 = **24,000 €** per year

With a 5,000 €/year DDoS protection service that lowers EF to 5% and ARO to 1:

- ALE after = 80,000 × 0.05 × 1 = **4,000 €**
- Annual benefit = 24,000 − 4,000 = **20,000 €**
- ROSI = (20,000 − 5,000) / 5,000 = **300%**

A positive ROSI means the control saves more than it costs.

## Features

- Live calculation with input validation
- Before and after comparison for a security control (new EF, new ARO, annual cost)
- Risk register with a total ALE
- CSV export, with protection against CSV formula injection
- Built-in glossary explaining every indicator and how to determine it
- Data stays in your browser (`localStorage`); nothing is sent anywhere
- Light and dark theme following the system setting, mobile-friendly layout

### Tips

- Calculate **one asset and one threat per entry**. The same asset can have several entries (for example DDoS, data breach, hosting outage), each with its own EF and ARO.
- The register total is a rough guide only. An asset cannot be lost more than once, so summing many threats for one asset can overstate the real loss.
- Mixed currencies in the register are not converted; the total is shown as "mixed currencies".

## Limitations

Quantitative risk assessment is only as good as its inputs. EF and ARO are usually expert estimates, so the results are suited to comparing and prioritising risks, not to precise forecasting. Record where each value came from so it can be reviewed later.

## Contributing

Issues and pull requests are welcome. The whole application lives in `index.html`, so changes are easy to review.

## License

Released under the [MIT License](LICENSE).
