# proyecto
EJERCICIOS DBEAVER
1-
SELECT DISTINCT Title
FROM Album
WHERE AlbumId <=13


2-
SELECT *
FROM Customer c
ORDER BY Country


3-
INSERT INTO MediaType (NameId)
VALUES (‘CD’)


4-
SELECT *
FROM Customer c
WHERE Company ISNULL


5-
SELECT
Album.AlbumId,
Album.Title AS Album_Title,
Artist.Name AS Artist
FROM Album
INNER JOIN	Artist ON Album.ArtistId = Artist.ArtistId;

6-
SELECT t.TrackId, t.Name , a2.Title
FROM Track t , Album a2
LEFT JOIN Album a
ON t.TrackId = a2.Title

7-
SELECT t.TrackId, t.Name AS TrackName, mt.Name AS MediaTypeName
FROM Track t
RIGHT JOIN MediaType mt
ON t.MediaTypeId = mt.MediaTypeId;








8-
SELECT i.InvoiceLineId , i.UnitPrice , i.Quantity , t.Milliseconds
FROM InvoiceLine i FULL OUTER JOIN Track t
ON i.TrackId = t.TrackId
ORDER BY t.Milliseconds DESC


9-
SELECT FirstName
FROM Customer c
UNION 
SELECT FirstName
FROM Employee e


10-
SELECT *
FROM Invoice Line
WHERE TrackId IN (
	SELECT TrackId
	FROM Track
	WHERE AlbumId IN (
		SELECT AlbumId
		FROM Album
		WHERE ArtistId IN (
			SELECT ArtistId
			FROM Artist
			WHERE Name = ‘Queen’
		)
	)
);


11-
SELECT i.InvoiceId , i.Total
	FROM Invoice i 
	GROUP BY i.InvoiceId
		ORDER BY i.Total DESC


12-
SELECT InvoiceLineId, 
SUM (UnitPrice * Quantity) AS Total
FROM InvoiceLine
GROUP BY InvoiceLineId
HAVING InvoiceLineId BETWEEN 150 AND 160;
13-
SELECT
InvoiceLineId,
UnitPrice,
CASE
	WHEN UnitPrice > 1 THEN ‘Precio normal’
	ELSE ‘Promoción’
END AS TipoPrecio
FROM InvoiceLine;
