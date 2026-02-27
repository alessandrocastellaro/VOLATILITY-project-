
import numpy as np
import pandas as pd


#%%

#We import the time series for the 600 stocks

tik = pd.read_excel(r"C:\Users\aless\OneDrive - King's College London\Documents\Investment Fund\Export_SPXX600_Last_Prices.xlsx",
                   index_col = 0)

tik.index = tik.to_datetime(df.index, unit = 'D', origin = '1899-12-30')
print(df.head())



#%%

#We import the market data

mkt = pd.read_excel(r"C:\Users\aless\OneDrive - King's College London\Documents\Investment Fund\Market_export.xlsx",
                   index_col = 0)

mkt.index = pd.to_datetime(mkt.index, unit = 'D', origin = '1899-12-30')
print(mkt.head())

#%%

def rolling_idio_vol(asset_ret, market_ret, window = 549):
    
    data = [pd.concat([asset_ret, mkt_ret], axis =1).dropna()]
    data.columns = ["r","m"]
    
    ivol = pd.Series(index=data.index, dtype = float)
#%%
import pandas as pd
import numpy as np

tik = pd.read_excel(
    r"C:\Users\aless\OneDrive - King's College London\Documents\Investment Fund\Export_SPXX600_Last_Prices.xlsx",
    index_col=0
)

mkt = pd.read_excel(
    r"C:\Users\aless\OneDrive - King's College London\Documents\Investment Fund\Market_export.xlsx",
    index_col=0
)

tik.index = pd.to_datetime(tik.index, unit="D", origin="1899-12-30")
mkt.index = pd.to_datetime(mkt.index, unit="D", origin="1899-12-30")

for c in r.columns:
    d = pd.concat([r[c], rm], axis=1).dropna()
    if len(d) >= w:
        y = d.iloc[-w:,0].values
        x = np.c_[np.ones(w), d.iloc[-w:,1].values]
        b = np.linalg.lstsq(x, y, rcond=None)[0]
        resid = y - x @ b
        last_iv[c]
        
r  = np.log(tik/tik.shift(1))
rm = np.log(mkt/mkt.shift(1)).iloc[:,0].reindex(r.index)

w = 252
last_iv = {}
 = np.std(resid, ddof=1) * np.sqrt(252)

last_iv = pd.Series(last_iv)

z_score_ivol = (last_iv - last_iv.mean()) / last_iv.std()

print(z_score_ivol.sort_values())
