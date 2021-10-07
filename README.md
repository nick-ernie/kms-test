# KMS Test Task

## Cash machine

Implement interface to ATM cash. The device received commands from standard input and sends replies to standard output.


### Accepted commands:

#### Add notes:

    + <currency> <value> <number> 

&lt;currency> is 3 uppercase letters, any combination is valid 

&lt;value> is the value of notes. Valid values are 10n and 5*10n,  0<=n<=3 (although some currencies may have larger value notes and some odd values like 2,3,20,25, we do not allow them for simplification). 

&lt;number> is any positive integer 

Semantics: put notes into cash

Reply: OK if successful, ERROR if validation fails

Example:

    + USD 100 30

<span style="color:green">OK</span>.


#### Get cash:

    - <currency> <amount> 

&lt;currency> as described above, &lt;amount> any positive integer 

Semantics: get the sum from the cash if possible.

Reply: one line per each note value, formatted as <value> <number of notes>, followed with a line OK

ERROR if the amount is unavailable (cash remains unchanged).

Example:

    - USD 2000

<i style="color:green">100 20</i>

<i style="color:green">OK</i>


#### Print cash:

?

Reply: one line for each currency/value pair

    <currency> <value> <number> 

followed by the line OK

Lines are ordered by first currency, then by value.

Semantics: what is currently in the cash

Example: see in sample session.



(Cash machine output is shown in green italics).



Sample Session



?

<i style="color:green">OK</i>

    + USD 100 30

<i style="color:green">OK</i>

    + RUR 250 10

<i style="color:green">ERROR</i>

    + CHF 100 5

<i style="color:green">OK</i>

    + USD 10 50

<i style="color:green">OK</i>

    ?

<i style="color:green">CHF 100 5</i>

<i style="color:green">USD 10 50</i>

<i style="color:green">USD 100 30</i>

<i style="color:green">OK</i>

    - USD 120

<i style="color:green">100 1</i>

<i style="color:green">10 2</i>

<i style="color:green">OK</i>

    - RUR 500

<i style="color:green">ERROR</i>

    -  CHF 250

<i style="color:green">ERROR</i>

    ?

<i style="color:green">CHF 100 5</i>

<i style="color:green">USD 10 48</i>

<i style="color:green">USD 100 29</i>

<i style="color:green">OK</i>

    + eur 100 5

<i style="color:green">ERROR</i>

    -  CHF 400

<i style="color:green">100 4</i>

<i style="color:green">OK</i>

    +  CHF 10 50

<i style="color:green">OK</i>

    ?

<i style="color:green">CHF 10 50</i>

<i style="color:green">CHF 100 1</i>

<i style="color:green">USD 10 48</i>

<i style="color:green">USD 100 29</i>

<i style="color:green">OK</i>
