---
title: 'Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint | Documentos de Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: dee5d1ec207f2b7bec030076797720fe9e8216ed
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59504268"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint
  Los procedimientos siguientes muestran cómo crear columnas de sitio de SharePoint personalizadas, o *campos*, así como un tipo de contenido que usa las columnas de sitio. También muestra cómo crear una lista que usa el nuevo tipo de contenido.

 En este tutorial se incluyen las tareas siguientes:

- [Crear columnas de sitio personalizadas](#create-custom-site-columns).

- [Crear un tipo de contenido personalizado](#create-a-custom-content-type).

- [Crear una lista](#create-a-list).

- [Probar la aplicación](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

-   Ediciones compatibles de Windows y SharePoint.

-   [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Crear columnas de sitio personalizada
 En este ejemplo se crea una lista para la administración de los pacientes en un hospital. En primer lugar, debe crear un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y agregar columnas de sitio, como se indica a continuación.

#### <a name="to-create-the-project"></a>Para crear el proyecto

1.  En el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **archivo** menú, elija **New** > **proyecto**.

2.  En el **nuevo proyecto** cuadro de diálogo, bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija **2010**.

3.  En el **plantillas** panel, elija **proyecto de SharePoint 2010**, cambie el nombre del proyecto a **Clinic**y, a continuación, elija el **Aceptar** botón.

     La plantilla de proyecto de SharePoint 2010 es un proyecto vacío que se usa en este ejemplo para contener las columnas de sitio y otros elementos de proyecto que se agreguen posteriormente.

4.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, escriba la dirección URL para el sitio de SharePoint local a la que desea agregar el nuevo elemento de campo personalizado o usar la ubicación predeterminada (`http://<`*SystemName* `>/)`.

5.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, use el valor predeterminado **implementar como solución en espacio aislado**.

     Para obtener más información acerca de espacio aislado y soluciones de granja, vea [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

6.  Elija la **finalizar** botón. El proyecto aparece ahora en **el Explorador de soluciones**.

#### <a name="to-add-site-columns"></a>Para agregar columnas de sitio

1.  Agregar una nueva columna de sitio. Para ello, en **el Explorador de soluciones**, abra el menú contextual para **Clinic**y, a continuación, elija **agregar** > **nuevo elemento**.

2.  En el **Agregar nuevo elemento** diálogo cuadro, elija **columna de sitio**, cambie el nombre a **nombre paciente**y, a continuación, elija el **agregar** botón.

3.  En la columna de sitio *Elements.xml* de archivos, deje el **tipo** establecer como **texto**y cambie el **grupo** si se establece en  **Columnas de sitio Clinic**. Cuando haya terminado, la columna de sitio *Elements.xml* archivo debe ser similar al ejemplo siguiente.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="Clinic - Patient Name"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

4.  Con el mismo procedimiento, agregue dos columnas de sitio más al proyecto: **Id. de pacientes** (tipo = "Integer") y **nombre médico** (tipo = "Text"). Establezca su valor de grupo en **columnas de sitio Clinic**.

## <a name="create-a-custom-content-type"></a>Crear un tipo de contenido personalizado
 A continuación, cree un tipo de contenido, según el tipo de contenido de contactos, que incluye las columnas de sitio que creó en el procedimiento anterior. A partir de un tipo de contenido en un tipo de contenido existente, puede ahorrar tiempo porque el tipo de contenido base proporciona varias columnas de sitio para su uso en el nuevo tipo de contenido.

#### <a name="to-create-a-custom-content-type"></a>Para crear un tipo de contenido personalizado

1.  Agregar un tipo de contenido al proyecto. Para ello, en **el Explorador de soluciones**, elija el nodo del proyecto

2.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3.  Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.

4.  En el **plantillas** panel, elija el **tipo de contenido** plantilla, cambie el nombre a **información del paciente**y, a continuación, elija el **agregar** botón.

     El **Asistente de personalización de SharePoint** se abre.

5.  En el **qué tipo de contenido base debe heredar este tipo de contenido de** elija **póngase en contacto con** como el tipo de contenido en el que se va a basar el nuevo tipo de contenido y, a continuación, elija el **finalizar**botón.

     Esto proporciona acceso a otras columnas de sitio potencialmente útiles en el tipo de contenido de contacto, además de las columnas de sitio que definió anteriormente.

6.  Después el tipo de contenido aparezca el diseñador, en el **columnas** pestaña, agregue las tres columnas que ha definido anteriormente del sitio: **Nombre del paciente**, **Id. de pacientes**, y **nombre médico**. Para agregar estas columnas, elija el primer cuadro de lista en la lista de columnas de sitio en **nombre para mostrar**y, a continuación, elija cada columna de sitio en la lista de uno a la vez.

    > [!TIP]
    >  Para elegir las columnas de sitio más rápidamente, filtrar la lista escribiendo las primeras letras del nombre de la columna.

7.  Además de las tres columnas de sitio personalizada, agregue el **comentarios** columna de sitio en la lista de columnas de sitio.

8.  Seleccione el **requiere** casilla de verificación de la **nombre paciente** y **identificador de paciente** columnas de sitio para que sean campos obligatorios.

9. En el **Content Type** pestaña, asegúrese de que el nombre de tipo de contenido es **información del paciente**y, a continuación, cambie la descripción a **tarjeta de información del paciente**.

10. Cambio **nombre del grupo** a **tipos de contenido Clinic**y deje los restantes valores con sus valores predeterminados.

11. En la barra de menús, elija **archivo** > **guardar todo**y, a continuación, cierre el Diseñador de tipo de contenido.

## <a name="create-a-list"></a>Crear una lista
 Ahora, cree una lista que usa las nuevas columnas de sitio y el tipo de contenido.

#### <a name="to-create-a-list"></a>Para crear una lista

1.  Agregar una lista al proyecto. Para ello, en **el Explorador de soluciones**, elija el nodo del proyecto.

2.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3.  Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.

4.  En el **plantillas** panel, elija el **lista** plantilla, cambie el nombre a **pacientes**y, a continuación, elija el **agregar** botón.

5.  Deje el **personalizar la lista según** establecer como **predeterminado (en blanco)** y, a continuación, elija el **finalizar** botón.

6.  En el Diseñador de la lista, elija el **tipos de contenido** botón para mostrar el **configuración del tipo de contenido** cuadro de diálogo.

7.  Elija la nueva fila, elija el **información del paciente** de contenido de tipo en la lista de tipos de contenido y, a continuación, elija el **Aceptar** botón.

     Esto permite agregar todas las columnas de sitio desde la **información del paciente** tipo en la lista de contenido.

8.  Eliminar todas las columnas de sitio en la lista, excepto los siguientes:

    -   Id. de pacientes

    -   Nombre del paciente

    -   Teléfono particular

    -   Correo electrónico

    -   Nombre del médico

    -   Comentarios

9. En **nombre para mostrar columna**, elija una fila vacía, agregue una columna de lista personalizada y asígnele el nombre **Hospital**. Deje su tipo de datos como **única línea de texto**.

     La columna de la lista personalizada se aplica solo a esta lista. Cuando se agrega una columna de lista personalizado a una lista, se crea un tipo de contenido de lista nuevo, incluidas todas las columnas agregadas en la lista y se establece como la lista predeterminada.

    > [!TIP]
    >  Si elige una columna de la lista de columnas de sitio, se usa una columna de sitio existente. Sin embargo, si escribe un valor de nombre de columna sin elegir las columnas en la lista, se crea una columna de lista personalizado, incluso si ya existe una columna con el mismo nombre en la lista.

     Si lo desea, en lugar de establecer el tipo de datos de la columna de lista personalizada para **única línea de texto**, en su lugar, se pudo establecer el tipo de datos para esta columna a la búsqueda y sus valores se recuperaría de una tabla u otra lista. Para obtener información acerca de las columnas de búsqueda, vea [relaciones de lista en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) y [búsquedas y las relaciones de la lista](http://go.microsoft.com/fwlink/?LinkID=224995).

10. Junto a la **identificador de paciente** y **nombre paciente** casillas, seleccionadas el **necesario** casilla de verificación.

11. En el **vistas** pestaña, seleccione una fila vacía para crear una vista. Escriba **los detalles del paciente**.

     En el **vistas** ficha, puede especificar las columnas que desea que aparezca en la lista de SharePoint.

12. Seleccione el nuevo **detalles del paciente** fila y, a continuación, elija el **Predeterminar** botón.

     La nueva vista ahora es la vista predeterminada de la lista.

13. Agregue las siguientes columnas a la **columnas seleccionadas** lista en el orden siguiente:

    -   Id. de pacientes

    -   Nombre del paciente

    -   Teléfono particular

    -   Correo electrónico

    -   Nombre del médico

    -   Hospital

    -   Comentarios

14. En el **propiedades** lista, elija el **ordenar y agrupar** propiedad y, a continuación, elija el botón de puntos suspensivos ![icono de puntos suspensivos](../sharepoint/media/ellipsisicon.gif "icono de puntos suspensivos")para mostrar el **ordenar y agrupar** cuadro de diálogo.

15. En el **nombre de columna** lista, elija **nombre paciente**, asegúrese de que el **ordenación** columna está establecida en **ascendente**y, a continuación, elija el  **Aceptar** botón.

## <a name="test-the-application"></a>Probar la aplicación
 Ahora que la lista, tipo de contenido y columnas de sitio personalizadas están listos, implementarlas en SharePoint y ejecute la aplicación para probarla.

#### <a name="to-test-the-application"></a>Para probar la aplicación

1.  En la barra de menús, pulse **Archivo** > **Guardar todo**.

2.  Elija la **F5** clave para ejecutar la aplicación.

     La aplicación se compila y, a continuación, se implementan en SharePoint y se activan sus características.

3.  En la barra de navegación rápida, elija la **pacientes** vínculo para mostrar el **pacientes** lista.

     Los nombres de columna en la lista deben coincidir con los que escribió en el **vistas** pestaña [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

4.  Elija la **Agregar nuevo elemento** vínculo para crear una tarjeta de información del paciente.

5.  Escriba información en los campos y, a continuación, elija el **guardar** botón.

     El nuevo registro aparece en la lista.

## <a name="see-also"></a>Vea también
- [Crear listas, tipos de contenido y columnas de sitio para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Cómo: Crear un tipo de campo personalizado](http://go.microsoft.com/fwlink/?LinkId=192079)
- [Tipos de contenido](http://go.microsoft.com/fwlink/?LinkId=192080)
- [Columnas](http://go.microsoft.com/fwlink/?LinkId=192081)
