# Northstar CPG: Marketing Measurement, Incrementality & Pricing Optimization

From explaining historical sales to understanding what actually drives them.

This repository shares a complete analytics project that uses synthetic Consumer Packaged Goods (CPG) data to explore Bayesian Marketing Mix Modeling (MMM), geo incrementality experiments, pricing elasticity, and profit optimization.

I first explored MMM in 2022, focusing on modeling methods and how different channels contribute. Since then, my work with pricing optimization and incrementality testing has changed how I approach marketing measurement.

Even if a model explains past sales well, how sure can we be that marketing actually caused those sales?

That question led to the starting point for this project.

## Project Overview

The analysis is based on a fictitious beverage brand called Northstar Hydration and includes synthetic weekly sales and commercial data from 20 different geographic markets over a period of 104 weeks.

The dataset features:

* Marketing investment: CTV, Paid Social, Retail Media, and Search
* Commercial drivers: Product pricing, promotions, retailer distribution, and competitor pricing
* Business outcomes: Unit sales, revenue, and profitability
* External factors: Seasonality and demand variation

With the help of the synthetic environment I am able to make realistic marketing decisions, carry out experiments, and finally compare the model estimates with the known underlying effects without employing those effects when estimating.

## Research Workflow

The project progresses from observational modelling to validation through experimental and business decision-making.

Column 1	Column 2	Column 3
Stage	Analysis	Notebook
01	Synthetic CPG Data Generation	Notebook 01
02	Exploratory Data Analysis	Notebook 02
03	Bayesian Marketing Mix Modeling	Notebook 03
04	Geo Incrementality Experiment	Notebook 04


The next steps will be to carry out an experimental calibration of the MMM, to estimate price elasticity, to carry out scenario analysis, and to optimise profits.

The notebooks are developed using Google Colab and are intended to contain the saved outputs, the visualizations, and explanations of the analytical decisions.

Initial Findings: MMM vs. Geo Incrementality

The first analysis looks at two estimates of incremental Paid Social sales:

1. A Bayesian MMM fitted on historical sales and marketing data.
2. A geo experiment was simulated for ten matched market pairs, involving an eight-week trial during which Paid Social investment in the treatment markets was increased by 40% at random.

## Results

Column 1	Column 2	Column 3
Method	Estimated Incremental Units	95% Interval
Baseline Bayesian MMM	6,195	[265, 27,121]
Geo Experiment	31,600	[-143,734, 207,554]

Despite estimating the impact of the same intervention, the approaches produced substantially different point estimates.

The comparison highlights two distinct measurement challenges:

Identification risk in MMM: Historical data may not clearly separate marketing’s effect from expected demand, promotions, distribution changes, or other related factors.

Precision risk in experiments: Randomization helps identify cause and effect, but small experiments can still lead to uncertain results.

Importantly, the uncertainty intervals overlap. The difference in point estimates alone does not establish that the two methods are statistically inconsistent.

The central learning is that MMM provides breadth, while experiments provide causal anchors. Combining observational and experimental evidence may create a more useful measurement framework than relying on either approach independently.

Articles & Research Notes

Alongside the notebooks, I’m documenting the analytical process in a series of technical articles.

Article 1: When MMM and Incrementality Disagree: What Is Each Actually Telling Us?

Exploring why strong model fit does not guarantee causal attribution, and what a geo experiment can reveal.

Medium publication link to be added.

Upcoming articles

* Article 2: Calibrating MMM With Incrementality Tests
* Article 3: Bringing Pricing Into the Measurement Framework
* Article 4: From Measurement to Decisioning: Optimizing Price, Promotion and Media for Profit

Markdown copies of the articles will be maintained in the articles/ directory.

Reproducing the Analysis

The notebooks are designed to be executed sequentially, beginning with synthetic data generation and continuing through the baseline MMM and geo experiment.

To explore the results without rerunning the analysis, open the notebooks directly on GitHub to view their saved outputs and visualizations.

Package dependencies and setup instructions will be finalized in requirements.txt.

Earlier Work

This project builds on my earlier exploration of Bayesian Marketing Mix Modeling with PyMC3 in 2022.

MMM-PyMC3-Marketing — Original GitHub Project

Notes

* All business and consumer data are synthetic.
* The true data-generating effects are excluded from baseline model fitting and experimental estimation.
* Results are intended to demonstrate measurement principles and analytical trade-offs, not to represent real commercial performance.
* The repository will be expanded as additional modeling and experimentation stages are completed.
