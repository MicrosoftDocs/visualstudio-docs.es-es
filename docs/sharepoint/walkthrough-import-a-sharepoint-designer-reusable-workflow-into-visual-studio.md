---
title: "Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio"
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
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Desarrollo de SharePoint en Visual Studio, importar flujos de trabajo reutilizables"
  - "flujos de trabajo reutilizables [desarrollo de SharePoint en Visual Studio]"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio
  En este tutorial se muestra cómo importar un flujo de trabajo reutilizable creado en SharePoint Designer 2010 en un proyecto de flujo de trabajo de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Los flujos de trabajo creados en SharePoint Designer, o *flujos de trabajo declarativos*, están compuestos de instrucciones [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] en lugar de código.  SharePoint Designer 2010 presenta los *flujos de trabajo reutilizables*, que son flujos de trabajo portátiles y declarativos que pueden utilizarse por listas diferentes en sitios de SharePoint.  
  
 Los flujos de trabajo creados en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], como los flujos de trabajo secuenciales y de equipo de estado, se denominan *flujos de trabajo de código*.  Los flujos de trabajo de código están compuestos de archivos XML y módulos de código en los que los usuarios pueden personalizar el comportamiento del flujo de trabajo.  
  
 Visual Studio permite importar flujos de trabajo reutilizables creados en SharePoint Designer 2010 y convertirlos a los flujos de trabajo para el uso en sitios de SharePoint.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear un flujo de trabajo simple y reutilizable en SharePoint Designer.  
  
-   Exportar el flujo de trabajo reutilizable de SharePoint Designer a un archivo .wsp y a SharePoint.  
  
-   Importar el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mediante el proyecto Importar flujo de trabajo reutilizable.  
  
-   Modificar el flujo de trabajo agregando código.  
  
-   Utilizar el flujo de trabajo importado en un sitio de SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## Crear subsitios de SharePoint de destino  
 Primero cree dos nuevos subsitios de SharePoint: uno para hospedar los flujos de trabajo reutilizables de SharePoint Designer, otro para hospedar los flujos de trabajo convertidos.  
  
#### Para crear subsitios de SharePoint  
  
1.  En SharePoint Designer 2010, en la barra de menú, elija **archivo**, **Nuevo sitio Web en blanco**.  
  
