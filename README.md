
# Stock Portfolio Risk Management

In this project we were give a pdf, which contains a list of stock with their respective 'Reco Date', 'Reco Price' and 'Exit Date', 'Exit Price'.

Now the given task at hand was to compute the minimum amount to investement we need to give from our pocket to maximize the profit/returns.

We were also give a constrains/conditions that we are allowed to invest one hundred thousand (or 1 lakh), for each stock, thus we built our algorithm on this basis.
## Authors

- [@yo-msh](https://github.com/yo-msh)
- [@ankit2210812](https://github.com/ankit2210812)


## Pre Requisite
- As the given condition stats that we will only invest one hundred thousand (or 1 lakh) for each stock, now this fund can either come from our pocket or from the surplus reture of some other stock.

- We will convert the given pdf into a EXCEL Sheet for better workability (we used a website to convert [pdf to excel](https://www.ilovepdf.com/pdf_to_excel))

- We also convert all the Date in the EXCEL into the format of **YYYYMMDD**, for example : from *Apr 15, 2024* to *20240425*

- This date convertion was done, as it is easier to sort date numerically and keeping the chorological order correct

- While investing we assume that we have a fund called 'remains', which initally will be zero, but while investing there would some residue amount left, which it store and all the return amount of any stock, be it in profit or loss will be stored in it.

- For all the stock who's ***Exit DATE*** isn't finalized yet, we will replace it by '-1'

## Algorithm

- So we for very first/initail stock, we have to spead money from our pocket, ie one hundred thousand (1 lakh) for that stock , we will add it into our funds called ***moneyinvested***, and if any amount is left, we will add it to the ***remains***, and push the ***ExitDate*** into the *priorityQueue* with its *returnAmount* for that stock.

- Now will we simple keep on purchasing all the stock till the end of the list, but before purchasing we will always check the front the *priorityQueue*,

    - If the ***RepoDate*** is less than ***ExitDate***, this indicates that the front stock has been matured and we will receive its returns, now we check if the return is more than one hundred thousand, 
        - If true, we will keep one hundred thousand aside, thus adding it into ***remains***, so that it can used to investing in other stock, and the remaing money will be consider pure profit
        - Else, just add it to ***remains***, as the return is less than one hundred thousand, thus we hit a loss
    
    - If the ***RepoDate*** is greater than ***ExitDate***, just buy the stock, and check if there are funds more then one hundred thousand in ***remains***, 
        - If true, use from ***remains*** for investing
        - Else, use money from our pocket

- Check if any stock has ***ExitDate*** of -1 :
    - If true that money invested won't be returned, so we will add it into another variable called ***corpusAmount***

- We will repeat the above step till the end of the list

