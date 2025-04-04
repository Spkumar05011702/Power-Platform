# Power-Platform
 Symbol         - https://pictogrammers.com/library/mdi/
 Dashboard      - [https://dribbble.com/](https://dribbble.com/search/dashboard)



# Callender Auto 
        Date = 
        VAR BaseCalendar =
            CALENDAR ( DATE (2019, 1, 1), NOW() )
        RETURN
            GENERATE(
                BaseCalendar,
                VAR BaseDate = [Date]
                RETURN ROW (
                    "DateKey", FORMAT (BaseDate, "yyyymmdd"),
                    "Year", YEAR(BaseDate),
                    "MonthName", FORMAT(BaseDate, "mmmm"),
                    "MonthNumber", FORMAT(BaseDate, "m"),
                    "Quarter", "Qtr " & FORMAT(BaseDate, "q")
                )
            )

 
