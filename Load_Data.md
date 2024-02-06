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

For this we use the button New Column on the Home tab 

![nueva columna](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/c166c498-9f51-4907-be00-03fae9bbe524)

And then i use the next codes to do it.

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

Once i finish the "calendar" table i move into the "Comparacion" table to start working on it.
I will create 3 new columns "Diferencia" that will tell me the diference between what was been spent and what was been charged, "Margen" which will tell me what percentage represents this difference between what was collected and what was spent, "RGB" This  column will represent a control within the range in which green will be taken into account as within the range, yellow with caution and red as already over the range.

Now For Diferencia we use the next code:

      Diferencia = Comparacion[Gasto Total Pesos] - Comparacion[Cobrado Total]    

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/900b35a4-6d90-40e0-85c1-a84b065701a0)

For Margen:

      Margen = Comparacion[Cobrado Total] / Comparacion[Gasto Total Pesos]

In the case of this column we will use the percentage function that is in the column tool tab so that the result of the code is in percentage

![Porcentaje](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/9b2ec05e-c294-40bc-9ff2-bbcbac6100e3)

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/5a8ec231-5ef4-4f5d-8fdf-42ffb3733d84)

For RGB:

      RGB = IF(Comparacion[Margen] >= .70, "Red",
        IF(Comparacion[Margen] >= .60 && Comparacion[Margen] <= .69, "Yellow", "Green"))

Result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/6f32a251-109d-433f-82e3-39dc46b4cbd8)

Now Every column and table is ready i need to create the relations between the tables for this first i will go to the "model view" tab

And this is what you should see

!![Modelo](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/5883146f-2bca-467d-9722-6497518eeade)

Now to create the relationships we have to drag the "date" column from the calendar table to the OC table with the "F.Entrega" column and you will see the following tab, it will recomment a tyoe of relationship and you will have to judge if it is the necessary relationship or you will have to change it, in this case it is the relationship we need.

Table that you will see:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/bb49702d-834b-480b-a177-c08fd2039ed9)

And we create the next relation between the table "Comparacion" and the "OC" table whit the "Descripcion" Column on both tables

The final result will be this relations

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/24e17986-fe1e-4954-b5ef-9b760208944f)

Now the final step is work on the Visualization for the storytelling and final results of the project

[Visualization](Visualice_data.md)







