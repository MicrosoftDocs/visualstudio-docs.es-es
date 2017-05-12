---
title: "Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.ListDesigner.GeneralMessageHelp"
  - "Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping"
  - "VS.SharePointTools.ListDesigner.SortingGrouping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, tipos de contenido"
  - "desarrollo de SharePoint en Visual Studio, campos"
  - "desarrollo de SharePoint en Visual Studio, definiciones de lista"
  - "desarrollo de SharePoint en Visual Studio, instancias de lista"
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint
  Los procedimientos siguientes muestran cómo crear el sitio de SharePoint personalizado columna\- o *campo\- como*así como tipo de contenido que usa las columnas de sitio.  También muestra cómo crear una lista que utilice el nuevo tipo de contenido.  
  
 En este tutorial se incluyen las tareas siguientes:  
  
-   [Crear columnas de sitio personalizadas](#BKMK_CreatingCustSiteCols).  
  
-   [Crear un tipo de contenido personalizado](#BKMK_CreateCustContType).  
  
-   [Crear una lista](#BKMK_CreateList).  
  
-   [Crear una lista](#BKMK_CreateList).  
  
-   [Probar la aplicación](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Crear columnas de sitio personalizadas  
 Este ejemplo crea una lista para administrar pacientes en un hospital.  Primero, debe crear un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y agregar columnas de sitio a, como sigue.  
  
#### Para crear el proyecto  
  
1.  En el menú de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**archivo** , elija **new**, **Project**.  
  
2.  En el cuadro de diálogo de **Nuevo proyecto** , en **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación **2010**.  
  
3.  En el panel de **Plantillas** , elija **SharePoint 2010 Project**, cambie el nombre del proyecto a la sesión, y después elija el botón de **Aceptar** .  
  
     La plantilla de proyecto de SharePoint 2010 es un proyecto vacío que se utiliza en este ejemplo para contener columnas de sitio y otros elementos que se agregan más adelante.  
  
4.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL del sitio de SharePoint local al que desea agregar el nuevo elemento de campo personalizado, o utilice la ubicación predeterminada \(`http://<`*SystemName*`>/)`.  
  
5.  En la sección **¿Cuál es el nivel de confianza de esta solución de SharePoint?**, use el valor predeterminado **Implementar como solución en espacio aislado**.  
  
     Para obtener más información sobre las soluciones de espacio aislado y granja de servidores, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Elija el botón **Finalizar**.  El proyecto debe ahora aparecen en **Explorador de soluciones**.  
  
#### Para agregar columnas de sitio  
  
1.  Agregue una nueva columna de sitio.  Para ello, en **Explorador de soluciones**, abra el menú contextual para **Sesión**y, a continuación **Add**, **Nuevo elemento**.  
  
2.  En el cuadro de diálogo de **Agregar nuevo elemento** , elija **Columna de sitio**, cambie el nombre por nombre de Patient, y elija el botón de **Add** .  
  
3.  En el archivo Elements.xml de la columna de sitio, deje **Tipo** que establece como **Texto**, y cambie **Agrupar** a las columnas del sitio de la sesión.  Cuando termina, el archivo Elements.xml de la columna de sitio debe tener el aspecto siguiente.  
  
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
  
4.  Utilizando el mismo procedimiento, agregue dos columnas más del sitio al proyecto: Identificador paciente \(tipo \= “entero”\) y Doctor Name \(tipo \= “text”\).  Establezca el valor de grupo a las columnas del sitio de la sesión.  
  
##  <a name="BKMK_CreateCustContType"></a> Crear un tipo de contenido personalizado  
 A continuación, cree un contenido tipo\- basado en el contenido de los contactos tipo\- que incluye columnas de sitio que creó en el procedimiento anterior.  Basar un tipo de contenido en un tipo de contenido existente, puede ahorrar tiempo porque el tipo de contenido base proporciona varias columnas de sitio para el uso en el nuevo tipo de contenido.  
  
#### Para crear un tipo de contenido personalizado  
  
1.  Agregue un tipo de contenido al proyecto.  Para ello, en **Explorador de soluciones**, elija el nodo del proyecto  
  
2.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
3.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
4.  En el panel de **Plantillas** , elija la plantilla de **Tipo de contenido** , cambie el nombre a la información de Patient, y elija el botón de **Add** .  
  
     **Asistente para la personalización de SharePoint** Abra.  
  
5.  En la lista de **El tipo de contenido base este tipo de contenido heredar** , elija **Contacto** como el tipo de contenido en el que basar el nuevo tipo de contenido, y elegir el botón de **Finalizar** .  
  
     Esto le da acceso a otras columnas potencialmente útiles del sitio en el tipo de contenido del contacto, además de las columnas de sitio que definió anteriormente.  
  
6.  Después de que el diseñador del tipo de contenido aparezca, en la pestaña de **Columnas** , agregue las tres columnas de sitio que definió anteriormente: **Nombre paciente**, **Identificador paciente**, y **Doctor Name**.  Para agregar estas columnas, elija el primer cuadro de lista de columnas de sitio enumeradas bajo **Mostrar nombre**, y después elija en cada columna de sitio en la lista de uno en uno.  
  
    > [!TIP]  
    >  Elegir las columnas de sitio más rápidamente, filtrar la lista escribiendo las primeras letras del nombre de la columna.  
  
7.  Además de las tres columnas personalizadas de sitio, agregue la columna de sitio **COMENTARIOS** de la lista de columnas de sitio.  
  
8.  Active la casilla de **Requerido** para que las columnas de sitio de **Nombre paciente** y de **Identificador paciente** se crean campos obligatorios.  
  
9. En la pestaña de **Tipo de contenido** , asegúrese de que el tipo de contenido es **Información paciente**, y después cambie la descripción a la tarjeta de información de Patient.  
  
10. Cambie **Nombre de grupo** a los tipos de contenido de la sesión, y deje los otros valores en sus valores predeterminados.  
  
11. En la barra de menú, elija **archivo**, **guardar todo**, y luego cierre el diseñador del tipo de contenido.  
  
##  <a name="BKMK_CreateList"></a> Crear una lista  
 Ahora, cree una lista que utilice las nuevas columnas de tipo de contenido y de sitio.  
  
#### Para crear una lista  
  
1.  Agregue una lista al proyecto.  Para ello, en **Explorador de soluciones**, elija el nodo del proyecto.  
  
2.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
3.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
4.  En el panel de **Plantillas** , elija la plantilla de **list** , cambie el nombre a Patients, y elija el botón de **Add** .  
  
5.  Deje **Personalizar la lista basada en** que establece como **Establezca como valor predeterminado \(en blanco\)**, y elija el botón de **Finalizar** .  
  
6.  En la lista Designer, elija el botón de **Tipos de contenido** para mostrar el cuadro de diálogo de **Configuración de tipo de contenido** .  
  
7.  Elija la nueva fila, elija el tipo de contenido de **Información paciente** en la lista de tipos de contenido, y elija el botón de **Aceptar** .  
  
     Esto agrega todas las columnas de sitio de tipo de contenido de **Información paciente** en la lista.  
  
8.  Elimine todas las columnas de sitio de la lista salvo el siguiente:  
  
    -   Identificador paciente  
  
    -   Nombre paciente  
  
    -   Teléfono doméstico  
  
    -   Correo electrónico  
  
    -   Doctor Name  
  
    -   Comentarios  
  
9. En **Nombre para mostrar de la columna**, elija una fila vacía, agregue una columna de la lista personalizada, y denomínela Hospital.  Deje su tipo de datos como **Una sola línea de texto**.  
  
     La columna de la lista personalizada solo se aplica a esta lista.  Cuando se agrega una personalizada muestra la columna en una lista, un nuevo tipo de contenido de la lista, incluidas todas las columnas agregadas en la lista, se crea y se establece como predeterminados de la lista.  
  
    > [!TIP]  
    >  Si elige una columna de la lista de columnas de sitio, se usa una columna existente del sitio.  Sin embargo, si escribe un valor de nombre de columna sin elegir ninguna columna en la lista, se crea una columna de la lista personalizada, aunque una columna con el mismo nombre ya existe en la lista.  
  
     Opcionalmente, en lugar de establecer el tipo de datos para custom muestra la columna a **Una sola línea de texto**, podría en lugar de establecer el tipo de datos de esta columna para buscar, y los valores se recuperan de una tabla u otra lista.  Para obtener información sobre columnas de búsqueda, vea [Lista Relaciones de SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) y [Búsquedas y Relaciones enumerado](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Junto a los cuadros de **Identificador paciente** y de **Nombre paciente** , active la casilla de **Requerido** .  
  
11. En la pestaña de **Vistas** , elija una fila vacía para crear una vista.  Escriba los detalles pacientes.  
  
     En la pestaña de **Vistas** , puede especificar las columnas que desea que aparezca en la lista de SharePoint.  
  
12. Elija la nueva fila de **Detalles pacientes** , y elija el botón de **Predeterminado** .  
  
     La nueva vista ahora es la vista predeterminada de la lista.  
  
13. Agregue las columnas siguientes a la lista de **Columnas seleccionadas** en el orden siguiente:  
  
    -   Identificador paciente  
  
    -   Nombre paciente  
  
    -   Teléfono doméstico  
  
    -   Correo electrónico  
  
    -   Doctor Name  
  
    -   Hospital  
  
    -   Comentarios  
  
14. En la lista de **Propiedades** , elija la propiedad de **Ordenar y agrupar** , y elija los puntos suspensivos ![Icono Puntos suspensivos](../sharepoint/media/ellipsisicon.png "Icono Puntos suspensivos") para mostrar el cuadro de diálogo de **Ordenar y agrupar** .  
  
15. En la lista de **Nombre de columna** , elija **Nombre paciente**, asegúrese de que la columna de **Ordenar** está establecida en **Ascendente**, y después elija el botón de **Aceptar** .  
  
##  <a name="BKMK_TestApp"></a> Probar la aplicación  
 Ahora que las columnas, el tipo de contenido, y la lista personalizados de sitio están listos, implementelas en SharePoint, y ejecute la aplicación para probarlo.  
  
#### Para probar la aplicación  
  
1.  En la barra de menús, elija **Archivo**, **Guardar todo**.  
  
2.  Elija la tecla F5 para ejecutar la aplicación.  
  
     Se compila la aplicación, y después sus características se implementan en SharePoint y se generan.  
  
3.  En la barra de navegación rápida, elija el vínculo de **Pacientes** para mostrar la lista de **Pacientes** .  
  
     Los nombres de columna en la lista deben coincidir con los que escribió en la pestaña de **Vistas** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Elija el vínculo de **Agregar nuevo elemento** para crear una tarjeta de información paciente.  
  
5.  Escriba información en los campos, y elija el botón de **Guardar** .  
  
     El nuevo registro aparece en la lista.  
  
## Vea también  
 [Crear listas, tipos de contenido y columnas de sitio para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Cómo: Cree un tipo de campo personalizado](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Tipos de contenido](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Columnas](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  