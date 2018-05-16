CREATE TABLE CosineTable(
  Angle INTEGER NOT NULL UNIQUE,
  CosValue NUMERIC(6,5) NOT NULL,
  PRIMARY KEY(Angle));
  
INSERT INTO CosineTable 
(Angle,CosValue)
VALUES
(0,1),
(5,0.9962),
(10,0.9848),
(15,0.9659),
(20,0.9397),
(25,0.9063),
(30,0.866),
(35,0.8192),
(40,0.766),
(45,0.7071),
(50,0.6428),
(55,0.5736),
(60,0.5),
(65,0.4226),
(70,0.342),
(75,0.2588),
(80,0.1736),
(85,0.0872),
(90,0);


SELECT Mini.CosValue + (Maxi.CosValue - Mini.CosValue) * (73 - Mini.Angle) / (Maxi.Angle - Mini.Angle)
FROM CosineTable Mini, CosineTable Maxi
WHERE Mini.Angle = (SELECT Max(Angle) FROM CosineTable WHERE Angle < 73)
AND   Maxi.Angle = (SELECT MIN(Angle) FROM CosineTable WHERE Angle > 73);