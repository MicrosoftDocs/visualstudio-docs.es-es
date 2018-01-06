---
title: 'Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 59dafe640428059b4c6772f79a23d5f0ccceaac7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint
  Los procedimientos siguientes muestran cómo crear columnas personalizadas de sitio de SharePoint, o *campos*, así como un tipo de contenido que usa las columnas de sitio. También muestra cómo crear una lista que utiliza el nuevo tipo de contenido.  
  
 En este tutorial se incluyen las tareas siguientes:  
  
-   [Crear columnas de sitio personalizadas](#BKMK_CreatingCustSiteCols).  
  
-   [Crear un tipo de contenido personalizado](#BKMK_CreateCustContType).  
  
-   [Crear una lista de](#BKMK_CreateList).  
  
-   [Crear una lista de](#BKMK_CreateList).  
  
-   [Probar la aplicación](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a>Crear columnas de sitio personalizadas  
 Este ejemplo crea una lista para la administración de pacientes en el hospital. En primer lugar, debe crear un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y agregue columnas de sitio, como se indica a continuación.  
  
#### <a name="to-create-the-project"></a>Para crear el proyecto  
  
1.  En el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **archivo** menú, elija **New**, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, bajo **Visual C#** o **Visual Basic**, expanda la **SharePoint** nodo y, a continuación, elija **2010**.  
  
3.  En el **plantillas** panel, elija **proyecto de SharePoint 2010**, cambie el nombre del proyecto para **Clinic**y, a continuación, elija la **Aceptar** botón.  
  
     La plantilla de proyecto de SharePoint 2010 es un proyecto vacío que se utiliza en este ejemplo para que contenga columnas de sitio y otros elementos de proyecto que se agreguen más tarde.  
  
4.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, escriba la dirección URL para el sitio de SharePoint local a la que desea agregar el nuevo elemento de campo personalizado o utilice la ubicación predeterminada (`http://<`*SystemName* `>/)`.  
  
5.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, utilice el valor predeterminado **implementar como una solución en espacio aislado**.  
  
     Para obtener más información acerca de espacio aislado y soluciones de granja, vea [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Elija la **finalizar** botón. El proyecto debe aparecer ahora en **el Explorador de soluciones**.  
  
#### <a name="to-add-site-columns"></a>Para agregar columnas de sitio  
  
1.  Agregar una nueva columna de sitio. Para ello, en **el Explorador de soluciones**, abra el menú contextual para **Clinic**y, a continuación, elija **agregar**, **nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** diálogo cuadro, elija **columna de sitio**, cambie el nombre a **Patient Name**y, a continuación, elija la **agregar** botón.  
  
3.  En el archivo Elements.xml de la columna de sitio, deje el **tipo** establecer como **texto**y cambie el **grupo** si se establece en **columnas de sitio Clinic**. Cuando haya finalizado, archivo Elements.xml de la columna de sitio debe ser similar al ejemplo siguiente.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Con el mismo procedimiento, agregue dos columnas de sitio más al proyecto: **ID de paciente** (tipo = "Integer") y **nombre médico** (tipo = "Text"). Establezca su valor de grupo en **columnas de sitio Clinic**.  
  
##  <a name="BKMK_CreateCustContType"></a>Crear un tipo de contenido personalizado  
 A continuación, cree un tipo de contenido, en función del tipo de contenido de contactos, que incluye las columnas de sitio que creó en el procedimiento anterior. A partir de un tipo de contenido en un tipo de contenido existente, puede ahorrar tiempo porque el tipo de contenido base proporciona varias columnas de sitio para su uso en el nuevo tipo de contenido.  
  
#### <a name="to-create-a-custom-content-type"></a>Para crear un tipo de contenido personalizado  
  
1.  Agregar un tipo de contenido al proyecto. Para ello, en **el Explorador de soluciones**, elija el nodo de proyecto  
  
2.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
3.  Bajo **Visual C#** o **Visual Basic**, expanda la **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En el **plantillas** panel, elija la **tipo de contenido** plantilla, cambie el nombre a **Info de paciente**y, a continuación, elija la **agregar** botón.  
  
     El **Asistente para personalización de SharePoint** se abre.  
  
5.  En el **qué tipo de contenido base debe heredarse de este tipo de contenido de** elija **póngase en contacto con** como el tipo de contenido en el que desea basar el nuevo tipo de contenido y, a continuación, elija la **finalizar**botón.  
  
     Esto le da acceso a otras columnas de sitio posiblemente útil en el tipo de contenido de contacto, además de las columnas de sitio que definió anteriormente.  
  
6.  El tipo de contenido aparezca el diseñador, en la **columnas** ficha, agregue los tres columnas que ha definido anteriormente del sitio: **Patient Name**, **ID de paciente**y **Nombre médico**. Para agregar estas columnas, elija el primer cuadro de lista en la lista de columnas de sitio en **nombre para mostrar**y, a continuación, elija las columnas de sitio en la lista de uno a la vez.  
  
    > [!TIP]  
    >  Para elegir las columnas de sitio más rápidamente, filtrar la lista, escriba las primeras letras del nombre de la columna.  
  
7.  Además de las tres columnas de sitio personalizado, agregue el **comentarios** columna de sitio en la lista de columnas de sitio.  
  
8.  Seleccione el **requiere** casilla de verificación de la **Patient Name** y **ID de paciente** campos de columnas de sitio para que sean necesarios.  
  
9. En el **Content Type** ficha, asegúrese de que el nombre de tipo de contenido es **Info de paciente**y, a continuación, cambie la descripción a **tarjeta de información de los pacientes**.  
  
10. Cambio **nombre del grupo de** a **tipos de contenido de la clínica**y deje los otros valores en sus valores predeterminados.  
  
11. En la barra de menús, elija **archivo**, **guardar todo**y, a continuación, cierre el Diseñador de tipo de contenido.  
  
##  <a name="BKMK_CreateList"></a>Creación de una lista  
 Ahora, cree una lista que usa las nuevas columnas de sitio y el tipo de contenido.  
  
#### <a name="to-create-a-list"></a>Para crear una lista  
  
1.  Agregar una lista al proyecto. Para ello, en **el Explorador de soluciones**, elija el nodo del proyecto.  
  
2.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
3.  Bajo **Visual C#** o **Visual Basic**, expanda la **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En el **plantillas** panel, elija la **lista** plantilla, cambie el nombre a **pacientes**y, a continuación, elija la **agregar** botón.  
  
5.  Deje el **personalizar la lista en función de** establecer como **predeterminado (en blanco)**y, a continuación, elija la **finalizar** botón.  
  
6.  En el Diseñador de la lista, elija la **tipos de contenido** botón para mostrar el **configuración del tipo de contenido** cuadro de diálogo.  
  
7.  Elija la nueva fila, elija la **Info de paciente** de contenido de tipo en la lista de tipos de contenido y, a continuación, elija la **Aceptar** botón.  
  
     Esto agrega todas las columnas de sitio desde la **Info de paciente** tipo en la lista de contenido.  
  
8.  Eliminar todas las columnas de sitio en la lista excepto los siguientes:  
  
    -   Id. de pacientes  
  
    -   Nombre del paciente  
  
    -   Teléfono particular  
  
    -   Correo electrónico  
  
    -   Nombre médico  
  
    -   Comentarios  
  
9. En **nombre para mostrar columna**, elija una fila vacía, agregar una columna de la lista personalizada y asígnele el nombre **Hospital**. Deje el tipo de datos como **única línea de texto**.  
  
     La columna de la lista personalizada sólo se aplica a esta lista. Cuando se agrega una columna de la lista personalizada a una lista, se crea un nuevo tipo de contenido de lista, que incluye todas las columnas que se agregan a la lista y se establece como la lista predeterminada.  
  
    > [!TIP]  
    >  Si elige una columna de la lista de columnas de sitio, se utiliza una columna de sitio existente. Sin embargo, si escribe un valor de nombre de columna sin elegir las columnas en la lista, se crea una columna de la lista personalizada, incluso si ya existe una columna con el mismo nombre en la lista.  
  
     Si lo desea, en lugar de establecer el tipo de datos de la columna de la lista personalizada para **única línea de texto**, en su lugar podría establecer el tipo de datos para esta columna a la búsqueda y sus valores se pueden recuperar desde una tabla u otra lista. Para obtener información acerca de las columnas de búsqueda, vea [relaciones de lista en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) y [búsquedas y las relaciones de lista](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Junto a la **ID de paciente** y **Patient Name** cuadros, seleccionados la **necesario** casilla de verificación.  
  
11. En el **vistas** ficha, elija una fila vacía para crear una vista. Escriba **los detalles del paciente**.  
  
     En el **vistas** ficha, puede especificar las columnas que desea que aparezca en la lista de SharePoint.  
  
12. Elija la nueva **detalles del paciente** fila y, a continuación, elija la **Predeterminar** botón.  
  
     La nueva vista ahora es la vista predeterminada de la lista.  
  
13. Agregue las columnas siguientes a la **columnas seleccionadas** lista en el orden siguiente:  
  
    -   Id. de pacientes  
  
    -   Nombre del paciente  
  
    -   Teléfono particular  
  
    -   Correo electrónico  
  
    -   Nombre médico  
  
    -   Hospital  
  
    -   Comentarios  
  
14. En el **propiedades** lista, elija la **ordenar y agrupar** propiedad y, a continuación, elija el botón de puntos suspensivos ![icono puntos suspensivos](../sharepoint/media/ellipsisicon.gif "el icono de puntos suspensivos")para mostrar la **ordenar y agrupar** cuadro de diálogo.  
  
15. En el **nombre de la columna** elija **Patient Name**, asegúrese de que el **ordenar** columna se establece en **ascendente**y, a continuación, elija la  **Aceptar** botón.  
  
##  <a name="BKMK_TestApp"></a>Probar la aplicación  
 Ahora que las columnas de sitio personalizadas, el tipo de contenido y la lista están listos, implementarlas en SharePoint y ejecutar la aplicación para probarla.  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  En la barra de menús, pulse **Archivo**, **Guardar todo**.  
  
2.  Presione la tecla F5 para ejecutar la aplicación.  
  
     Se compila la aplicación y, a continuación, se implementan en SharePoint y activar sus características.  
  
3.  En la barra de navegación rápida, elija la **pacientes** vínculo para mostrar la **pacientes** lista.  
  
     Los nombres de columna en la lista deben coincidir con la que ha especificado en el **vistas** ficha [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Elija la **Agregar nuevo elemento** vínculo para crear una tarjeta de información de los pacientes.  
  
5.  Escriba información en los campos y, a continuación, elija la **guardar** botón.  
  
     El nuevo registro aparece en la lista.  
  
## <a name="see-also"></a>Vea también  
 [Crear listas, tipos de contenido y columnas de sitio para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Cómo: crear un tipo de campo personalizado](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Tipos de contenido](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Columnas](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  