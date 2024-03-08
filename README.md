Ticket Size = SWITCH(TRUE(),
                    [Banding] = "001_0 to 1 Lakh", "0-1 Lakh",
                    [Banding] = "002_1 to 2 Lakhs", "1-2 Lakh",
                    [Banding] = "003_2 to 2.5 Lakh", "2-2.5 Lakh",
                    [Banding] = "004_2.5 to 5 Lakh", "2.5 to 5 Lakh",
                    [Banding] = "005_above 5  Lakh", "Above 5 Lakh"
)
