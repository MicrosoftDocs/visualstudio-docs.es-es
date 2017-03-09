---
title: "Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla &#250;nica (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla &#250;nica (Object Relational Designer)
[Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md) admite la herencia de tabla única normalmente implementada en los sistemas relacionales.En este tutorial se amplían los pasos genéricos descritos en el tema [Cómo: Configurar herencia usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) y se proporcionan algunos datos reales para mostrar el uso de la herencia en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Durante este tutorial realizará las tareas siguientes:  
  
-   Crear una tabla de base de datos y agregar datos a la tabla.  
  
-   Crear una aplicación de Windows Forms.  
  
-   Agregar un archivo de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un proyecto.  
  
-   Crear nuevas clases de entidad.  
  
-   Configurar las clases de entidad de modo que usen la herencia.  
  
-   Consultar la clase heredada.  
  
-   Mostrar los datos en un Windows Form  
  
## Crear una tabla de la que se va a heredar  
 Para ver cómo funciona la herencia, va a crear una pequeña tabla Person, que usará como clase base y, a continuación, va a crear un objeto Employee, que heredará de ella.  
  
#### Para crear una tabla base con el fin de mostrar la herencia  
  
1.  En el **Explorador de servidores**\/**Explorador de bases de datos**, haga clic con el botón secundario del mouse en el nodo **Tablas** y, a continuación, haga clic en **Agregar nueva tabla**.  
  
    > [!NOTE]
    >  Puede usar la base de datos Northwind o cualquier otra base de datos a la que pueda agregar una tabla.  
  
2.  En el Diseñador de tablas, agregue las siguientes columnas a la tabla:  
  
    |Nombre de columna|Tipo de datos|Permitir valores nulos|  
    |-----------------------|-------------------|----------------------------|  
    |Id.|int|False|  
    |Tipo|int|True|  
    |Nombre|nvarchar\(200\)|False|  
    |Apellido|nvarchar\(200\)|False|  
    |Administrador|int|True|  
  
3.  Establezca la columna Id. como clave principal.  
  
4.  Guarde la tabla y asígnele el nombre Person.  
  
## Agregar datos a la tabla  
 Para poder comprobar que la herencia está correctamente configurada, la tabla necesita algunos datos por cada clase en la herencia de tabla única.  
  
#### Para agregar datos a la tabla  
  
1.  Abra la tabla en la vista de datos.\(Haga clic con el botón secundario del mouse en la tabla **Person** en el **Explorador de servidores**\/**Explorador de bases de datos** y, a continuación, haga clic en **Mostrar datos de tabla**.\)  
  
2.  Copie los datos siguientes en la tabla.\(Puede copiarlos y, a continuación, pegarlos en la tabla seleccionando toda la fila en el [Results Pane](http://msdn.microsoft.com/es-es/3c712f20-7c9f-4021-b1ac-fdc6f534c95a).\)  
  
    ||||||  
    |-|-|-|-|-|  
    |Id.|Tipo|Nombre|Apellido|Administrador|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## Crear un nuevo proyecto  
 Ahora que ha creado la tabla, cree un nuevo proyecto para mostrar la configuración de la herencia.  
  
#### Para crear una nueva aplicación para Windows  
  
1.  Desde el menú **Archivo**, cree un proyecto nuevo.  
  
2.  Asigne al proyecto el nombre InheritanceWalkthrough.  
  
    > [!NOTE]
    >  El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se admite en proyectos de Visual Basic y de C\#.Cree el nuevo proyecto en uno de estos lenguajes.  
  
3.  Haga clic en la plantilla **Aplicación de Windows Forms** y, a continuación, en haga clic en **Aceptar**.Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
4.  Se crea el proyecto InheritanceWalkthrough y se agrega al **Explorador de soluciones**.  
  
## Agregar un archivo de clases de LINQ to SQL al proyecto  
  
#### Para agregar un archivo de LINQ to SQL al proyecto  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  Haga clic en la plantilla **Clases de LINQ to SQL** y, a continuación, haga clic en **Agregar**.  
  
     El archivo .dbml se agrega al proyecto y se abre el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Crear la herencia mediante Object Relational Designer  
 Configure la herencia arrastrando un objeto **Herencia** desde el **Cuadro de herramientas** hasta la superficie de diseño.  
  
#### Para crear la herencia  
  
1.  En el **Explorador de servidores**\/**Explorador de bases de datos**, navegue a la tabla **Person** que creó anteriormente.  
  
2.  Arrastre la tabla **Person** hasta la superficie de diseño del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Arrastre una segunda tabla **Person** hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y cambie su nombre a Employee.  
  
4.  Elimine la propiedad **Administrador** del objeto **Person**.  
  
5.  Elimine las propiedades **Tipo**, **Id.**, **Nombre** y **Apellido** del objeto **Employee**.\(Es decir, elimine todas las propiedades menos **Administrador**.\)  
  
6.  Desde la pestaña **Object Relational Designer** del **Cuadro de herramientas**, cree una **Herencia** entre los objetos **Person** y **Employee**.Para ello, haga clic en el elemento **Herencia** del **Cuadro de herramientas** y suelte el botón del mouse.Después, haga clic en el objeto **Employee** y, a continuación, en el objeto **Person** del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].La flecha en la línea de herencia apuntará al objeto **Person**.  
  
7.  Haga clic en la línea **Herencia** en la superficie de diseño.  
  
8.  Establezca la propiedad **Discriminator** en **Tipo**.  
  
9. Establezca la propiedad **Valor de discriminador de clase derivada** en **2**.  
  
10. Establezca la propiedad **Valor de discriminador de clase base** en **1**.  
  
11. Establezca la propiedad **Predeterminado de herencia** en **Person**.  
  
12. Cree el proyecto.  
  
## Consultar la clase heredada y mostrar los datos en el formulario  
 Ahora, va a agregar código al formulario para consultar una clase concreta en el modelo de objetos.  
  
#### Para crear una consulta LINQ y mostrar los resultados en el formulario  
  
1.  Arrastre un control **ListBox** hasta el formulario Form1.  
  
2.  Haga doble clic en el formulario para crear un controlador de eventos `Form1_Load`.  
  
3.  Agregue el código siguiente al controlador de eventos `Form1_Load`:  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## Probar la aplicación  
 Ejecute la aplicación y compruebe que los registros mostrados en el cuadro de lista son todos empleados \(registros con el valor 2 en la columna Tipo\).  
  
#### Para probar la aplicación  
  
1.  Presione F5.  
  
2.  Compruebe que se muestran únicamente los registros con el valor 2 en la columna Tipo.  
  
3.  Cierre el formulario.\(En el menú **Depurar**, haga clic en **Detener depuración**.\)  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Cómo: Agregar clases de LINQ to SQL a un proyecto \(Object Relational Designer\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Cómo: Generar el modelo de objetos en Visual Basic o C\#](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)