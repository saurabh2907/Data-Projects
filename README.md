TOPN(
    1,
    FILTER(
        SUMMARIZE(
            YourTable,
            YourTable[Product],
            "TotalAmount", SUM(YourTable[Amount])
        ),
        YourTable[Segment] = "par"
    ),
    [TotalAmount],
    DESC
)
