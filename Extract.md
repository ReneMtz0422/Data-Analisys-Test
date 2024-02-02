  # Extraction

Now we know the problem i start whit the extract dataset for the database.
For this phase i first need to know the project number to filter from "MasAdmin" Software and get all the purchase orders in pdf

1.-Illustrative Example of a purchase order:

  - ![imagen](https://github.com/ReneMtz0422/Data-Analisys-Test/assets/158523436/312d1142-6058-4895-971d-b43db145159d)
  - 
      Note: In the example i am not using any sensitive information cause of privacy policies
    

Once I got all the purchase orders i have to load all the information in an excel format

2.- Illustrative Example of the excel database used

  ![imagen](https://github.com/ReneMtz0422/Data-Analisys-Test/assets/158523436/0ddff637-90f6-4a1c-b3d3-4bb2f3be7c58)
  
   Note: The values on the columns Cant,M.N.Prec, M.N.IVA, M.N.Subtotal and M.N.Total are empty since i will use a python script to generate values since this is part of the sensitive information that is not
   being used because of privacy policies, there are even columns that are not being used for the same reason but in my main file they were neccesary for the analysis


Now that we have our dataset we can start completing the empty values for the empty columns.

I made a simple code to do it random so that´s why this is only a analysis test and not a real one.

The code is on python and i use Visual studio Code to work on it.

For this you need to download the library openpyxl that you can install using pip on the Visual studio Code terminal you only need te next script

    pip install openpyxl


Once you have it installed you can use the code to generate the values

    import openpyxl
    import random

    # Seleccionar ruta de archivo de Excel
    excel_file_path = r'\\Netpoint_NAS\René Martinéz\Documentacion de Proyecto\OC_Datos_Prueba.xlsx'

    # Cargar archivo de Excel
    workbook = openpyxl.load_workbook(excel_file_path)
    sheet = workbook['OC']

    # Leer la ultima fila utilizada
    first_row = sheet.min_row+1
    last_row = sheet.max_row

    # Gemerar numeros aleatorios
    for row_num in range(first_row, last_row + 1):
        Cantidad_piezas = random.randint(1,100)
        Precio_unitario = round(random.uniform(0.30, 4000),2)
        subtotal = round(Cantidad_piezas*Precio_unitario,2)
        iva = round(subtotal * .16 , 2)
        total = round(iva + subtotal)

        # Escribir Datos en archivo
        sheet.cell(row=row_num, column=3).value = Cantidad_piezas
        sheet.cell(row=row_num, column=7).value = Precio_unitario
        sheet.cell(row=row_num, column=9).value = subtotal
        sheet.cell(row=row_num, column=8).value = iva
        sheet.cell(row=row_num, column=10).value = total

    # Guardar los cambios en el archivo
    workbook.save(excel_file_path)

    print("Valores Generados y guardados correctamente")

Once we run the code our excel will look like this

3.- Excel Dataset Whitout empty columns

  ![imagen](https://github.com/ReneMtz0422/Data-Analysis-Test/assets/158523436/8a670973-0461-4b0c-97d4-58811fe3c1e4)



    




