  # Transform Data
  
Now we start whit the data Transformation.

First step is to clean the data.

The filter of this information was made before because we extract the information manually from the pdf files so we only extract the information we need.

I assigned to the columns their data format on the home tab selecting the column and asigning every column a tipe

![Formato](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/72a87b8b-8eea-4c6d-aa12-22636e76a68a)


For the columns Servicio, Orden de Compra, Unidad, Descripción, Especialidad y Grupo i used the Text Format.

For the column Cant. i use the Number Format.

For the column Fecha de entrega i use short date Format.

For the columns M.N. Prec, M.N.Iva, M.N.Subtotal, M.N.Total i use accounting Format.

Now that i have the principal dataset i have to know what other information i need. In this case i need how much money i have been spending on every material individually and how much i am charging so i can know the difference in this two. For this i make a second page on excel where i divide every material individually considering the service number so i can distinguish which service is being charged for the material.

For this i copy all the description material and his service number to this new page and use the "Erase Duplicates" function on the data tab 

![Duplicados](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/a92e3101-0f1e-47b1-a7d1-35a0e1d6613a)

Then i need to know for every description individualy how much i was spending. For this i use the "=SUM.IF" function on excel to leave it like this 

Function :

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/702a384f-427c-4c58-b7b4-548d9a44d00c)

Final Result on Page

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/b9bb4f58-8365-402b-8b64-db278b5ee32c)

The next step was only copy the column to the next time on the format accounting and like values and not like a function

To complete this page i just end teaming whit the estimation team to know how much of the project has been charged to the client. In this case i use a random number generator that i programed on python to protect the company information where i assigne a range below what has been purchased in terms of cost since we are generally below that number.

And the code ended like this :

    import openpyxl
    import random

    # Cargar archivo de excel
    excel_file_path = r'\\Netpoint_NAS\René Martinéz\Documentacion de Proyecto\OC_Datos_Prueba.xlsx'
    workbook = openpyxl.load_workbook(excel_file_path)
    sheet = workbook['Comparacion']

    # Leer la columna de costos
    columna_costo = sheet['D']

    # Generar numero de manera aleatoria

    for cell in columna_costo [1:]:
        gasto_total = float(cell.value)
        numero_aleatorio = random.uniform (0, gasto_total)
        cell.offset(column=1).value = numero_aleatorio

    # Guarda los cambios en el archivo de Excel
    workbook.save(r'\\Netpoint_NAS\René Martinéz\Documentacion de Proyecto\OC_Datos_Prueba.xlsx')

    print("Los costos se generaron aleatoriamente")
    
When i run it this was the result:

![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/623e25ca-182b-4c88-b907-b269d3ece80f)

Now that the dataset are ready i can continue whit the Load procces

Next step is Loading

[Loading Procces](Load_data.md)







