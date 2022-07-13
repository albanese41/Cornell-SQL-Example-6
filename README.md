SELECT O.first_name, O.last_name,

TIMESTAMPDIFF (YEAR, O.birthdate, CURDATE()) AS age,

M.model_name

FROM Owners AS O

INNER JOIN Customer_Guitars AS CG

ON O.owners_id = CG.owner_id

INNER JOIN Guitars AS G

On CG.guitar_id = G.guitar.id

INNER JOIN Models AS M

ON G.model_name = M.model_name

WHERE O.owner_id =

(SELECT owner_id

FROM Owners

WHERE birthdate = (SELECT MAX(birthdate) FROM Owners))

ORDER BY O.owner_id;
