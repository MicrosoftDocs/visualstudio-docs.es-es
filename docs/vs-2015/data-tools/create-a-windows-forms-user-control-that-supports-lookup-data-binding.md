---
title: Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 7c0514d29d3c8e87b277115f8e1307dc0a5fb0c4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662717"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando muestra datos en formularios Windows Forms, puede elegir controles existentes en el **Cuadro de herramientas** o puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> pueden contener tres propiedades que se pueden enlazar a los datos. Tales controles son similares a <xref:System.Windows.Forms.ComboBox>.  
  
 Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Al crear controles para usarlos en escenarios de enlace de datos, es necesario implementar uno de los atributos de enlace de datos siguientes:  
  
|Uso de atributos de enlace de datos|  
|-----------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos pero que también necesiten presentar una única columna o propiedad. (Este proceso se describe en esta página del tutorial.)|  
  
 Este tutorial crea un control de búsqueda que se enlaza a los datos de dos tablas. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind. El control de búsqueda se enlazará al campo `CustomerID` de la tabla `Orders`. Utilizará este valor para buscar `CompanyName` en la tabla `Customers`.  
  
 Durante este tutorial aprenderá a:  
  
-   Cree un nuevo **aplicación Windows**.  
  
-   Agregue un nuevo **Control de usuario** a su proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `LookupBindingProperty`.  
  
-   Crear un conjunto de datos con el **configuración origen de datos** asistente.  
  
-   Establezca la columna **CustomerID** de la tabla **Pedidos** en la ventana **Orígenes de datos** para utilizar el nuevo control.  
  
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
  
     El proyecto **LookupControlWalkthrough** se crea y se agrega al **Explorador de soluciones**.  
  
## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto  
 Este tutorial crea un control de búsqueda a partir de un **Control de usuario**, por lo que debe agregar un elemento **Control de usuario** al proyecto **LookupControlWalkthrough**.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para agregar un control de usuario al proyecto  
  
1.  En el menú **Proyecto**, elija **Agregar control de usuario**.  
  
2.  Tipo `LookupBox` en el **nombre** área y, a continuación, haga clic en **agregar**.  
  
     El control **LookupBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.  
  
## <a name="design-the-lookupbox-control"></a>Diseñar el control LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Para diseñar el control LookupBox  
  
-   Arrastre un control <xref:System.Windows.Forms.ComboBox> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.  
  
## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido  
 Para controles de búsqueda que admiten el enlace de datos, puede implementar <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Para implementar el atributo LookupBindingProperties  
  
1.  Cambie el control **LookupBox** a vista de código. (En el menú **Ver**, elija **Código**.)  
  
2.  Reemplace el código de `LookupBox` por lo siguiente:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  En el menú **Compilar** , elija **Compilar solución**.  
  
## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 En este paso se crea un origen de datos utilizando el **Asistente para configuración de orígenes de datos** basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [bases de datos de ejemplo de instalación de SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione las tablas `Customers` y `Orders` y después haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Establezca la columna CustomerID de la tabla Orders para utilizar el control LookupBox  
 Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Para establecer la columna CustomerID para enlazarse al control LookupBox  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
3.  Expanda el nodo **Orders** (incluido en el nodo **Customers** debajo de la columna **Fax**).  
  
4.  Haga clic en la flecha de lista desplegable en el nodo **Orders** y elija **Detalles** de la lista de control.  
  
5.  Haga clic en la flecha de lista desplegable en la columna **CustomerID** (del nodo **Orders**) y elija **Personalizar**.  
  
6.  Seleccione **LookupBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.  
  
7.  Haga clic en **Aceptar**.  
  
8.  Haga clic en la flecha de lista desplegable en la columna **CustomerID** y elija **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear controles enlazados en el Windows Form  
  
-   Arrastre el **pedidos** nodo desde el **orígenes de datos** ventana hasta el formulario de Windows y compruebe que la **LookupBox** control se usa para mostrar los datos en el `CustomerID` columna.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Enlazar el control para buscar CompanyName desde la tabla Customers  
  
#### <a name="to-setup-the-lookup-bindings"></a>Para configurar los enlaces de búsqueda  
  
-   Seleccione el método main **clientes** nodo en el **orígenes de datos** ventana y arrastre en el cuadro combinado del cuadro de la **CustomerIDLookupBox** en **Form1** .  
  
     Así configura el enlace de datos para mostrar el valor `CompanyName` de la tabla `Customers` a la vez que mantiene el valor `CustomerID` de la tabla `Orders`.  
  
## <a name="running-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
-   Navegue por algunos registros y compruebe que `CompanyName` aparece en el control `LookupBox`.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
