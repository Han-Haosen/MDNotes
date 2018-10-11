# SQL Learning Notes

Wildcard

e.g

SELECT prod_id,prod-name FROM Products
WHERE
Prod_name LIKE 'Fish%' //all starts with fish
//accepting anything after fish
//microsoft Access uses *

or where
prod_name LIKE '%bean bag%' //as long as bean bag appear

using _ as wildcard

one char

//Access uses ? not _

WHERE prod_name LIKE '__ inch teddy bear';

[]// only supported by SQL server and Access

e.g find all contact start with J or M

FROM Customers
WHERE cust_contact LIKE '[JM]%'
ORDER BY cust_contact;


concatenate 

"+ or || depends on server "

SELECT vend_name + '(' + vend_country + ')'
FROM Vendors
ORDER BY vend_name;
