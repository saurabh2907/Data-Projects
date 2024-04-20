FilterTop3ByCat_Filter =
VAR Top3Cat =
    CALCULATETABLE (
        GENERATE (
            VALUES ( 'Product'[Category] ),
            TOPN (
                3,
                CALCULATETABLE ( VALUES ( 'Product'[Product Name] ) ),
                [Sales Amount]
            )
        ),
        ALLSELECTED()
    )
RETURN
    CALCULATE (
        1 * ( NOT ISEMPTY ( 'Product' ) ),
        KEEPFILTERS ( Top3Cat )
    )
