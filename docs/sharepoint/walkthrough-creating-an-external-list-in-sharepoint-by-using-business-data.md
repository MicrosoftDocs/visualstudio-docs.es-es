---
title: 'Tutorial: Crear una lista externa en SharePoint mediante el uso de los datos empresariales | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d8a557ae7f08afceee49e9e797f18562b548a67c
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119475"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Tutorial: Crear una lista externa en SharePoint con datos profesionales

El servicio de conectividad de datos profesionales (BDC) permite a SharePoint mostrar los datos empresariales de aplicaciones de servidor back-end, servicios Web y bases de datos.

En este tutorial se muestra cómo crear un modelo para el servicio BDC que devuelve información acerca de los contactos de una base de datos de ejemplo. A continuación, creará una lista externa en SharePoint mediante el uso de este modelo.

En este tutorial se muestran las tareas siguientes:

- Creación de un proyecto.
- Agregar una entidad al modelo.
- Agregar un método finder.
- Agregar un método Finder específico.
- Probar el proyecto.

## <a name="prerequisites"></a>Requisitos previos

Necesita los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Acceso a la base de datos de ejemplo AdventureWorks. Para obtener más información sobre cómo instalar la base de datos de AdventureWorks, vea [bases de datos de ejemplo de SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Crear un proyecto que contiene un modelo BDC

1. En la barra de menús de Visual Studio, elija **archivo** > **New** > **proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

2. Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** elemento.

3. En el **plantillas** panel, elija **proyecto de SharePoint 2010**, denomine el proyecto **AdventureWorksTest**y, a continuación, elija el **Aceptar** botón .

     El **Asistente de personalización de SharePoint** aparece. En este asistente, puede especificar el sitio que va a usar para depurar el proyecto y establecer el nivel de confianza de la solución.

4. Elija la **implementar como solución de granja de servidores** botón de opción para establecer el nivel de confianza.

5. Elija la **finalizar** botón para aceptar el sitio local predeterminado de SharePoint.

6. En **el Explorador de soluciones**, elija el nodo de proyecto de SharePoint.

7. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

8. En el **plantillas** panel, elija **(solución de granja de servidores únicamente) modelo de conectividad a datos empresariales**, denomine el proyecto **escriba AdventureWorksContacts**y, a continuación, elija el **Agregar** botón.

## <a name="add-data-access-classes-to-the-project"></a>Agregar clases de acceso a datos al proyecto

1. En la barra de menús, elija **herramientas** > **conectar con base de datos**.

     El **Agregar conexión** abre el cuadro de diálogo.

2. Agregar una conexión a la base de datos de ejemplo AdventureWorks de SQL Server.

     Para obtener más información, consulte [agregar o modificar conexión (Microsoft SQL Server)](http://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. En el **Explorador de soluciones**, elija el nodo de proyecto.

4. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

5. En el **plantillas instaladas** panel, elija el **datos** nodo.

6. En el **plantillas** panel, elija **clases LINQ to SQL**.

7. En el **nombre** , especifique **AdventureWorks**y, a continuación, elija el **agregar** botón.

     Un archivo .dbml se agrega al proyecto y abre el Object Relational Designer (Object Relational Designer).

8. En la barra de menús, elija **vista** > **Explorador de servidores**.

9. En **Explorador de servidores**, expanda el nodo que representa la base de datos de ejemplo AdventureWorks y, a continuación, expanda el **tablas** nodo.

10. Agregar el **contacto (persona)** tabla hasta Object Relational Designer.

     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas de la tabla Contact (Person).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Quitar la entidad predeterminada del modelo BDC

El **modelo de conectividad a datos empresariales** proyecto agrega una entidad de predeterminada denominada Entity1 al modelo. Quite esta entidad. Más adelante, agregará una nueva entidad. A partir de un modelo vacío, reduce el número de pasos necesarios para completar el tutorial.

1. En **el Explorador de soluciones**, expanda el **BdcModel1** nodo y, a continuación, abra el *BdcModel1.bdcm* archivo.

2. Se abre el archivo de modelo de conectividad a datos empresariales en el Diseñador de BDC.

3. En el diseñador, abra el menú contextual de **Entity1**y, a continuación, elija **eliminar**.

4. En **el Explorador de soluciones**, abra el menú contextual para *Entity1.vb* (en Visual Basic) o *Entity1.cs* (en C#) y, a continuación, elija **eliminar** .

5. Abra el menú contextual para *Entity1Service.vb* (en Visual Basic) o *Entity1Service.cs* (en C#) y, a continuación, elija **eliminar**.

## <a name="add-an-entity-to-the-model"></a>Agregar una entidad al modelo

Agregar una entidad al modelo. Puede agregar entidades de Visual Studio **cuadro de herramientas** en el Diseñador de BDC.

1. En la barra de menús, elija **vista** > **cuadro de herramientas**.

2. En el **BusinessDataConnectivity** pestaña de la **cuadro de herramientas**, agregue un **entidad** hasta el diseñador BDC.

     La nueva entidad aparece en el diseñador. Visual Studio agrega un archivo denominado *EntityService.vb* (en Visual Basic) o *EntityService.cs* (en C#) al proyecto.

3. En la barra de menús, elija **vista** > **propiedades** > **ventana**.

4. En el **propiedades** ventana, establezca el **nombre** valor de propiedad **póngase en contacto con**.

5. En el diseñador, abra el menú contextual de la entidad, elija **agregar**y, a continuación, elija **identificador**.

     Un nuevo identificador aparece en la entidad.

6. En el **propiedades** ventana, cambie el nombre del identificador para **ContactID**.

7. En el **nombre de tipo** elija **System.Int32**.

## <a name="add-a-specific-finder-method"></a>Agregar un método Finder específico

Para habilitar el servicio BDC mostrar un contacto específico, debe agregar un método Finder específico. El servicio BDC llama al método de buscador específico cuando un usuario elige un elemento en una lista y, a continuación, elige el **ver elemento** botón en la cinta de opciones.

Agregar un método Finder específico a la entidad Contact mediante el **detalles del método de BDC** ventana. Para devolver una entidad concreta, agregue código al método.

1. En el Diseñador de BDC, elija el **póngase en contacto con** entidad.

2. En la barra de menús, elija **vista** > **Other Windows** > **detalles del método de BDC**.

     Se abre la ventana de detalles del método de BDC.

3. En el **agregue un método** elija **crear método Finder específico**.

     Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la **detalles del método de BDC** ventana.

    - Un método denominado ReadItem.

    - Un parámetro de entrada para el método.

    - Un parámetro de valor devuelto del método.

    - Un descriptor de tipo para cada parámetro.

    - Una instancia de método para el método.

4. En el **detalles del método de BDC** ventana, abra la lista que aparece para la **póngase en contacto con** descriptor de tipo y, a continuación, elija **editar**.

     El **Explorador de BDC** se abre y proporciona una vista jerárquica del modelo.

5. En el **propiedades** ventana, abra la lista junto a la **TypeName** propiedad, elija el **proyecto actual** pestaña y, a continuación, elija el **póngase en contacto con**propiedad.

6. En el **Explorador de BDC**, abra el menú contextual de la **póngase en contacto con**y, a continuación, elija **agregar Descriptor de tipo**.

     Un nuevo descriptor de tipo que se denomina **TypeDescriptor1** aparece en el **Explorador de BDC**.

7. En el **propiedades** ventana, establezca el **nombre** valor de propiedad **ContactID**.

8. Abra la lista junto a la **TypeName** propiedad y, a continuación, elija **Int32**.

9. Abra la lista junto a la **identificador** propiedad y, a continuación, elija **ContactID**.

10. Repita el paso 6 para crear un descriptor de tipo para cada uno de los siguientes campos.

    |nombre|Nombre de tipo|
    |----------|---------------|
    |Nombre|System.String|
    |LastName|System.String|
    |Teléfono|System.String|
    |Dirección de correo electrónico|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. En el diseñador BDC, en la **póngase en contacto con** entidad, abra el **ReadItem** método.

     El archivo de código del servicio de contacto se abre en el Editor de código.

12. En el `ContactService` class, reemplace el `ReadItem` método con el código siguiente. Este código realiza las tareas siguientes:

    - Recupera un registro de la tabla Contact de la base de datos AdventureWorks.

    - Devuelve una entidad Contact al servicio BDC.

    > [!NOTE]
    > Reemplace el valor de la `ServerName` campo con el nombre del servidor.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Agregar un método finder

Para habilitar el servicio BDC mostrar los contactos en una lista, debe agregar un método Finder. Agregar un método Finder a la entidad Contact utilizando la **detalles del método de BDC** ventana. Para devolver una colección de entidades para el servicio BDC, agregue código al método.

1. En el diseñador BDC, elija el **póngase en contacto con** entidad.

2. En el **detalles del método de BDC** ventana, contraer los **ReadItem** nodo.

3. En el **agregue un método** lista bajo el **ReadList** método, elija **crear método Finder**.

     Visual Studio agrega un método, un parámetro de retorno y un descriptor de tipos.

4. En el diseñador BDC, en la **póngase en contacto con** entidad, abra el **ReadList** método.

     El archivo de código para el servicio de contacto se abre en el Editor de código.

5. En el `ContactService` class, reemplace el `ReadList` método con el código siguiente. Este código realiza las tareas siguientes:

    - Recupera datos de la tabla de contactos de la base de datos AdventureWorks.

    - Devuelve una lista de entidades de contacto para el servicio BDC.

    > [!NOTE]
    > Reemplace el valor de la `ServerName` campo con el nombre del servidor.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>El proyecto de prueba

Al ejecutar el proyecto, se abre el sitio de SharePoint y Visual Studio agrega el modelo para el servicio de conectividad a datos empresariales. Crear una lista externa en SharePoint que hace referencia a la entidad Contact. Los datos de contactos en la base de datos AdventureWorks aparecen en la lista.

> [!NOTE]
> Es posible que deba modificar la configuración de seguridad en SharePoint antes de poder depurar la solución. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Elija la tecla **F5**.

     Se abre el sitio de SharePoint.

2. En el **acciones del sitio** menú, elija la **más opciones** comando.

3. En el **crear** página, elija el **lista externa** plantilla y, a continuación, elija el **crear** botón.

4. Nombre de la lista personalizada de **contactos**.

5. Elija el botón Examinar junto a la **tipo de contenido externo** campo.

6. En el **selector de tipos de contenido externo** diálogo cuadro, elija el **AdventureWorksContacts.BdcModel1.Contact** elemento y, a continuación, elija el **crear** botón.

     SharePoint crea una lista externa que contiene los contactos de la base de datos de ejemplo AdventureWorks.

7. Para probar el método de buscador específico, elija un contacto en la lista.

8. En la cinta de opciones, elija la **elementos** pestaña y, a continuación, elija el **ver elemento** comando.

     Los detalles de contacto que eligió aparecen en un formulario.

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información acerca de cómo diseñar modelos para el servicio BDC de SharePoint en los siguientes temas:

- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md).
- [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Vea también

[Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)  
[Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)  
[Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)  
[Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
