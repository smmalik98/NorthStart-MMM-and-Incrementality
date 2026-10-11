# Northstar CPG: Marketing Measurement, Incrementality & Pricing Optimization

### From explaining historical sales to understanding what actually drives them.

This repository documents an ongoing analytics project exploring **Bayesian Marketing Mix Modeling (MMM), geo incrementality experiments, pricing elasticity, and profit optimization** using synthetic Consumer Packaged Goods (CPG) data.

I first explored MMM in 2022, focusing on the modeling methods and how different marketing channels contribute to sales. Since then, working more closely with pricing optimization and incrementality testing has changed how I approach marketing measurement.

Even if a model explains historical sales well, how confident can we be that marketing actually *caused* the sales attributed to it?

That question became the starting point for this project.

## Project Overview

The analysis uses a fictional beverage brand, **Northstar Hydration**, with synthetic weekly sales and commercial data from **20 geographic markets over 104 weeks**.

The dataset includes:

- **Marketing investment:** CTV, Paid Social, Retail Media, and Search
- **Commercial drivers:** Product pricing, promotions, retailer distribution, and competitor pricing
- **Business outcomes:** Unit sales, revenue, and profitability
- **External factors:** Seasonality and demand variation

The synthetic environment makes it possible to simulate marketing decisions, run experiments, and ultimately compare estimates with the known underlying causal effects—without using those effects during estimation.

## Research Workflow

The project moves from observational modeling to experimental evidence and, eventually, business decision-making.

| Stage | Analysis | Notebook |
|:---:|---|---|
| 01 | Synthetic CPG Data Generation | [Notebook 01](notebooks/01-data-generation.ipynb) |
| 02 | Exploratory Data Analysis | [Notebook 02](notebooks/02-exploration.ipynb) |
| 03 | Bayesian Marketing Mix Modeling | [Notebook 03](notebooks/03-bayesian-mmm.ipynb) |
| 04 | Geo Incrementality Experiment | [Notebook 04](notebooks/04-geo-incrementality.ipynb) |

**Planned next steps:** Calibrate the MMM using experimental evidence, estimate price elasticity, analyze pricing and media scenarios, and optimize for profit.

The notebooks are developed in Google Colab and are intended to include saved outputs, visualizations, and explanations of key analytical decisions.

## Initial Findings: MMM vs. Geo Incrementality

The first analysis compares two estimates of incremental units from additional Paid Social investment:

1. A **Bayesian MMM** fitted on historical sales and marketing data.
2. A **simulated geo experiment** with ten matched market pairs, an eight-week test, and a randomized **40% increase in Paid Social spend** in treatment markets.

### Results

| Method | Estimated Incremental Units | 95% Interval |
|---|---:|---:|
| Baseline Bayesian MMM | 6,195 | [265, 27,121] (posterior interval) |
| Geo Experiment | 31,600 | [-143,734, 207,554] (bootstrap confidence interval) |

Although both approaches estimate the impact of the same intervention, their point estimates differ substantially.

The comparison highlights two distinct measurement challenges:

- **Identification risk in MMM:** Historical data may not fully separate marketing's causal effect from expected demand, promotions, distribution changes, and other correlated factors.
- **Precision risk in experiments:** Randomization strengthens causal identification, but a small experiment can still produce a highly uncertain estimate.

Importantly, the uncertainty intervals overlap. The difference between the point estimates alone does not establish that the methods are statistically inconsistent.

The central lesson is that **MMM provides breadth, while experiments provide causal anchors**. Combining observational and experimental evidence may create a more decision-useful measurement framework than relying on either method independently.

## Articles & Research Notes

Alongside the notebooks, I'm documenting the analytical process in a series of technical articles.

**Article 1: When MMM and Incrementality Disagree: What Is Each Actually Telling Us?**

Why good model fit doesn't guarantee causal attribution, and what a geo experiment can reveal.

*[Medium article link coming soon.](https://medium.com/@smitmalik/when-mmm-and-incrementality-disagree-what-is-each-actually-telling-us-edff2d0a7499)*

**Upcoming articles:**

- **Article 2:** Calibrating MMM With Incrementality Tests
- **Article 3:** Bringing Pricing Into the Measurement Framework
- **Article 4:** From Measurement to Decisioning: Optimizing Price, Promotion and Media for Profit

Markdown copies of the articles will be maintained in the [`articles/`](articles/) directory.

## Reproducing the Analysis

The notebooks are designed to be run in order, starting with synthetic data generation and progressing through exploratory analysis, the baseline MMM, and the geo experiment.

You can also **view the notebooks directly on GitHub** to inspect saved outputs and visualizations without rerunning the analysis.

Package dependencies and detailed setup instructions will be added to `requirements.txt` and this README as the project develops.

## Earlier Work

This project builds on my 2022 exploration of Bayesian Marketing Mix Modeling using PyMC3:

[MMM-PyMC3-Marketing — Original GitHub Project](https://github.com/smmalik98/MMM-PyMC3-Marketing)

## Notes

- All business and consumer data are **synthetic**.
- The hidden data-generating effects were excluded from baseline model fitting and experimental estimation.
- Results illustrate measurement principles and analytical trade-offs; they do not represent real commercial performance.
- The repository will expand as further modeling and experimentation stages are completed.
