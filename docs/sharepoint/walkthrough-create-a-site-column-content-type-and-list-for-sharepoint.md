---
title: Crear columna de sitio, tipo de contenido y lista para SharePoint
titleSuffix: ''
description: En este tutorial, cree una columna de sitio personalizada (campo), un tipo de contenido personalizado que use la columna sitio y una lista que use el tipo de contenido de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1670dfa3c7202e8ebbdb28396f161daeffac491
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914015"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Tutorial: Creación de una columna, un tipo de contenido y una lista de sitios para SharePoint
  Los procedimientos siguientes muestran cómo crear columnas de sitio de SharePoint personalizadas, o *campos*, así como un tipo de contenido que usa las columnas de sitio. También se muestra cómo crear una lista que usa el nuevo tipo de contenido.

 En este tutorial se incluyen las tareas siguientes:

- [Crear columnas de sitio personalizadas](#create-custom-site-columns).

- [Cree un tipo de contenido personalizado](#create-a-custom-content-type).

- [Cree una lista](#create-a-list).

- [Pruebe la aplicación](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Crear columnas de sitio personalizadas
 En este ejemplo se crea una lista para administrar pacientes en un hospital. En primer lugar, debe crear un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y agregarle columnas de sitio, como se indica a continuación.

#### <a name="to-create-the-project"></a>Para crear el proyecto

1. En el menú [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Archivo**, elija **Nuevo** > **Proyecto**.
::: moniker range="=vs-2017"
2. En el cuadro de diálogo **nuevo proyecto** , en **Visual C#** o **Visual Basic**, expanda el nodo **Office/SharePoint** y, a continuación, seleccione **soluciones de SharePoint**.

3. En el panel **plantillas** , elija el **proyecto vacío de SharePoint** para la versión concreta de SharePoint que ha instalado. Por ejemplo, si tiene instalado SharePoint 2016, seleccione la plantilla **de proyecto sharepoint 2016-Empty** .  

4. Cambie el nombre del proyecto a **Clinic** y, a continuación, elija el botón **Aceptar** .

5. En el cuadro de diálogo **especificar el sitio y el nivel de seguridad para la depuración** , escriba la dirección URL del sitio de SharePoint local al que desea agregar el nuevo elemento de campo personalizado o use la ubicación predeterminada ( `http://<` *SystemName* `>/)` .

6. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , use el valor predeterminado **implementar como una solución en espacio aislado**.

     Para obtener más información sobre las soluciones en espacio aislado y las soluciones de granja, consulte [consideraciones sobre soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7. Elija el botón **Finalizar**. El proyecto se muestra ahora en **Explorador de soluciones**.
::: moniker-end
::: moniker range=">=vs-2019"
2.  En el cuadro de diálogo **crear un nuevo proyecto** , seleccione el **proyecto vacío de SharePoint** para la versión concreta de SharePoint que ha instalado. Por ejemplo, si tiene instalado SharePoint 2016, seleccione la plantilla **de proyecto sharepoint 2016-Empty** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Cambie el nombre del proyecto a **Clinic** y, a continuación, elija el botón **crear** .

4. En el cuadro de diálogo **especificar el sitio y el nivel de seguridad para la depuración** , escriba la dirección URL del sitio de SharePoint local al que desea agregar el nuevo elemento de campo personalizado o use la ubicación predeterminada ( `http://<` *SystemName* `>/)` .

5. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , use el valor predeterminado **implementar como una solución en espacio aislado**.

     Para obtener más información sobre las soluciones en espacio aislado y las soluciones de granja, consulte [consideraciones sobre soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

6. Elija el botón **Finalizar**. El proyecto se muestra ahora en **Explorador de soluciones**.
::: moniker-end

#### <a name="to-add-site-columns"></a>Para agregar columnas de sitio

1. Agregue una nueva columna de sitio. Para ello, en **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **Clinic** y, a continuación, elija **Agregar**  >  **nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , elija **columna de sitio**, cambie el nombre a **PatientName** y, a continuación, elija el botón **Agregar** .

3. En el archivo de *Elements.xml* de la columna de sitio, deje la configuración de **tipo** como **texto**, cambie la configuración de **Grupo** a columnas de sitio de la **sesión**. Cuando haya finalizado, el archivo de *Elements.xml* de la columna de sitio debería ser similar al ejemplo siguiente.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > Si usa la grafía Camel en el nombre de la columna de sitio, Visual Studio agregará automáticamente un espacio en la DisplayName.
    > Se recomienda no usar espacios en el nombre de la columna del sitio, ya que puede causar problemas al intentar implementar la solución en SharePoint.

4. Con el mismo procedimiento, agregue dos columnas de sitio más al proyecto: **PatientID** (Type = "integer") y **DoctorName** (Type = "Text"). Establezca su valor de grupo en **columnas de sitio** de la sesión.

## <a name="create-a-custom-content-type"></a>Crear un tipo de contenido personalizado
 A continuación, cree un tipo de contenido, basado en el tipo de contenido contactos, que incluya las columnas del sitio que creó en el procedimiento anterior. Al basar un tipo de contenido en un tipo de contenido existente, puede ahorrar tiempo porque el tipo de contenido base proporciona varias columnas de sitio para su uso en el nuevo tipo de contenido.

#### <a name="to-create-a-custom-content-type"></a>Para crear un tipo de contenido personalizado

1. Agregue un tipo de contenido al proyecto. Para ello, en **Explorador de soluciones**, elija el nodo del proyecto.

2. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En el panel **plantillas** , elija la plantilla **tipo de contenido** , cambie el nombre a información de **paciente** y, a continuación, elija el botón **Agregar** .

     Se abre el **Asistente para la personalización de SharePoint** .

5. En la lista **¿en qué tipo de contenido base debe heredar este tipo de contenido** ?, elija **contacto** como el tipo de contenido en el que se basará el nuevo tipo de contenido y, a continuación, elija el botón **Finalizar** .

     Esto le proporciona acceso a otras columnas de sitio potencialmente útiles en el tipo de contenido de contacto, además de las columnas de sitio que definió anteriormente.

6. Cuando aparezca el diseñador de tipos de contenido, en la pestaña **columnas** , agregue las tres columnas de sitio que definió anteriormente: **patient Name**, **patient ID** y **doctor Name**. Para agregar estas columnas, elija el primer cuadro de lista de la lista columnas de sitio en **nombre para mostrar** y, a continuación, elija cada columna de sitio de la lista de una en una.

    > [!TIP]
    > Para elegir las columnas de sitio más rápidamente, filtre la lista escribiendo las primeras letras del nombre de la columna.

7. Además de las tres columnas del sitio personalizado, agregue la columna **comentarios** del sitio de la lista columnas del sitio.

8. Active la casilla **requerido** para las columnas de sitio **nombre de paciente** e ID. de **paciente** para convertirlos en campos obligatorios.

9. En la pestaña **tipo de contenido** , asegúrese de que el nombre del tipo de contenido es información del **paciente** y, a continuación, cambie la descripción a tarjeta de **información de pacientes**.

10. Cambie el **nombre del grupo** a los tipos de contenido de la **sesión** y deje los valores predeterminados de los demás valores.

11. En la barra de menús, elija **archivo**  >  **guardar todo** y, a continuación, cierre el diseñador de tipos de contenido.

## <a name="create-a-list"></a>Crear una lista
 Ahora, cree una lista que use el nuevo tipo de contenido y las columnas de sitio.

#### <a name="to-create-a-list"></a>Para crear una lista

1. Agregue una lista al proyecto. Para ello, en **Explorador de soluciones**, elija el nodo del proyecto.

2. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** .

4. En el panel **plantillas** , elija la plantilla **lista** , cambie el nombre a **pacientes** y, a continuación, elija el botón **Agregar** .

5. Deje la opción **personalizar la lista según** la configuración **predeterminada (lista personalizada)** y, a continuación, elija el botón **Finalizar** .

6. En el diseñador de listas, elija el botón **tipos de contenido** para mostrar el cuadro de diálogo Configuración de **tipo de contenido** .

7. Elija la nueva fila, elija el tipo de contenido **información de paciente** en la lista de tipos de contenido y, a continuación, elija el botón **Aceptar** .

     Al hacerlo, se agregan a la lista todas las columnas de sitio del tipo de contenido de **información del paciente** .

8. Elimine todas las columnas de sitio de la lista excepto las siguientes:

    - ID. de paciente

    - Nombre del paciente

    - Teléfono particular

    - Correo electrónico

    - Nombre del doctor

    - Comentarios

9. En **nombre para mostrar columna**, elija una fila vacía, agregue una columna de lista personalizada y asígnele el nombre **Hospital**. Deje su tipo de datos como **una sola línea de texto**.

     La columna lista personalizada solo se aplica a esta lista. Cuando se agrega una columna de lista personalizada a una lista, se crea un nuevo tipo de contenido de lista, incluidas todas las columnas agregadas a la lista, y se establece como la lista predeterminada.

    > [!TIP]
    > Si elige una columna de la lista de columnas de sitio, se usa una columna de sitio existente. Sin embargo, si escribe un valor de nombre de columna sin elegir ninguna columna de la lista, se creará una columna de lista personalizada, incluso si ya existe una columna con el mismo nombre en la lista.

     Opcionalmente, en lugar de establecer el tipo de datos de la columna de lista personalizada en **una sola línea de texto**, podría establecer el tipo de datos para esta columna en Lookup y sus valores se recuperarían de una tabla o de otra lista. Para obtener información acerca de las columnas de búsqueda, vea [lista de relaciones en SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) y [búsquedas y listas de relaciones](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. Junto a los cuadros ID. de **paciente** y **nombre del paciente** , active la casilla **requerido** .

11. En la pestaña **vistas** , elija una fila vacía para crear una vista. Escriba los **detalles del paciente** en una fila en blanco en la columna Nombre de **vista** .

     En la pestaña **vistas** , puede especificar las columnas que desea que aparezcan en la lista de SharePoint.

12. Elija la nueva fila de **detalles del paciente** y, a continuación, elija el botón **establecer como predeterminado** .

     La nueva vista es ahora la vista predeterminada de la lista.

13. Agregue las siguientes columnas a la lista **columnas seleccionadas** en el orden siguiente:

    - ID. de paciente

    - Nombre del paciente

    - Teléfono particular

    - Correo electrónico

    - Nombre del doctor

    - Urgencia

    - Comentarios

14. En la lista **propiedades** , elija la propiedad **ordenar y agrupar** y, a continuación, elija el ![icono de puntos suspensivos](../sharepoint/media/ellipsisicon.gif "Icono Puntos suspensivos") del botón de puntos suspensivos para mostrar el cuadro de diálogo **ordenar y agrupar** .

15. En la **lista nombre de columna** , elija **patient Name**, asegúrese de que la columna de **ordenación** esté establecida en **ascendente** y elija el botón **Aceptar** .

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora que las columnas del sitio personalizado, el tipo de contenido y la lista están listos, impleméntela en SharePoint y ejecute la aplicación para probarlo.

#### <a name="to-test-the-application"></a>Para probar la aplicación

1. En la barra de menús, pulse **Archivo** > **Guardar todo**.

2. Elija la tecla **F5** para ejecutar la aplicación.

     La aplicación se compila y, a continuación, sus características se implementan en SharePoint y se activan.

3. En la barra de navegación rápida, elija el vínculo **pacientes** para mostrar la lista **pacientes** .

     Los nombres de columna de la lista deben coincidir con los que especificó en la pestaña **vistas** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. Elija el vínculo **Agregar nuevo elemento** para crear una tarjeta de información de pacientes.

5. Escriba información en los campos y elija el botón **Guardar** .

     El nuevo registro aparece en la lista.

## <a name="see-also"></a>Consulte también
- [Creación de listas, tipos de contenido y columnas de sitio para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Cómo: crear un tipo de campo personalizado](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Tipos de contenido](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Columnas](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
