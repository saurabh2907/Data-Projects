VAR TopRank = 
    RANKX(
        SUMMARIZE(
            FILTER(YourTable, YourTable[Segment] = 'par'),
            YourTable[Product],
            "Amount", SUM(YourTable[Amount])
        ),
        [Amount],
        DESC
    )

VAR TopProducts = 
    FILTER(
        SUMMARIZE(
            FILTER(YourTable, YourTable[Segment] = 'par'),
            YourTable[Product],
            "Amount", SUM(YourTable[Amount])
        ),
        TopRank <= EARLIER(TopRank)
    )

RETURN
    TopProducts
