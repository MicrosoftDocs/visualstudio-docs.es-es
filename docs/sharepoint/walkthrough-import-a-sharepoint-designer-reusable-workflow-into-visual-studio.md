---
title: 'Tutorial: importar un flujo de trabajo reutilizable de SharePoint Designer | Microsoft Docs'
titleSuffix: ''
description: En este tutorial, importe un flujo de trabajo reutilizable creado en SharePoint Designer en un proyecto de flujo de trabajo de Visual Studio SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1421b061c50277177b5a30f0357725e9a042f3bd
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970185"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Tutorial: importar un flujo de trabajo reutilizable de SharePoint Designer

  En este tutorial se muestra cómo importar un flujo de trabajo reutilizable creado en SharePoint Designer 2010 en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de flujo de trabajo de SharePoint.

 Los flujos de trabajo creados en SharePoint Designer, o *flujos de trabajo declarativos*, se componen de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones en lugar de código. SharePoint Designer 2010 presenta *flujos de trabajo reutilizables*, que son flujos de trabajo declarativos y portátiles que se pueden usar en distintas listas de sitios de SharePoint.

 Los flujos de trabajo creados en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , como los flujos de trabajo de equipo de estado y secuenciales, se denominan *flujos de trabajo de código*. Los flujos de trabajo de código constan de archivos XML y módulos de código en los que los usuarios pueden personalizar el comportamiento del flujo de trabajo.

 Visual Studio permite importar flujos de trabajo reutilizables creados en SharePoint Designer 2010 y convertirlos en flujos de trabajo de código para su uso en los sitios de SharePoint.

 En este tutorial se muestran las siguientes tareas:

- Crear un flujo de trabajo sencillo y reutilizable en SharePoint Designer.

- Exportar el flujo de trabajo reutilizable de SharePoint Designer a un archivo *. wsp* y a SharePoint.

- Importar el archivo *. wsp* en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mediante el proyecto importar flujo de trabajo reutilizable.

- Modificar el flujo de trabajo agregando código.

- Usar el flujo de trabajo importado en un sitio de SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Crear subsitios de SharePoint de destino
 En primer lugar, cree dos nuevos subsitios de SharePoint: uno para hospedar los flujos de trabajo reutilizables desde SharePoint Designer y otro para hospedar los flujos de trabajo convertidos.

#### <a name="to-create-sharepoint-subsites"></a>Para crear subsitios de SharePoint

1. En SharePoint Designer 2010, en la barra de menús, elija **archivo**  >  **nuevo sitio web en blanco**.

2. En el cuadro de diálogo **nuevo sitio web en blanco** , vaya a un sitio de SharePoint en el que desee crear el flujo de trabajo o use el valor de http://<em>SystemName</em>/y, a continuación, elija el botón **Aceptar** .

    Aparece la Página principal.

3. En la sección **subsitios** , elija el botón **nuevo** .

4. En el cuadro de diálogo **nuevo** , seleccione **plantillas de SharePoint** en la lista del panel izquierdo y elija **sitio de grupo** en la lista del panel derecho.

5. En el cuadro **especifique la ubicación del sitio web** , reemplace el **subsitio** de Word de la dirección URL por **SPD1** y, a continuación, elija el botón **Aceptar** .

    Se abrirá el nuevo subsitio en SharePoint Designer. Cierre esta instancia de SharePoint Designer y vuelva a la primera instancia (el sitio de nivel superior).

