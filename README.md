CALCULATETABLE(
    SUMMARIZE(
        FILTER(
            YourTable,
            YourTable[Segment] = "par"
        ),
        YourTable[Product],
        "Amount", SUM(YourTable[Amount])
    ),
    RANKX(
        SUMMARIZE(
            FILTER(
                YourTable,
                YourTable[Segment] = "par"
            ),
            YourTable[Product],
            "Amount", SUM(YourTable[Amount])
        ),
        [Amount],
        DESC
    ),
    FILTER(
        RANKX(
            SUMMARIZE(
                FILTER(
                    YourTable,
                    YourTable[Segment] = "par"
                ),
                YourTable[Product],
                "Amount", SUM(YourTable[Amount])
            ),
            [Amount],
            DESC
        ),
        [Rank] = 1
    )
)
