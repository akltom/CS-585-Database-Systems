CREATE TABLE Salaries(
CheckNum INTEGER PRIMARY KEY,
Amount DECIMAL(8,2) NOT NULL
);

INSERT INTO Salaries
(CheckNum, Amount)
VALUES
(101,10000),
(102,10000),
(103,10000),
(104,10000),
(105,10000),
(106,20000),
(107,20000),
(108,20000),
(109,20000),
(110,20000),
(111,30000),
(112,40000);

CREATE TABLE SubTable AS
SELECT Amount AS AmountTwo, COUNT(Amount) AS CountNum
FROM Salaries
GROUP BY Amount;

SELECT AmountTwo, CountNum
FROM SubTable 
WHERE CountNum = (SELECT MAX(CountNum) FROM SubTable);