2.  En el cuadro de diálogo de **Nuevo sitio Web en blanco** , vaya a un sitio de SharePoint donde desea crear el flujo de trabajo, o utilice el valor http:\/\/*SystemName*\/y después elija el botón de **Aceptar** .  
  
     Aparece la Página principal.  
  
3.  En la sección de **Subsitios** , elija el botón de **new** .  
  
4.  En el cuadro de diálogo de **new** , elija **Plantillas de SharePoint** de la lista del panel izquierdo, y elija **Sitio de grupo** de la lista del panel derecho.  
  
5.  En el cuadro de **Especifique la ubicación del sitio Web** , reemplace la palabra **subsitio** en la dirección URL por SPD1, y elija el botón de **Aceptar** .  
  
     Esto abre el nuevo subsitio en SharePoint Designer.  Cierre esta instancia de SharePoint Designer y vuelva a la primera instancia \(el sitio de nivel superior\).  
  
6.  Repita los pasos 3 a 5 para crear el segundo subsitio, pero esta vez reemplace la palabra **subsitio** en la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] por SPD2.  
  
## Crear un flujo de trabajo reutilizable de SharePoint Designer  
 Dado que SharePoint no incluye todos los flujos de trabajo reutilizables que puede utilizar para este ejemplo, creará uno.  En este flujo de trabajo simple, cuando un usuario escribe una nueva tarea en la lista de tareas que tiene un título concreto, la tarea se asigna a ese usuario.  
  
#### Para crear un flujo de trabajo reutilizable de SharePoint Designer  
  
1.  En la sección de **Subsitios** , elija el sitio de **SPD1** para modificarlo.  
  
2.  En la cinta de opciones, elija el botón de **Flujo de trabajo reutilizable** .  
  
     Aparecerá el asistente para crear flujos de trabajo reutilizables.  
  
3.  En el cuadro de **Name** , escriba el flujo de trabajo de tarea SPD.  
  
4.  En la lista de **Tipo de contenido** , elija **tarea**, y elija el botón de **Aceptar** .  
  
     El flujo de trabajo se abre en el diseñador de flujos de trabajo de SharePoint Designer.  
  
5.  En el diseñador de flujo de trabajo, elija el paso 1 y, a continuación, en la cinta de opciones, elija el botón de **Condición** .  
  
6.  En la lista de condiciones, elija **Si el campo del elemento actual es igual a valor**.  
  
     Este paso agrega una condición que se denomina **Si el campo es valor**.  
  
7.  En la condición de **Si el campo es valor** , elija el vínculo de **campo** .  
  
8.  En la lista de valores, elija **title**.  
  
9. En la condición de **Si el campo es valor** , elija el vínculo de **Valor** .  
  
10. En el cuadro, escriba Nueva tarea.  
  
     La instrucción condicional ahora es **Si el título de elemento actual es Nueva tarea**.  
  
11. Elija la línea bajo la instrucción condicional y, a continuación, en la cinta de opciones, elija el botón de **Acción** .  
  
12. En la lista de acciones, elija **Establezca el campo de elemento actual**.  
  
13. En la acción de **Establezca el campo en el valor** , elija el vínculo de **campo** y, a continuación, en la lista, elija **Asignado a**.  
  
14. En la acción de **Establezca el campo en el valor** , elija el vínculo de **Valor** y, a continuación, en la lista de usuarios existentes y grupos, elija **Usuario que creó el elemento**.  
  
15. Elija el botón **Agregar** y después elija el botón **Aceptar**.  
  
     La instrucción de acción ahora es **Establecer Asignado a en Elemento actual:CreatedBy**.  
  
## Guardar e implementar el flujo de trabajo reutilizable  
 Como [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solo puede importar archivos .wsp, debe guardar el flujo de trabajo reutilizable como un archivo .wsp e implementarlo en SharePoint antes de importarlo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Si recibe un error en tiempo de ejecución cuando lleva a cabo el procedimiento siguiente, tiene que realizar el procedimiento en un sistema con acceso al sitio de SharePoint.  
  
#### Para guardar e implementar el flujo de trabajo reutilizable  
  
1.  En la parte superior de SharePoint Designer, elija el botón de **Guardar** para guardar el progreso, y elija el botón de **Publicar** para implementar el flujo de trabajo en el sitio de SharePoint **SPD1** .  
  
2.  En el panel de navegación, elija el objeto de **Flujos de trabajo** .  
  
3.  En **Flujo de trabajo reutilizable**, elija **Flujo de trabajo de tarea SPD**.  
  
4.  En la cinta de opciones, elija el botón de **Guardar como plantilla** para guardar el flujo de trabajo como un archivo .wsp.  
  
5.  Abra el sitio de SharePoint **SPD1** en un explorador para ver el archivo .wsp en SharePoint.  
  
6.  En la barra de inicio rápido, elija el vínculo de **Bibliotecas** .  
  
7.  En la sección de **Bibliotecas de documentos** , elija el vínculo de **Activos del sitio** .  
  
     El archivo **Flujo de trabajo de tarea SPD** aparece con otros activos del sitio.  
  
8.  En la lista de archivos, elija el nombre de dicho archivo  
  
9. En el cuadro de diálogo de **Descarga de archivos** , elija el botón de **Guardar** para guardar el archivo .wsp en el sistema local.  
  
## Importar el archivo .wsp en Visual Studio  
 Importe el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizando un proyecto Importar flujo de trabajo reutilizable.  Este proyecto convierte un flujo de trabajo reutilizable y declarativo en un flujo de trabajo de código.  Una vez convertido el flujo de trabajo, se usa el código para modificar su comportamiento.  
  
#### Para importar un flujo de trabajo de un archivo .wsp y modificarlo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menú, elija **archivo**, **new**, **Project**.  
  
2.  En el cuadro de diálogo de **Nuevo proyecto** , expanda el nodo de **sharepoint** en **Visual C\#** o **Visual Basic**y, a continuación el nodo de **2010** .  
  
3.  En el panel de **Plantillas** , elija la plantilla de **Flujo de trabajo reutilizable de SharePoint 2010 de importación** , deje el nombre del proyecto como **WorkflowImportProject1**, y elija el botón de **Aceptar** .  
  
     Aparece el Asistente para personalización de SharePoint.  
  
4.  En la página de **Especifique el sitio y el nivel de seguridad de la depuración** , entre en [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó previamente: http:\/\/*system name*\/SPD2.  
  
5.  En la sección de **Cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción de **Implementar como solución de granja de servidores** , y elija el botón de **siguiente** .  
  
     Para obtener más información sobre soluciones de granja y soluciones en espacio aislado, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  En la página de **Especifique el nuevo origen del proyecto** , vaya a la ubicación del sistema donde guardó el archivo .wsp previamente, abra el archivo, y después elija el botón de **siguiente** .  
  
    > [!NOTE]  
    >  Elija el botón de **Finalizar** para importar todos los elementos disponibles en el archivo .wsp.  
  
     De este modo, se muestra una lista de los flujos de trabajo reutilizables que están disponibles para la importación.  
  
7.  En el cuadro de **Seleccione los elementos que desea importar** , elija el flujo de trabajo de **Flujo de trabajo de tarea SPD** , y elija el botón de **Finalizar** .  
  
     Una vez finalizada la operación de importación, se crea un proyecto denominado **WorkflowImportProject1** que contiene un flujo de trabajo denominado **SPD\_Workflow\_TestFT**.  En esta carpeta se encuentra el archivo de definición Elements.xml del flujo de trabajo y el archivo del diseñador de flujo de trabajo \(.xoml\).  El diseñador contiene dos archivos: el archivo de reglas \(.rules\) y el archivo de código subyacente \(.cs o .vb, dependiendo del lenguaje de programación de su proyecto\).  
  
8.  En **Explorador de soluciones**, elimine la carpeta de **Otros archivos importados** .  
  
9. En el archivo Elements.xml, elimine `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. En **Explorador de soluciones**, elija **WorkflowImportProject1**y, a continuación, en la barra de menús, elija **Project**, **Establecer como proyecto de inicio** para establecer **WorkflowImportProject1** como elemento de inicio.  
  
     De este modo, se mostrará la lista inmediatamente cuando se depure el proyecto.  
  
11. Dado que la plantilla de **Importar flujos de trabajo reutilizables de SharePoint 2010** no importa los valores de propiedad de asociación del flujo de trabajo importado, es necesario escribirlos.  Para hacerlo:  
  
    1.  En **Explorador de soluciones**, elija el nodo de **SPD\_Workflow\_TestFT** .  
  
    2.  Elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\) situado junto a una de las propiedades de la lista, como la propiedad de **Lista de destino** .  
  
    3.  Rellene los valores que faltan en el Asistente para la personalización de SharePoint, y después elija el botón de **Finalizar** .  
  
12. Elija el archivo .xoml y, a continuación, en la barra de menú, elija **Visualización**, **Diseñador** para ver el flujo de trabajo importado en el diseñador de flujo de trabajo.  
  
13. En el nodo de **Windows workflow v3.0** de **Cuadro de herramientas**, realice uno de los pasos siguientes:  
  
    -   Abrir el menú contextual de la actividad de **code** y, a continuación **copiar**.  En el diseñador de flujo de trabajo, abra el menú contextual para la línea bajo la actividad de **SequenceActivity1** y, a continuación **Pegar**.  
  
    -   Arrastre la actividad de **code** de **Cuadro de herramientas** el diseñador de flujo de trabajo, y conéctela a la línea bajo la actividad de **SequenceActivity1** .  
  
     Esto agrega una actividad al diseñador de flujo de trabajo denominada **ActividadCódigo1**.  En esta actividad, agregará una acción de código que crea un anuncio en la lista de anuncios cuando el usuario inicia el flujo de trabajo.  
  
14. Siga una de estas series de procedimientos:  
  
    -   Haga doble clic en **CodeActivity1** para generar un controlador de eventos y ver el código.  
  
    -   En la ventana de **Propiedades** para **CodeActivity1**, establezca el valor de la propiedad de **ExecuteCode** a **codeActivity\_ExecuteCode**.  
  
15. Agregue lo siguiente bajo las instrucciones **Imports** o **using** existentes:  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Reemplace `codeActivity1_ExecuteCode` por lo siguiente:  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## Implementar el proyecto y asociar el flujo de trabajo  
 A continuación, ejecute WorkflowImportProject1 para implementarlo en un sitio de SharePoint y después asocie el flujo de trabajo a la lista de Tareas para ver y probar el flujo de trabajo modificado y convertido.  
  
#### Para implementar el proyecto y asociar el flujo de trabajo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija la tecla F5 para ejecutar e implementar el proyecto de flujo de trabajo convertido.  
  
2.  En la barra de inicio rápido, elija el vínculo de **Tareas** para mostrar la lista de Tareas.  
  
3.  En la pestaña de **Enumera las herramientas** , elija el botón de **Elementos** , y elija el botón de **Nuevo elemento** .  
  
     El cuadro de diálogo de **Tareas \- nuevo elemento** abra.  
  
4.  En el cuadro de **title** , escriba nueva tarea, y elija el botón de **Guardar** .  
  
5.  En la pestaña de **Enumera las herramientas** , elija el botón de **list** , y elija el botón de **Configuración de la lista** .  
  
     La página de **Configuración de la lista** aparece.  
  
6.  En la sección de **Permisos y administración** , elija el vínculo de **Valores de flujo de trabajo** .  
  
     La página de **Valores de flujo de trabajo** aparece.  
  
7.  Elija el vínculo de **Agregue un flujo de trabajo** .  
  
8.  En la lista de **Flujo de trabajo** , elija **WorkflowImportProject1 \- prueba de flujo de trabajo SPD**.  
  
9. En el cuadro de **Name** , escriba prueba flujo trabajo SPD, y elija el botón de **Aceptar** .  
  
10. En la barra de inicio rápido, elija la lista de **Tareas** .  
  
11. Elija la flecha situada junto a **Nueva tarea**y, a continuación, en la lista, elija **Flujos de trabajo**.  
  
12. En la sección de **Inicie un nuevo flujo de trabajo** , elija el vínculo para **Prueba del flujo de trabajo SPD**, y elija el botón de **Comienzo** para iniciar el flujo de trabajo.  
  
    > [!NOTE]  
    >  También puede asociar automáticamente  un flujo de trabajo a una lista ejecutando el asistente para la configuración del flujo de trabajo y estableciendo el flujo de trabajo en asociar automáticamente.  
  
     Observe que el flujo de trabajo realiza dos acciones: su nombre aparece en la columna **Asignado a** de la tarea y aparece un anuncio en la lista **Anuncios**.  
  
## Vea también  
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  