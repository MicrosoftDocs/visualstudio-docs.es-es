---
title: "Tutorial: Crear clases LINQ to SQL mediante la herencia de tabla única (Object Relational Designer) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b6e255492f0859689b41723657338140ffee5931
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla única (Object Relational Designer)
El [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) admite la herencia de tabla única normalmente implementada en los sistemas relacionales. En este tutorial se expande en los pasos genéricos proporcionados en el [Cómo: configurar la herencia utilizando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tema y proporciona algunos datos reales para demostrar el uso de la herencia en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Durante este tutorial realizará las tareas siguientes:  
  
-   Crear una tabla de base de datos y agregar datos a la tabla.  
  
-   Crear una aplicación de Windows Forms.  
  
-   Agregar un archivo de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un proyecto.  
  
-   Crear nuevas clases de entidad.  
  
-   Configurar las clases de entidad de modo que usen la herencia.  
  
-   Consultar la clase heredada.  
  
-   Mostrar los datos en un Windows Form  
  
## <a name="create-a-table-to-inherit-from"></a>Crear una tabla de la que se va a heredar  
 Para ver cómo funciona la herencia, va a crear una pequeña tabla Person, que usará como clase base y, a continuación, va a crear un objeto Employee, que heredará de ella.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Para crear una tabla base con el fin de mostrar la herencia  
  
1.  En **Explorador de servidores**/**el Explorador de base de datos**, haga clic en el **tablas** nodo y haga clic en **agregar nueva tabla**.  
  
    > [!NOTE]
    >  Puede usar la base de datos Northwind o cualquier otra base de datos a la que pueda agregar una tabla.  
  
2.  En el Diseñador de tablas, agregue las siguientes columnas a la tabla:  
  
    |Nombre de columna|Tipo de datos|Permitir valores NULL|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**Type**|**int**|**True**|  
    |**FirstName**|**nvarchar (200)**|**False**|  
    |**Apellidos**|**nvarchar (200)**|**False**|  
    |**Administrador de**|**int**|**True**|  
  
3.  Establezca la columna Id. como clave principal.  
  
4.  Guarde la tabla y asígnele el nombre **persona**.  
  
## <a name="add-data-to-the-table"></a>Agregar datos a la tabla  
 Para poder comprobar que la herencia está correctamente configurada, la tabla necesita algunos datos por cada clase en la herencia de tabla única.  
  
#### <a name="to-add-data-to-the-table"></a>Para agregar datos a la tabla  
  
1.  Abra la tabla en la vista de datos. (Haga clic en el **persona** tabla **Explorador de servidores**/**el Explorador de base de datos** y haga clic en **mostrar datos de tabla**.)  
  
2.  Copie los datos siguientes en la tabla. (Puede copiarlo y, a continuación, péguelo en la tabla seleccionando la fila completa en el panel de resultados.)  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**Type**|**FirstName**|**Apellidos**|**Administrador de**|  
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Bermejo**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**Tai**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**María**|**Martin**|**3**|  
    |**12**|**2**|**Ken**|**Kwok**|**3**|  
  
## <a name="create-a-new-project"></a>Crear un nuevo proyecto  
 Ahora que ha creado la tabla, cree un nuevo proyecto para mostrar la configuración de la herencia.  
  
#### <a name="to-create-the-new-windows-forms-application"></a>Para crear la nueva aplicación de Windows Forms  
  
1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .  
  
2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.  

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.  

4. Denomine el proyecto **InheritanceWalkthrough**y, a continuación, elija **Aceptar**. 
  
     El **InheritanceWalkthrough** proyecto se crea y se agrega a **el Explorador de soluciones**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Agregar un archivo de clases de LINQ to SQL al proyecto  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Para agregar un archivo de LINQ to SQL al proyecto  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2.  Haga clic en el **clases LINQ to SQL** plantilla y, a continuación, haga clic en **agregar**.  
  
     El archivo .dbml se agrega al proyecto y se abre el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Crear la herencia mediante Object Relational Designer  
 Configurar la herencia arrastrando un **herencia** objeto desde el **cuadro de herramientas** a la superficie de diseño.  
  
#### <a name="to-create-the-inheritance"></a>Para crear la herencia  
  
1.  En **Explorador de servidores**/**el Explorador de base de datos**, navegue hasta la **persona** tabla que creó anteriormente.  
  
2.  Arrastre el **persona** de tabla en la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] superficie de diseño.  
  
3.  Arrastre una segunda **persona** de tabla en la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y cambie su nombre a **empleado**.  
  
4.  Eliminar el **Manager** propiedad desde el **persona** objeto.  
  
5.  Eliminar el **tipo**, **identificador**, **FirstName**, y **LastName** propiedades desde el **empleado** objeto. (En otras palabras, elimine todas las propiedades excepto **Manager**.)  
  
6.  Desde el **Object Relational Designer** pestaña de la **cuadro de herramientas**, crear un **herencia** entre el **persona** y  **Empleado** objetos. Para ello, haga clic en el **herencia** de elemento en el **cuadro de herramientas** y suelte el botón del mouse. A continuación, haga clic en el **empleado** objeto y, a continuación, el **persona** objeto en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. La flecha situada en la línea de herencia apuntará a la **persona** objeto.  
  
7.  Haga clic en el **herencia** línea en la superficie de diseño.  
  
8.  Establecer el **propiedad Discriminator** propiedad **tipo**.  
  
9. Establecer el **valor de discriminador de clase derivada** propiedad **2**.  
  
10. Establecer el **valor de discriminador de clase Base** propiedad **1**.  
  
11. Establecer el **predeterminado de herencia** propiedad **persona**.  
  
12. Compile el proyecto.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Consultar la clase heredada y mostrar los datos en el formulario  
 Ahora, va a agregar código al formulario para consultar una clase concreta en el modelo de objetos.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Para crear una consulta LINQ y mostrar los resultados en el formulario  
  
1.  Arrastre un **ListBox** hasta Form1.  
  
2.  Haga doble clic en el formulario para crear un controlador de eventos `Form1_Load`.  
  
3.  Agregue el código siguiente al controlador de eventos `Form1_Load`:  
  
    ```vb  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```csharp  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ejecute la aplicación y compruebe que los registros mostrados en el cuadro de lista son todos empleados (registros con el valor 2 en la columna Tipo).  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  Presione F5.  
  
2.  Compruebe que se muestran únicamente los registros con el valor 2 en la columna Tipo.  
  
3.  Cierre el formulario. (En el **depurar** menú, haga clic en **Detener depuración**.)  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Generación del modelo de objetos en Visual Basic o C#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)