Premium Frequency = SWITCH(TRUE(),
                            _003_Age_banding_Summary[PREM_FREQ] = "1", REPT(UNICHAR(8203),5)&"Yearly",
                            _003_Age_banding_Summary[PREM_FREQ] = "4", REPT(UNICHAR(8203),4)&"Quaterly",
                            _003_Age_banding_Summary[PREM_FREQ] = "2", REPT(UNICHAR(8203),3)&"Half-Yearly",
                            _003_Age_banding_Summary[PREM_FREQ] = "12", REPT(UNICHAR(8203),2)&"Monthly",
                            _003_Age_banding_Summary[PREM_FREQ] = "0", REPT(UNICHAR(8203),1)&"SP"
)
