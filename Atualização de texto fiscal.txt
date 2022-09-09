Atualização de texto fiscal:
executar primeiro 1 depois o 2.

1-
USE [MISTERCHEFNET]
GO
CREATE TRIGGER [dbo].[VoxyTextoFiscal]
ON [dbo].[Estoque]
AFTER INSERT,UPDATE
AS
BEGIN
IF EXISTS(SELECT TOP 1 [texto fiscal] FROM estoque WHERE [texto fiscal]!=[nome produto])
BEGIN
UPDATE estoque
SET [texto fiscal]=[nome produto]
WHERE [texto fiscal]!=[nome produto]
END
END

2-
UPDATE estoque
SET [texto fiscal]=[nome produto]
WHERE [texto fiscal]!=[nome produto]
