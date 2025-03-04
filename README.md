# Dax-query-3-m-sales-avg
Dax query to retrieve the last 3 month sales and its avg

Write a dax query to retrieve the last 3 month sales and its avg

    Last 3 Month Sales = 
    VAR CurrentDate = TODAY()
    VAR StartDate = EOMONTH(CurrentDate, -4) + 1 
    VAR EndDate = EOMONTH(CurrentDate, -1) 
    RETURN
    CALCULATE(
    SUM(Sales[Amount]), 
    DATESBETWEEN( 
        Calendar[Date], 
        StartDate,
        EndDate ))
        
And create another measure

    Last 3 Month Average Sales = 
          DIVIDE(
    [Last 3 Month Sales], 
    CALCULATE( 
        DISTINCTCOUNT(Calendar[Month]), 
        DATESBETWEEN( 
            Calendar[Date], 
            StartDate, 
            EndDate )))
