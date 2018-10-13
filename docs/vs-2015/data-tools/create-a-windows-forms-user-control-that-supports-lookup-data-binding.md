---
title: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e1779ab1d39a28e750cab757c94717d496b98ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231671"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cuando muestra datos en Windows Forms, puede elegir controles existentes en el **cuadro de herramientas**, o puede crear controles personalizados si la aplicación requiere funcionalidad no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> pueden contener tres propiedades que se pueden enlazar a los datos. Tales controles son similares a <xref:System.Windows.Forms.ComboBox>.  
  
 Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Al crear controles para su uso en escenarios de enlace de datos, necesita implementar uno de los siguientes atributos de enlace de datos:  
  
|Uso de atributos de enlace de datos|  
|-----------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos pero que también necesiten presentar una única columna o propiedad. (Este proceso se describe en esta página del tutorial.)|  
  
 Este tutorial crea un control de búsqueda que se enlaza a los datos de dos tablas. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind. El control de búsqueda se enlazará al campo `CustomerID` de la tabla `Orders`. Utilizará este valor para buscar `CompanyName` en la tabla `Customers`.  
  
 Durante este tutorial aprenderá a:  
  
-   Cree un nuevo **aplicación Windows**.  
  
-   Agregue un nuevo **Control de usuario** al proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `LookupBindingProperty`.  
  
-   Crear un conjunto de datos con el **configuración origen de datos** asistente.  
  
-   Establecer el **CustomerID** columna en el **pedidos** de tabla, en el **orígenes de datos** ventana, para utilizar el nuevo control.  
  
-   Cree un formulario para mostrar los datos en el nuevo control.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  
  
## <a name="create-a-windows-application"></a>Crear una aplicación de Windows  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, desde el **archivo** menú, cree un nuevo **proyecto**.  
  
2.  Denomine el proyecto **LookupControlWalkthrough**.  
  
3.  Seleccione **aplicación de Windows Forms**y haga clic en **Aceptar**.  
  
     El **LookupControlWalkthrough** se crea y agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="add-a-user-control-to-the-project"></a>Agregue un control de usuario al proyecto  
 Este tutorial crea un control de búsqueda de un **Control de usuario**, por tanto, agregue un **Control de usuario** elemento a la **LookupControlWalkthrough** proyecto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para agregar un control de usuario al proyecto  
  
1.  Desde el **proyecto** menú, seleccione **agregar Control de usuario**.  
  
2.  Tipo `LookupBox` en el **nombre** área y, a continuación, haga clic en **agregar**.  
  
     El **LookupBox** se agrega al control **el Explorador de soluciones**y se abre en el diseñador.  
  
## <a name="design-the-lookupbox-control"></a>Diseñar el control LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Para diseñar el control LookupBox  
  
-   Arrastre un <xref:System.Windows.Forms.ComboBox> desde el **cuadro de herramientas** hasta la superficie de diseño del control de usuario.  
  
## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido  
 Para controles de búsqueda que admiten el enlace de datos, puede implementar <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Para implementar el atributo LookupBindingProperties  
  
1.  Cambiar el **LookupBox** control a la vista código. (En el **vista** menú, elija **código**.)  
  
2.  Reemplace el código de `LookupBox` por lo siguiente:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  En el menú **Compilar** , elija **Compilar solución**.  
  
## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 Este paso crea un origen de datos utilizando el **configuración origen de datos**asistente, según la `Customers` y `Orders` tablas en la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [bases de datos de ejemplo de instalación de SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **configuración origen de datos** asistente.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En el **elegir la conexión de datos** realice página uno de los siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.  
  
6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página, haga clic en **siguiente**.  
  
7.  En el **elija los objetos de base de datos** , expanda el **tablas** nodo.  
  
8.  Seleccione el `Customers` y `Orders` tablas y, a continuación, haga clic en **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y el `Customers` y `Orders` tablas aparecen en la **orígenes de datos** ventana.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Establezca la columna CustomerID de la tabla Orders para utilizar el control LookupBox  
 Dentro de la **orígenes de datos** ventana, puede establecer el control que se creará antes de arrastrar elementos al formulario.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Para establecer la columna CustomerID para enlazarse al control LookupBox  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el **clientes** nodo en el **orígenes de datos** ventana.  
  
3.  Expanda el **pedidos** nodo (en el **clientes** nodo debajo el **Fax** columna).  
  
4.  Haga clic en la flecha de lista desplegable el **pedidos** nodo y elija **detalles** desde la lista de control.  
  
5.  Haga clic en la flecha de lista desplegable el **CustomerID** columna (en el **pedidos** nodo) y elija **personalizar**.  
  
6.  Seleccione el **LookupBox** en la lista de **controles asociados** en el **opciones de personalización de la interfaz de usuario de datos** cuadro de diálogo.  
  
7.  Haga clic en **Aceptar**.  
  
8.  Haga clic en la flecha de lista desplegable el **CustomerID** columna y elija **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear controles enlazados en el Windows Form  
  
-   Arrastre el **pedidos** nodo desde el **orígenes de datos** ventana hasta el formulario de Windows y compruebe que la **LookupBox** control se usa para mostrar los datos en el `CustomerID` columna.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Enlazar el control para buscar CompanyName desde la tabla Customers  
  
#### <a name="to-setup-the-lookup-bindings"></a>Para configurar los enlaces de búsqueda  
  
-   Seleccione el método main **clientes** nodo en el **orígenes de datos** ventana y arrastre en el cuadro combinado del cuadro de la **CustomerIDLookupBox** en **Form1** .  
  
     Esto configura el enlace de datos para mostrar el `CompanyName` desde el `Customers` tabla manteniendo el `CustomerID` valor desde el `Orders` tabla.  
  
## <a name="running-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
-   Navegue por algunos registros y compruebe que la `CompanyName` aparece en el `LookupBox` control.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

