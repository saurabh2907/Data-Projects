= Date.AddYears(Date.FromText(Text.Middle([Month Column],0,4)),if Number.FromText(Text.End([Month Column],3)) > 6 then 1 else 0)
