# CutSqlFunction
Cut  function for string, Transact SQL


CREATE FUNCTION dbo.Cut(@text nvarchar(4000),
	@begin nvarchar(4000),
	@end nvarchar(4000))  
RETURNS nvarchar(max)   
AS   
BEGIN  
DECLARE @indexBegin int = CHARINDEX(@begin,@text);
if(@indexBegin=0)  RETURN NULL;
DECLARE @indexEnd int = CHARINDEX(@end,@text,@indexBegin);
if(@indexEnd=0) RETURN NULL;
RETURN SUBSTRING(@text,@indexBegin+1,@indexEnd-@indexBegin-1);
END;
