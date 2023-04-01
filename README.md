
<a name="readme-top"></a>



<!-- PROJECT LOGO -->
<br />
<div align="center">
    <img src="https://challengedata.ens.fr/logo/public/CFM_CoRGB_300dpi_Tight_box.png" alt="Logo" width="200" height="200">

  <h3 align="center">CFM CHALLENGE 2020</h3>

  <p align="center">
    Predicting where will the next trade take place, using machine learning
    <br />
    <a href="https://challengedata.ens.fr/challenges/40">Challenge Link</a>
  </p>

</div>


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#challenge-context">Challenge Context</a>
    </li>
      <li><a href="#challenge-goals">Challenge Gaols</a></li>
    <li>
      <a href="#data-description">Data Description</a>
    </li>
    <li><a href="#running-notebook">Running The Notebook</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>






## Challenge Context

Most financial markets use an electronic trading mechanism called a limit order book to facilitate the trading of assets (stocks, futures, options, etc.). Participants submit (or cancel) orders to this electronic order book. These orders are requests to buy or sell a given quantity of an asset at a specified price, thus allowing buyers to be matched with sellers at a mutually agreed price [1][2]. Since an asset can be traded on multiple trading venues, participants can choose to which venue they send an order. For instance, a US stock can be traded on various exchanges, such as NYSE, NASDAQ, Direct Edge or BATS. When sending an order, participants generally select the best available trading venue at that time [3]. Their decisions may include a statistical analysis of past venue activity.

## Challenge Goals

Given recent trades and order books from a set of trading venues, predict on which trading venue the next trade will be executed.

## Data Description

The dataset is stored in an HDF5 file and can be loaded with pandas by running the following command:
```
>>> train_data = pandas.read_hdf("train_data.h5", 'data')
```
Labels are stored in a CSV file and can be loaded as follows:
```
>>> labels = pandas.read_csv("train_labels.csv")
```
Description of rows in the dataset
For each row, we want predict on which venue the next trade will be executed. The stock is represented by a randomized stock_id and the day by a randomized day_id.

Each row provides a description of six order books, from six trading venues, and a history of trades for the corresponding asset.

Order books
An order book lists the quantities of an asset that are currently on offer by sellers (who ask for higher prices) and the quantities that buyers wish to acquire (who bid at lower prices). The six order books (one for each trading venue) are described in the dataset through the best two bids and best two asks (which makes them respectively the two highest bid prices of the buyers and the two lowest ask prices of the sellers).

We call aggregate volume the sum of all quantities on both the bid and ask sides (only considering the best two bids and best two asks) in the six given books.

We also define the aggregate mid-price as the average of the best bid among the six books (i.e. the maximum of the best six bids) and the best ask among the six books (i.e. the minimum of the best six asks).

Each of the six books is described as follows:

The 'bid' column (respectively 'ask') represents the difference between the best bid (respectively best ask) and the aggregate mid-price, expressed in some fixed currency unit.

The 'bid1' column (respectively 'ask1') represents the difference between the second best bid (respectively second best ask) and the aggregate mid-price, expressed in some fixed currency unit.

The 'bid_size' column (respectively 'ask_size') represents the total number of stocks available at the best bid (respectively best ask) divided by the aggregate volume.

The 'bid_size1' column (respectively 'ask_size1') represents the total number of stocks available at the second best bid (respectively at the second best ask) divided by the aggregate volume.

The 'ts_last_update' column corresponds to the timestamp, given as a number of microseconds since midnight (local time), of the last update of the book.

A NAN value indicates an empty book or a partially empty book.

Note that all prices are expressed in the same fixed currency unit.

Besides, since all the trading venues belong to the same time zone, all the timestamps have the same time reference.

Trades
Each row also comprises a description of the ten last trades (ordered from the most recent one to the oldest one) for the corresponding asset. A trade represents a transaction of a certain quantity of an asset at a given price between a buyer and a seller. Most trade result from the matching of an order in an order book with an incoming order but they can also result from a different trading mechanism such as auctions. Trades often involve fees, paid by the buyer and the seller, which vary from one trading venue to another. The ten trades from the history of trades are given are described as follows:

Its quantity ('qty'): the number of stocks traded, divided by the aggregate volume (defined above in the section "Order book").

Its timestamp ('tod'): when the trade was executed, given as a number of microseconds since midnight (local time).

Its price ('price'), representing the difference between the trade price with the aggregate mid-price (defined in the section "Order book"), expressed in some fixed currency unit.

Its source ('source_id') representing the trading venue on which this particular trade was executed.

Description of labels
The labels correspond to the trading venues to predict. Each of the six trading venues is represented by a number between 0 and 5.

### Running The Notebook


1. To download the data go to : https://challengedata.ens.fr/challenges/40 , create an account and download the data.
2. Install the packages, recommended to use a virtual environment.
```
pip install -r requirements.txt
```
3. Open the notebook
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Tariq Massaoudi - [@linkedin](https://www.linkedin.com/in/tariqmassaoudi/) - tariq.massaoudi@gmail.com

Personal Website: [Tariq Massaoudi](https://tariqmassaoudi.com)

<p align="right">(<a href="#readme-top">back to top</a>)</p>




<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/tariqmassaoudi/two-subs/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/tariqmassaoudi/two-subs/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/packagist/stars/tariqmassaoudi/two-subs
[stars-url]: https://github.com/tariqmassaoudi/two-subs
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/tariqmassaoudi/two-subs/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/tariqmassaoudi/two-subs/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/tariqmassaoudi/
[product-screenshot]: images/screenshot.png

