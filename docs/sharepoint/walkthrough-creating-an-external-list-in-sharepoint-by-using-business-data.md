---
title: Crear una lista externa en SharePoint con datos económicos
description: Cree un modelo para el servicio BDC que devuelva información sobre los contactos en una base de datos empresarial y, después, cree una lista externa en SharePoint con este modelo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbf996a2d44f94e4571a332fa7a86d861d820d45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847718"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Tutorial: crear una lista externa en SharePoint con datos económicos

El servicio de conectividad a datos profesionales (BDC) permite a SharePoint mostrar los datos empresariales de las aplicaciones de servidor back-end, los servicios web y las bases de datos.

En este tutorial se muestra cómo crear un modelo para el servicio BDC que devuelve información sobre los contactos en una base de datos de ejemplo. A continuación, creará una lista externa en SharePoint mediante este modelo.

En este tutorial se muestran las tareas siguientes:

- Crear un proyecto.
- Agregar una entidad al modelo.
- Agregar un método Finder.
- Agregar un método Finder específico.
- Prueba del proyecto.

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint.

- Acceso a la base de datos de ejemplo AdventureWorks. Para obtener más información acerca de cómo instalar la base de datos AdventureWorks, vea [SQL Server bases](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)de datos de ejemplo.

## <a name="create-a-project-that-contains-a-bdc-model"></a>Crear un proyecto que contenga un modelo BDC

1. En la barra de menús de Visual Studio, elija **archivo**  >  **nuevo**  >  **proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

2. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el elemento **2010** .

3. En el panel **plantillas** , elija **proyecto de SharePoint 2010**, asigne al proyecto el nombre **AdventureWorksTest** y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** . En este asistente, puede especificar el sitio que va a usar para depurar el proyecto y establecer el nivel de confianza de la solución.

4. Elija el botón de opción **implementar como solución de granja de servidores** para establecer el nivel de confianza.

5. Elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.

6. En **Explorador de soluciones**, elija el nodo de proyecto de SharePoint.

7. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

8. En el panel **plantillas** , elija **modelo de conectividad a datos profesionales (solo solución de granja de servidores)**, asigne al proyecto el nombre **AdventureWorksContacts** y, a continuación, elija el botón **Agregar** .

## <a name="add-data-access-classes-to-the-project"></a>Agregar clases de acceso a datos al proyecto

1. En la barra de menús, elija **herramientas**  >  **conectar con base de datos**.

     Se abrirá el cuadro de diálogo **Agregar conexión**.

