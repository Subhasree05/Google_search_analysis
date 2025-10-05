# Google Trends Analysis

This project uses the pytrends library to analyze Google Trends data.  
The example shown here is for the keyword "Cloud Computing".

## Features
- Interest over time for the keyword
- Top 10 peak dates of search interest
- Regional interest by country
- Bar chart visualization
- Related queries and keyword suggestions

## Installation
Install the required libraries:

```bash
pip install pytrends pandas matplotlib lxml
```

## Usage
```python
from pytrends.request import TrendReq
import pandas as pd
import matplotlib.pyplot as plt

pytrends = TrendReq(hl='en-US', tz=360)
kw_list = ["Cloud Computing"]

# Build payload
pytrends.build_payload(kw_list, timeframe='today 12-m')

# Interest over time
data = pytrends.interest_over_time()
print(data.head())

# Regional interest
region_data = pytrends.interest_by_region()
print(region_data.head())

# Plot
region_data.reset_index().plot(x='geoName', y='Cloud Computing', kind='bar', figsize=(10,5))
plt.show()
```

## Notes
- Google Trends may limit frequent requests, so short delays might be needed.
- Related queries are not always available.
