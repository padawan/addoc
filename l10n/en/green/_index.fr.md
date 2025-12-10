+++
url = "/green-hosting/"
title = "Environmental Responsibility"
pre = "<i class='fas fa-fw fa-leaf'></i> "
weight = 55
tags = [ "green" ]
+++

## Organization

It is our responsibility to all of us to make every effort in the course of our mission to limit the impact of our activities on the negative broadcasts for our planet.

Thus, our company has incorporated the following elements into its daily operation:

- **Work at 100%**: our team has been working for several years thus limiting all emissions connected to transport (except datacenters);
- **Minimum stock management**: adding servers in large quantities just to make more numbers do not integrate us, we anticipate a reasonable stock, depending on the rate of orders made in the last months;
- **Appropriate advice**: we attach importance to bringing personalized advice to our users so that they focus on the most suitable offer for their real need and thus on a meager consumption.

## Compensation

_Last Updated: January 28, 2025_

Each year, we want to **compensate 200%** for our GHG emissions (greenhouse gases). Although our impact is extremely complicated to determine accurately, we want to transparently delineate our calculation method to determine the budget allocated to this compensation.

### Donated and hypothetical

In order to simplify the method, but also to compensate in the right direction, some data are marginalized. We specify this in the following table.

| Donated                                 | Details                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                      Value 2024 |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------: |
| Number of servers                       | All consumer devices (servers, routers, hypervisors, etc. ) purchased and integrated into our infrastructure during the year.                                                                                                                                                                                                                                                                                           |                              39 |
| Apparent Power (kVA) | Acquisition of data centers across our entire infrastructure. Margin: Calculation therefore uses the subscribed maximum power rather than the actual consumption.                                                                                                                                                                                                                                                          |                          31 kVA |
| Power factor (cos φ) | In general it takes 0.8 as an average value for standard installations. Margin: Even if most modern servers have a higher factor than 0. (actually approaching the Power Factor [displayed by our food](https://store.supermicro.com/us_en/pub/media/wysiwyg/productspecs/PWS-606P-1R/PWS-606P-1R_quick_spec.pdf)), we choose to remain on this more pessimistic value. |             0.8 |
| Annual hard to use                      | Total server consumption time. Margin : the most energy hypotheis, therefore 100% of the time.                                                                                                                                                                                                                                                                                                                             |                      8760 hours |
| PUE                                     | Average power efficiency of [our partner datacenters](https://sustainability.equinix.com/environment/operational-sustainability/).                                                                                                                                                                                                                                                                                                                         |            1.42 |
| Issue factor                            | Consider the average in France. Last value 2024: source [RTE-france.com](https://www.rte-france.com/actualites/production-electricite-francaise-atteint-plus-haut-niveau-depuis-5-ans).                                                                                                                                                                                                                    | 21.3 gCO2eq/kWh |
| Server production consumption           | Estimated consumption generated when producing a server: see [Boavizta](https://boavizta.org/blog/empreinte-de-la-fabrication-d-un-serveur). Margin: Complex information to find, which depends on many factors. The values are always under the integer. Rounding to the top integer.                                                                                     |                        1 tCO2eq |

### Calculation

```python
# Données pour le calcul
serveurs = 39           # Serveurs arrivés en 2024
kVA = 31                # Consommation en kVA
cos_phi = 0.8           # Facteur de puissance moyen
heures_par_an = 8760    # Nombre d'heures dans une année
pue = 1.42              # Efficacité énergétique du DC
facteur_emission = 21.3 # Facteur d'émission en gCO₂eq/kWh
emission_production = 1 # Émission de la production d'un serveur en tCO₂eq

# Conversion de kVA en kW
kW = kVA * cos_phi

# Calcul de la consommation annuelle en kWh
kWh_annuels = kW * heures_par_an

# Calcul des émissions de consommation totale en tCO₂eq
emissions_consommation = (kWh_annuels * facteur_emission * pue) / 1000 / 1000  # Conversion de g à tonnes

# Calcul des émissions liées à la production des serveurs entrant en 2024
emissions_production = emission_production * serveurs

# Calcul des émissions totales (consommation et production)
emissions = emissions_consommation + emissions_production
```

The result:

- Electric consumption for the year 2024: **217 248 kWh**;
- Electrical consumption: **6.57 tCO2eq**;
- Linked broadcasts to server production: **39 tCO2eq**;
- Total emissions: **45.57 tCO2eq**;
- Compensation Required (200%) : **92 tons of CO2**.

We chose [Gold Standard](https://www.goldstandard.org/) to record our compensation.
See our [certificat](https://files.alwaysdata.com/certifications/2025_GOLDSTANDARD_CERTIFICATE.zip).

