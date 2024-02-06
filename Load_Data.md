   # Loading The Data
   
Now that already i have the dataset´s ready it´s time to start working on Power BI, in first instance we open a new power BI file

I load the Data in the home tab from power bi i select the function "Obtain data" 

![obtener data](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/9fad71b8-9602-496c-92b8-b3d4f4180b70)

We should use the "Excel book" option

![excel book](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/f89e1a79-7e71-4177-8c3a-828965e53716)

Then i select the Excel file that we start working on the first instance of the project.

Once the dataset is charged on PowerBI we check all the information is charged whithout errors.

We move to the "View table" tab 

![tabla](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/0e222c0e-0ebb-44b5-b62e-fd68a2ba6ee5)

And we check that the data is correct. This is what we should see, And you should check the tables and columns on the data tab at the right

![columnas](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/6b70d3eb-9999-44ce-b434-d3094c07e454)

And then we start working on the Power BI DAX.

I start creating a new table on the home tab using the function "new table".

![tabla](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/96bdccb7-9bd7-427f-b048-140b3780d6c4)


I will create a calendar so first on the function tab we use the next code.

      Calendario = CALENDAR(MIN('OC (2)'[F.Entrega]),MAX('OC (2)'[F.Entrega]))

The minimun and maximun function is used to avoid null values within our visualization

And the result will we the next

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/b8461112-25b5-4d00-94ef-7ae30427b5d8)

Now I separate according to the needs of the project in this case i only need year, month, month description (First 3 letters), day and day description (First 3 Letters).
I use the next codes to do it.

For Year : 

      Año = YEAR(Calendario[Date])

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/397f29f4-2adf-4271-bb9e-82b22df6c7f2)


Note: Now i don´t need the max and min function because i am calling the "Calendario" table and this is for the next functions to.

For Month : 

      Mes = MONTH(Calendario[Date])

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/afb0fa1e-a681-4462-8b38-c99e36487dd0)

Mont Description:

      Mes_Desc = FORMAT(Calendario[Date],"MMM")

Note: The format function is to assign ho many characters the function will print

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/4026acc5-92df-4abc-a51a-f640bf549053)


For Day :

      Dia = DAY(Calendario[Date])

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/6f8021bf-2de4-462a-abb4-3ecb30f98987)

For Day Description :

      Dia_Desc = FORMAT(Calendario[Date],"DDD")

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/08b0d3d8-e75a-4ede-bb7c-a6320f896286)