2. Agregue una conexión a la base de datos de ejemplo AdventureWorks de SQL Server.

     Para obtener más información, vea [Agregar o modificar conexión (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. En el **Explorador de soluciones**, elija el nodo de proyecto.

4. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

5. En el panel **plantillas instaladas** , elija el nodo de **datos** .

6. En el panel **plantillas** , elija **LINQ to SQL clases**.

7. En el cuadro **nombre** , especifique **AdventureWorks** y, a continuación, elija el botón **Agregar** .

     Se agrega un archivo. dbml al proyecto y se abre el Object Relational Designer (Object Relational Designer).

8. En la barra de menús, elija **Ver**  >  **Explorador de servidores**.

9. En **Explorador de servidores**, expanda el nodo que representa la base de datos de ejemplo AdventureWorks y, a continuación, expanda el nodo **tablas** .

10. Agregue la tabla **Contact (person)** en Object Relational Designer.

     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas de la tabla Contact (person).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Quitar la entidad predeterminada del modelo BDC

El proyecto **modelo de conectividad a datos profesionales** agrega una entidad predeterminada denominada Entity1 al modelo. Quite esta entidad. Más adelante, agregará una nueva entidad. Comenzar con un modelo vacío reduce el número de pasos necesarios para completar el tutorial.

1. En **Explorador de soluciones**, expanda el nodo **BdcModel1** y, a continuación, abra el archivo *BdcModel1. bdcm* .

2. El archivo de modelo de conectividad a datos profesionales se abre en el diseñador de BDC.

3. En el diseñador, abra el menú contextual de **Entity1** y, a continuación, elija **eliminar**.

4. En **Explorador de soluciones**, abra el menú contextual de *Entity1. vb* (en Visual Basic) o *Entity1.CS* (en C#) y, a continuación, elija **eliminar**.

5. Abra el menú contextual de *Entity1Service. VB* (en Visual Basic) o *Entity1Service.CS* (en C#) y, a continuación, elija **eliminar**.

## <a name="add-an-entity-to-the-model"></a>Agregar una entidad al modelo

Agregue una entidad al modelo. Puede Agregar entidades desde el **cuadro de herramientas** de Visual Studio al diseñador de BDC.

1. En la barra de menús, elija **Ver**  >  **cuadro de herramientas**.

2. En la pestaña **BusinessDataConnectivity** del **cuadro de herramientas**, agregue una **entidad** al diseñador de BDC.

     La nueva entidad aparece en el diseñador. Visual Studio agrega un archivo denominado *EntityService. VB* (en Visual Basic) o *EntityService.CS* (en C#) al proyecto.

3. En la barra de menús, elija **Ver**  >    >  **ventana** propiedades.

4. En la ventana **propiedades** , establezca el valor de la propiedad **Name** en **Contact**.

5. En el diseñador, abra el menú contextual de la entidad, elija **Agregar** y, a continuación, elija **identificador**.

     Aparece un nuevo identificador en la entidad.

6. En la ventana **propiedades** , cambie el nombre del identificador a **ContactID**.

7. En la lista **nombre de tipo** , elija **System. Int32**.

## <a name="add-a-specific-finder-method"></a>Agregar un método Finder específico

Para permitir que el servicio BDC muestre un contacto específico, debe agregar un método Finder específico. El servicio BDC llama al método de buscador específico cuando un usuario elige un elemento en una lista y, a continuación, elige el botón **Ver elemento** de la cinta de opciones.

Agregue un método Finder específico a la entidad Contact mediante la ventana **detalles del método de BDC** . Para devolver una entidad específica, agregue código al método.

1. En el diseñador de BDC, elija la entidad **contacto** .

2. En la barra de menús, elija **Ver**  >  **otros**  >  **detalles del método BDC** de Windows.

     Se abre la ventana detalles del método de BDC.

3. En la lista **Agregar un método** , elija **crear método de buscador específico**.

     Visual Studio agrega los siguientes elementos al modelo. Estos elementos aparecen en la ventana **detalles del método de BDC** .

    - Un método denominado ReadItem.

    - Parámetro de entrada para el método.

    - Parámetro devuelto para el método.

    - Un descriptor de tipo para cada parámetro.

    - Instancia de método para el método.

4. En la ventana **detalles del método de BDC** , abra la lista que aparece para el descriptor de tipo de **contacto** y, a continuación, elija **Editar**.

     Se abre el **Explorador de BDC** y proporciona una vista jerárquica del modelo.

5. En la ventana **propiedades** , abra la lista situada junto a la propiedad **TypeName** , elija la pestaña **proyecto actual** y, a continuación, elija la propiedad **contacto** .

6. En el **Explorador de BDC**, abra el menú contextual del **contacto** y, a continuación, elija **Agregar descriptor de tipos**.

     Aparece un nuevo descriptor de tipo denominado **TypeDescriptor1** en el **Explorador de BDC**.

7. En la ventana **propiedades** , establezca el valor de la propiedad **nombre** en **ContactID**.

8. Abra la lista situada junto a la propiedad **TypeName** y, a continuación, elija **Int32**.

9. Abra la lista situada junto a la propiedad **identificador** y, a continuación, elija **ContactID**.

10. Repita el paso 6 para crear un descriptor de tipo para cada uno de los campos siguientes.

    |Nombre|Nombre del tipo|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Teléfono|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. En el diseñador de BDC, en la entidad **Contact** , abra el método **ReadItem** .

     El archivo de código de servicio de contacto se abre en el editor de código.

12. En la `ContactService` clase, reemplace el `ReadItem` método por el código siguiente. Este código realiza las tareas siguientes:

    - Recupera un registro de la tabla Contact de la base de datos AdventureWorks.

    - Devuelve una entidad Contact al servicio BDC.

    > [!NOTE]
    > Reemplace el valor del `ServerName` campo por el nombre del servidor.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Agregar un método Finder

Para permitir que el servicio BDC muestre los contactos en una lista, debe agregar un método Finder. Agregue un método Finder a la entidad Contact mediante la ventana **detalles del método de BDC** . Para devolver una colección de entidades al servicio BDC, agregue código al método.

1. En el diseñador de BDC, elija la entidad **contacto** .

2. En la ventana **detalles del método de BDC** , contraiga el nodo **ReadItem** .

3. En la lista **Agregar un método** en el método **ReadList** , elija **crear método de buscador**.

     Visual Studio agrega un método, un parámetro de retorno y un descriptor de tipos.

4. En el diseñador de BDC, en la entidad **Contact** , abra el método **ReadList** .

     El archivo de código para el servicio de contacto se abre en el editor de código.

5. En la `ContactService` clase, reemplace el `ReadList` método por el código siguiente. Este código realiza las tareas siguientes:

   - Recupera datos de la tabla Contacts de la base de datos AdventureWorks.

   - Devuelve una lista de entidades Contact al servicio BDC.

     > [!NOTE]
     > Reemplace el valor del `ServerName` campo por el nombre del servidor.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Prueba del proyecto

Al ejecutar el proyecto, se abre el sitio de SharePoint y Visual Studio agrega el modelo al servicio de conectividad a datos profesionales. Cree una lista externa en SharePoint que haga referencia a la entidad contact. Los datos para contactos en la base de datos AdventureWorks aparecen en la lista.

> [!NOTE]
> Es posible que tenga que modificar la configuración de seguridad en SharePoint antes de poder depurar la solución. Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Elija la tecla **F5**.

     Se abre el sitio de SharePoint.

2. En el menú **acciones del sitio** , elija el comando **más opciones** .

3. En la página **crear** , elija la plantilla **lista externa** y, a continuación, elija el botón **crear** .

4. Asigne a la lista personalizada el nombre **contactos**.

5. Elija el botón examinar situado junto al campo **tipo de contenido externo** .

6. En el cuadro de diálogo **selector de tipos de contenido externo** , elija el elemento **AdventureWorksContacts. BdcModel1. contact** y, a continuación, elija el botón **crear** .

     SharePoint crea una lista externa que contiene contactos de la base de datos de ejemplo AdventureWorks.

7. Para probar el método de buscador específico, elija un contacto en la lista.

8. En la cinta de opciones, elija la pestaña **elementos** y, a continuación, elija el comando **Ver elemento** .

     Los detalles del contacto que ha elegido aparecen en un formulario.

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información sobre cómo diseñar modelos para el servicio BDC en SharePoint en estos temas:

- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md).
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Vea también

[Diseñar un modelo](../sharepoint/designing-a-business-data-connectivity-model.md) 
 de conectividad a datos profesionales [Crear un modelo](../sharepoint/creating-a-business-data-connectivity-model.md) 
 de conectividad a datos profesionales [Introducción a](../sharepoint/bdc-model-design-tools-overview.md) 
 las herramientas de diseño del modelo BDC [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)