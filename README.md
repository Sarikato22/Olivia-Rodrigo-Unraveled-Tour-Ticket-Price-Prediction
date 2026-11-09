# Olivia Rodrigo Tour Ticket Price Prediction

## Overview

This project explores the use of machine learning to predict ticket prices for Olivia Rodrigo's **Unraveled Tour** using historical ticket market data.

The data collection covers both the *GUTS World Tour* and the *Unraveled Tour*, with data collected through October 30, 2026, using the SeatData API (pay-per-request).

Because the Unraveled Tour was still ongoing, its available historical data alone was not sufficient to build a reliable predictive model. To address this limitation, I incorporated data from the GUTS World Tour as an additional source of historical pricing information.

However, after extensive experimentation, I discovered an important challenge: ticket price patterns were not directly comparable between the two tours. Not only did pricing trends differ, but the overall price levels were significantly higher during the Unraveled Tour, reflecting the substantial growth in Olivia Rodrigo's popularity.

Rather than combining the datasets directly, I developed an approach to account for these differences.

## The Approach

The final project consists of a machine learning model and a small interactive interface.

The model:

1. **Adjusts historical prices:** Scales GUTS World Tour ticket prices to better align with the higher price levels observed during the Unraveled Tour.
2. **Establishes a benchmark:** Calculates a median ticket price to establish a reference point for typical ticket value.
3. **Classifies ticket prices:** Categorizes prices into three groups:
   - **Below Typical:** Prices below the expected market benchmark.
   - **Typical:** Prices within the expected range.
   - **Above Typical:** Prices above the expected market benchmark.

The interactive interface allows users to select a future tour date they are interested in attending. Using the latest available information, the model estimates ticket prices over the following seven days and classifies their expected value.

## Model Performance

The model was evaluated against historical observations, including data beyond July 2026 and a completely unseen set of dates in November 2026.

The classification results were:

| Predicted Category | Observations | Accuracy |
|:-------------------|-------------:|---------:|
| Below Typical      | 2,493        | 84%      |
| Typical            | 7,914        | 86%      |
| Above Typical      | 4,163        | 83%      |

These results represent the accuracy within each predicted category. Across all 14,570 observations, the approximate weighted accuracy was **84.8%**.

In addition to evaluating the model against the downloaded historical data, I independently cross-checked its predictions using SeatData's reporting tools, which provide the lowest observed ticket price for each tour date on a given day.

This provided an additional reference for assessing whether the model's predictions were consistent with observed market prices.

## Data Availability

The underlying ticket market data was obtained through the paid SeatData API.

The raw datasets are not included in this repository because they are subject to SeatData's data licensing and redistribution restrictions. I do not have permission to redistribute the original data.

The repository is intended to showcase the data collection methodology, experimentation, modeling approach, and predictive interface without making proprietary source data publicly available.

## Limitations

- Ticket prices are influenced by changing market conditions and are not guaranteed to follow historical patterns.
- Predictions are based on the information available at the time of each run.
- The model estimates market prices and classifications; it cannot guarantee that a ticket will be available at a predicted price.

## Acknowledgments

Ticket market data provided by **SeatData.io** through its API.

This project is an independent analytical project and is not affiliated with, endorsed by, or associated with Olivia Rodrigo or her tour organizers.