6. Repita los pasos del 3-5 para crear el segundo subsitio, y esta vez Reemplace el **subsitio** de Word en [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Crear un flujo de trabajo reutilizable de SharePoint Designer
 Dado que SharePoint no incluye ningún flujo de trabajo reutilizable que pueda usar en este ejemplo, creará uno. En este flujo de trabajo simple, cuando un usuario escribe una nueva tarea en la lista de tareas que tiene un título específico, la tarea se asigna a ese usuario.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Para crear un flujo de trabajo reutilizable de SharePoint Designer

1. En la sección **subsitios** , elija el sitio **SPD1** para modificarlo.

2. En la cinta de opciones, elija el botón **flujo de trabajo reutilizable** .

     Aparece el Asistente para crear flujo de trabajo reutilizable.

3. En el cuadro **nombre** , escriba **flujo de trabajo de tarea SPD**.

4. En la lista **tipo de contenido** , elija **tarea** y, a continuación, elija el botón **Aceptar** .

     El flujo de trabajo se abre en el diseñador de flujo de trabajo de SharePoint Designer.

5. En el diseñador de flujo de trabajo, elija el paso 1 y, a continuación, en la cinta de opciones, elija el botón **condición** .

6. En la lista de condiciones, elija **si el campo de elemento actual es igual a valor**.

     Este paso agrega una condición denominada si el **campo es igual a valor**.

7. En el **campo si el campo es igual** a la condición de valor, elija el vínculo de **campo** .

8. En la lista de valores, elija **título**.

9. En el **campo si el campo es igual** a la condición de valor, elija el vínculo **valor** .

10. En el cuadro, escriba **nueva tarea**.

     La instrucción de condición ahora lee **si elemento actual: el título es la nueva tarea**.

11. Elija la línea en la instrucción de condición y, a continuación, en la cinta de opciones, elija el botón de **acción** .

12. En la lista de acciones, elija **establecer campo en elemento actual**.

13. En la acción **establecer campo en valor** , elija el vínculo de **campo** y, a continuación, en la lista, elija **asignado a**.

14. En la acción **establecer campo en valor** , elija el vínculo **valor** y, a continuación, en la lista de usuarios y grupos existentes, elija el **usuario que creó el elemento**.

15. Elija el botón **Agregar** y, a continuación, elija el botón **Aceptar** .

     La instrucción de acción ahora lee **Set asignado a en el elemento actual: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Guardar e implementar el flujo de trabajo reutilizable
 Dado que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solo puede importar archivos *. wsp* , debe guardar el flujo de trabajo reutilizable como archivo *. wsp* e implementarlo en SharePoint antes de importarlo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Si recibe un error de tiempo de ejecución que realiza el procedimiento siguiente, tendrá que realizar el procedimiento en un sistema que tenga acceso al sitio de SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Para guardar e implementar el flujo de trabajo reutilizable

1. En la parte superior de SharePoint Designer, elija el botón **Guardar** para guardar el progreso y, a continuación, elija el botón **publicar** para implementar el flujo de trabajo en el sitio de SharePoint de **SPD1** .

2. En el panel de navegación, elija el objeto **flujos de trabajo** .

3. En **flujo de trabajo reutilizable**, elija el flujo de trabajo de la **tarea SPD**.

4. En la cinta de opciones, elija el botón **Guardar como plantilla** para guardar el flujo de trabajo como un archivo *. wsp* .

5. Abra el sitio de SharePoint de **SPD1** en un explorador para ver el archivo *. wsp* en SharePoint.

6. En la barra de inicio rápido, elija el vínculo **bibliotecas** .

7. En la sección **bibliotecas de documentos** , elija el vínculo recursos del **sitio** .

     El archivo de flujo de trabajo de la **tarea SPD** aparece con otros recursos del sitio.

8. En la lista de archivos, elija el nombre de ese archivo.

9. En el cuadro de diálogo **descarga de archivos** , elija el botón **Guardar** para guardar el archivo *. wsp* en el sistema local.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importar el archivo. wsp en Visual Studio
 Importe el archivo *. wsp* en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando un proyecto importar flujo de trabajo reutilizable. Este proyecto convierte el flujo de trabajo de un flujo de trabajo declarativo y reutilizable en un flujo de trabajo de código. Una vez convertido el flujo de trabajo, utilizará el código para modificar su comportamiento.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Para importar un flujo de trabajo desde un archivo. wsp y modificarlo

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , en la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **SharePoint** en **Visual C#** o en **Visual Basic** y, a continuación, elija el nodo **2010** .

3. En el panel **plantillas** , elija la plantilla de **flujo de trabajo importar reutilizable de SharePoint 2010** , deje el nombre del proyecto como **WorkflowImportProject1** y, a continuación, elija el botón **Aceptar** .

    Aparece el Asistente para personalización de SharePoint.

4. En la página **especifique el sitio y el nivel de seguridad de la depuración** , escriba [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó anteriormente: http://<em>nombre del sistema</em>/SPD2.

5. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **siguiente** .

    Para obtener más información sobre las soluciones en espacio aislado frente a las de granja, consulte [consideraciones sobre soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

6. En la página **especificar el origen del nuevo proyecto** , vaya a la ubicación en el sistema donde guardó anteriormente el archivo *. wsp* , abra el archivo y, a continuación, elija el botón **siguiente** .

   > [!NOTE]
   > Elija el botón **Finalizar** para importar todos los elementos disponibles en el archivo *. wsp* .

    Esto muestra una lista de flujos de trabajo reutilizables disponibles para la importación.

7. En el cuadro **seleccionar elementos para importar** , elija el flujo de trabajo del flujo de trabajo de la **tarea SPD** y elija el botón **Finalizar** .

    Una vez finalizada la operación de importación, se crea un proyecto denominado **WorkflowImportProject1** que contiene un flujo de trabajo denominado **SPD_Workflow_TestFT**. En esta carpeta se encuentra el archivo de definición del flujo de trabajo *Elements.xml* y el archivo del diseñador de flujo de trabajo (*. xoml*). El diseñador contiene dos archivos: el archivo de reglas (. Rules) y el archivo de código subyacente ( *. CS* o *. VB*, según el lenguaje de programación del proyecto).

8. En **Explorador de soluciones**, elimine la carpeta **otros archivos importados** .

9. En el archivo de *Elements.xml* , elimine `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. En **Explorador de soluciones**, elija **WorkflowImportProject1** y, a continuación, en la barra de menús, elija **proyecto**  >  **establecer como proyecto de inicio** para establecer **WorkflowImportProject1** como elemento de inicio.

     Esto muestra la lista inmediatamente al depurar el proyecto.

11. Dado que la plantilla de **flujo de trabajo importar reutilizable de SharePoint 2010** no importa los valores de propiedad de Asociación para el flujo de trabajo importado, debe escribirlos. Para hacerlo:

    1. En **Explorador de soluciones**, elija el nodo **SPD_Workflow_TestFT** .

    2. Elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) situado junto a una de las propiedades de la lista, como la propiedad **lista de destino** .

    3. Rellene los valores que faltan en el Asistente para la personalización de SharePoint y, a continuación, elija el botón **Finalizar** .

12. Elija el archivo. xoml y, a continuación, en la barra de menús, elija Diseñador de **vistas**  >  **Designer** para ver el flujo de trabajo importado en el diseñador de flujo de trabajo.

13. En el nodo **Windows Workflow v 3.0** del **cuadro de herramientas**, realice uno de los pasos siguientes:

    - Abra el menú contextual de la actividad de **código** y, a continuación, elija **copiar**. En el diseñador de flujo de trabajo, abra el menú contextual de la línea bajo la actividad **SequenceActivity1** y, a continuación, elija **pegar**.

    - Arrastre la actividad **code** del **cuadro de herramientas** al diseñador de flujo de trabajo y conéctela a la línea bajo la actividad **SequenceActivity1** .

      Esto agrega una actividad al diseñador de flujo de trabajo denominado **CodeActivity1**. En esta actividad, agregará una acción de código que crea un anuncio en la lista anuncios cuando el usuario inicia el flujo de trabajo.

14. Siga una de estas series de procedimientos:

    - Haga doble clic en **CodeActivity1** para generar un controlador de eventos y ver el código.

    - En la ventana **propiedades** de **CodeActivity1**, establezca el valor de la propiedad **ExecuteCode** en **codeActivity_ExecuteCode**.

15. Agregue lo siguiente en las directivas **using** o **Imports** existentes:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Reemplace `codeActivity1_ExecuteCode` por lo siguiente:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Implementar el proyecto y asociar el flujo de trabajo
 A continuación, ejecute WorkflowImportProject1 para implementarlo en un sitio de SharePoint y, a continuación, asocie el flujo de trabajo a la lista de tareas para ver y probar el flujo de trabajo modificado y convertido.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Para implementar el proyecto y asociar el flujo de trabajo

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , elija la tecla **F5** para ejecutar e implementar el proyecto de flujo de trabajo convertido.

2. En la barra de inicio rápido, elija el vínculo **tareas** para mostrar la lista de tareas.

3. En la pestaña **herramientas de lista** , elija el botón **elementos** y, a continuación, elija el botón **nuevo elemento** .

     Se abrirá el cuadro **de diálogo tareas-nuevo elemento** .

4. En el cuadro **título** , escriba **nueva tarea** y elija el botón **Guardar** .

5. En la pestaña **herramientas de lista** , elija el botón **lista** y, a continuación, elija el botón **Mostrar configuración** .

     Aparece la página Configuración de la **lista** .

6. En la sección **permisos y administración** , elija el vínculo **configuración de flujo de trabajo** .

     Aparece la página **configuración del flujo de trabajo** .

7. Elija el vínculo **Agregar un flujo de trabajo** .

8. En la lista **flujo de trabajo** , elija **WorkflowImportProject1-SPD Workflow test**.

9. En el cuadro **nombre** , escriba **prueba de flujo de trabajo SPD** y elija el botón **Aceptar** .

10. En la barra de inicio rápido, elija la lista de **tareas** .

11. Elija la flecha situada junto a **nueva tarea** y, a continuación, en la lista, elija **flujos de trabajo**.

12. En la sección **iniciar un nuevo flujo de trabajo** , elija el vínculo de **prueba de flujo de trabajo SPD** y, a continuación, elija el botón **iniciar** para iniciar el flujo de trabajo.

    > [!NOTE]
    > Como alternativa, puede asociar automáticamente un flujo de trabajo a una lista ejecutando el Asistente para configuración de flujo de trabajo y estableciendo el flujo de trabajo en asociación automática.

     Observe que el flujo de trabajo realiza dos acciones: su nombre aparece en la columna **asignado a** de la tarea y aparece un anuncio en la lista **anuncios** .

## <a name="see-also"></a>Vea también
- [Importación de elementos desde un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creación de controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
