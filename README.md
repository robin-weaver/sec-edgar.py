# sec-edgar.py
A basic (unofficial) Python API wrapper for the SEC's EDGAR system

## Documentation

The aim of this project is to make the SEC's EDGAR system more accessible to python programmers, performing all of the "messy" work so the user can make simple requests and receive clean results.
Still very much a WIP.

### Current Features

Start off by importing the base class from the main file and instantiating it.
```py
from sec-edgar-py import EdgarWrapper
client = EdgarWrapper()
```
Now you can call all of the methods from `client`.

```client.get_company_filings(ticker_or_cik, form_types=None, amount=0)```
Where:
  * `ticker_or_cik` can be either the company ticker, or the CIK.
  * `form_types` if specified, must be a list of the types of filings you wish to retrieve.
  * `amount` is the amount of filings you wish to retrieve. If unspecified or 0, all available filings will be retrieved.

This method returns a list of dictionaries of the filings, with the most recent filings first.
 
So:
`client.get_company_filings('abbv', form_types=['10-K', '10-Q'], amount=5)`
will return:
```py
[{'form': '10-Q',
  'filingDate': '2022-05-06',
  'URL': 'https://www.sec.gov/Archives/edgar/data/1551152/000155115222000017/abbv-20220331.htm'},
 {'form': '10-K',
  'filingDate': '2022-02-18',
  'URL': 'https://www.sec.gov/Archives/edgar/data/1551152/000155115222000007/abbv-20211231.htm'},
 {'form': '10-Q',
  'filingDate': '2021-11-02',
  'URL': 'https://www.sec.gov/Archives/edgar/data/1551152/000155115221000031/abbv-20210930.htm'},
 {'form': '10-Q',
  'filingDate': '2021-08-02',
  'URL': 'https://www.sec.gov/Archives/edgar/data/1551152/000155115221000025/abbv-20210630.htm'},
 {'form': '10-Q',
  'filingDate': '2021-05-07',
  'URL': 'https://www.sec.gov/Archives/edgar/data/1551152/000155115221000016/abbv-20210331.htm'}]
  ```
  
