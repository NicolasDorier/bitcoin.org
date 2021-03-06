{% comment %}
This file is licensed under the MIT License (MIT) available on
http://opensource.org/licenses/MIT.
{% endcomment %}
{% assign filename="_includes/ref/bitcoin-core/rpcs/rpcs/listaddressgroupings.md" %}

##### ListAddressGroupings
{% include helpers/subhead-links.md %}

{% assign summary_listAddressGroupings="lists groups of addresses that may have had their common ownership made public by common use as inputs in the same transaction or from being used as change from a previous transaction." %}

{% autocrossref %}

*Requires wallet support.*

The `listaddressgroupings` RPC {{summary_listAddressGroupings}}

*Parameters: none*

*Result---an array of arrays describing the groupings*

| Name                   | Type              | Presence                    | Description
|------------------------|-------------------|-----------------------------|----------------
| `result`               | array             | Required<br>(exactly 1)     | An array containing the groupings.  May be empty
| →<br>Groupings         | array             | Optional<br>(0 or more)     | An array containing arrays of addresses which can be associated with each other
| → →<br>Address Details | array             | Required<br>(1 or more)     | An array containing information about a particular address
| → → →<br>Address       | string (base58)   | Required<br>(exactly 1)     | The address in base58check format
| → → →<br>Balance       | number (bitcoins) | Required<br>(exactly 1)     | The current spendable balance of the address, not counting unconfirmed transactions
| → → →<br>Account       | string            | Optional<br>(0 or 1)        | The account the address belongs to, if any.  This field will not be returned for change addresses.  The default account is an empty string ("")
{:.ntpd}

*Example from Bitcoin Core 0.10.0*

{% highlight bash %}
bitcoin-cli -testnet listaddressgroupings
{% endhighlight %}

Result (edited to only the first two results):

{% highlight json %}
[
    [
        [
            "mgKgzJ7HR64CrB3zm1B4FUUCLtaSqUKfDb",
            0.00000000
        ],
        [
            "mnUbTmdAFD5EAg3348Ejmonub7JcWtrMck",
            0.00000000,
            "test1"
        ]
    ]
]
{% endhighlight %}

*See also*

* [GetAddressesByAccount][rpc getaddressesbyaccount]: {{summary_getAddressesByAccount}}
* [GetTransaction][rpc gettransaction]: {{summary_getTransaction}}

{% endautocrossref %}
