# Power-Platform
 Symbol         - https://pictogrammers.com/library/mdi/
 Dashboard      - [https://dribbble.com/](https://dribbble.com/search/dashboard)
 
 Git Hub
 https://microsoftlearning.github.io/PL-200-Power-Platform-Functional-Consultant/

# Calendar Auto table genrated
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


# Remove bank Columns and rows PQ Function
   
     (Source as table) =>
        let
            #"Removed Blank Rows" = Table.SelectRows(Source, each not List.IsEmpty(List.RemoveMatchingItems(List.Transform(List.RemoveMatchingItems(Record.FieldValues(_), {"", null}), each try Text.Clean(Text.Trim(_)) otherwise _ ) , {""}))),
            #"Removed Blank Cols" = Table.SelectColumns(#"Removed Blank Rows" , List.Select(Table.ColumnNames(#"Removed Blank Rows"), each List.NonNullCount(List.Transform(Table.Column( #"Removed Blank Rows", _) , each try if Text.Clean(Text.Trim(_)) = "" then null else _ otherwise _ ) ) > 0 ))
        in
            #"Removed Blank Cols"
