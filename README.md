# Google Patents PDF Downloader

Download patents as PDF documents from [Google Patents](https://patents.google.com)


## Installation

You can install the development version from [GitHub](https://github.com/) with:

``` python
pip install git+https://github.com/lorenzbr/GooglePatentsPdfDownloader.git
```

Please make sure you have [Google Chrome](https://www.google.com/chrome/) and the corresponding chromedriver.exe (see [here](https://chromedriver.chromium.org/downloads)) installed to access the website using Selenium.


## Function arguments

* `patents`: A list of strings containing patent numbers
* `file`: A path to a txt file which contains a table with patent numbers and column name `patent_number`
* `output_path`: The folder where the PDFs are saved (default is the current working directory)
* `driver_file`: The path of the Chrome driver
* `remove_kind_codes`: A list of strings specifying patent kind codes which will be removed from all patent numbers in the input. This option is included as Google Patents sometimes does not find the correct patent if kind codes are included (default is `None`)

Specify either `patents` or `file` in the function `get_pdfs` to download the PDFs of the corresponding patents.


## Examples

```python
from GooglePatentsPdfDownloader.patent_downloader import patent_downloader
patent_downloader = patent_downloader(verbose = True)

# Download a single patent to the current working directory
patent_downloader.get_pdf(patent = "US4405829A1", output_path = "", driver_file = "chromedriver.exe")

# Download multiple patents using a list of inputs to the current working directory
patent_downloader.get_pdfs(patents = ["US4405829A1", "EP0551921B1", "EP1304824B1"],
                           output_path = "", driver_file = "chromedriver.exe", 
                           remove_kind_codes = ["A1"])

# Download multiple patents using a txt file to the current working directory
patent_downloader.get_pdfs(file = "docs/data/patents.txt", output_path = "",
                           driver_file = "chromedriver.exe", remove_kind_codes = ["A1"])
```

## License

This repository is licensed under the MIT license.

See [here](https://github.com/lorenzbr/GooglePatentsPdfDownloader/blob/master/LICENSE) for further information.