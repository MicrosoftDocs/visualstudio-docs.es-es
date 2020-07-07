---
title: Crear un elemento Web para SharePoint mediante el diseñador
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 732bd9fe3d34a768e0c6f71315f212c49bdf02af
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016393"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Tutorial: crear un elemento Web para SharePoint mediante un diseñador

Si crea elementos Web para un sitio de SharePoint, los usuarios pueden modificar directamente el contenido, la apariencia y el comportamiento de las páginas de ese sitio mediante un explorador. En este tutorial se muestra cómo crear un elemento web visualmente con la plantilla de proyecto de **elemento Web visual** de SharePoint en Visual Studio.

El elemento Web que creará muestra una vista de calendario mensual y una casilla para cada lista de calendarios del sitio. Los usuarios pueden especificar las listas de calendarios que se van a incluir en la vista de calendario mensual activando las casillas.

En este tutorial se muestran las tareas siguientes:

- Crear un elemento Web utilizando la plantilla de proyecto **elemento Web visual** .
- Diseñar el elemento Web mediante el diseñador de Visual Web Developer en Visual Studio.
- Agregar código para controlar los eventos de los controles en el elemento Web.
- Probar el elemento Web en SharePoint.

    > [!NOTE]
    > Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint.

## <a name="create-a-web-part-project"></a>Crear un proyecto de elemento Web

En primer lugar, cree un proyecto de elemento Web mediante la plantilla de proyecto **elemento Web visual** .

1. Empiece [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la opción **Ejecutar como administrador** .

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto** .

3. En el cuadro de diálogo **nuevo proyecto** , en **Visual C#** o **Visual Basic**, expanda **Office/SharePoint**y, a continuación, elija la categoría **soluciones de SharePoint** .

4. En la lista de plantillas, elija la plantilla de **elemento Web SharePoint 2013-visual** y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** . Con este asistente, puede especificar el sitio que usará para depurar el proyecto y el nivel de confianza de la solución.

5. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción **implementar como solución de granja de servidores** .

6. Elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.

## <a name="designing-the-web-part"></a>Diseñar el elemento Web

Diseñe el elemento Web agregando controles desde el **cuadro de herramientas** a la superficie del diseñador de Visual Web Developer.

1. En el diseñador de Visual Web Developer, elija la pestaña **diseño** para cambiar a vista de diseño.

2. En la barra de menús, elija **Ver**  >  **cuadro de herramientas**.

3. En el nodo **estándar** del **cuadro de herramientas**, elija el control **CheckBoxList** y, a continuación, realice uno de los pasos siguientes:

    - Abra el menú contextual del control **CheckBoxList** , elija **copiar**, abra el menú contextual de la primera línea del diseñador y, a continuación, elija **pegar**.

    - Arrastre el control **CheckBoxList** desde el **cuadro de herramientas**y conecte el control a la primera línea del diseñador.

4. Repita el paso anterior, pero mueva un botón a la línea siguiente del diseñador.

5. En el diseñador, elija el botón **button1** .

6. En la barra de menús, elija **Ver**  >  **ventana Propiedades**.

     Se abre la ventana **Propiedades**.

7. En la propiedad **texto** del botón, escriba **Actualizar**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Controlar los eventos de los controles en el elemento Web

Agregue código que permita al usuario agregar calendarios a la vista de calendario principal.

1. Siga una de estas series de procedimientos:

   - En el diseñador, haga doble clic en el botón **Actualizar** .

   - En la ventana **propiedades** del botón **Actualizar** , elija el botón **eventos** . En la propiedad **click** , escriba **Button1_Click**y, a continuación, elija la tecla entrar.

     El archivo de código de control de usuario se abre en el editor de código y `Button1_Click` aparece el controlador de eventos. Más adelante, agregará código a este controlador de eventos.

2. Agregue las siguientes instrucciones a la parte superior del archivo de código del control de usuario.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Agregue la siguiente línea de código a la `VisualWebPart1` clase. Este código declara un control de vista de calendario mensual.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Reemplace el `Page_Load` método de la `VisualWebPart1` clase por el código siguiente. Este código realiza las tareas siguientes:

   - Agrega una vista de calendario mensual al control de usuario.

   - Agrega una casilla para cada lista de calendarios del sitio.

   - Especifica una plantilla para cada tipo de elemento que aparece en la vista de calendario.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Reemplace el `Button1_Click` método de la `VisualWebPart1` clase por el código siguiente. Este código agrega elementos de cada calendario seleccionado a la vista de calendario principal.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Probar el elemento Web

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. El elemento Web se agrega automáticamente a la galería de elementos Web de SharePoint. Para probar este proyecto, realizará las siguientes tareas:

- Agregue un evento a cada una de las dos listas de calendarios independientes.
- Agregue el elemento Web a una página de elementos Web.
- Especifique las listas que se van a incluir en la vista de calendario mensual.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Para agregar eventos a las listas de calendarios del sitio

1. En Visual Studio, elija la tecla **F5** .

     Se abre el sitio de SharePoint y [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] aparece la barra de inicio rápido en la página.

2. En la barra Inicio rápido, en **listas**, elija el vínculo **calendario** .

     Aparece la página **calendario** .

     Si no aparece ningún vínculo de calendario en la barra Inicio rápido, elija el vínculo **contenido del sitio** . Si la página contenido del sitio no muestra un elemento de **calendario** , cree uno.

3. En la página calendario, elija un día y, a continuación, elija el vínculo **Agregar** en el día seleccionado para agregar un evento.

4. En el cuadro **título** , escriba **evento en el calendario predeterminado**y elija el botón **Guardar** .

5. Elija el vínculo **contenido del sitio** y, a continuación, elija el icono **Agregar una aplicación** .

6. En la página **crear** , elija el tipo de **calendario** , asigne un nombre al calendario y, a continuación, elija el botón **crear** .

7. Agregue un evento al nuevo calendario, asigne un nombre al **evento de evento en el calendario personalizado**y elija el botón **Guardar** .

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Para agregar el elemento Web a una página de elementos Web

1. En la página **contenido del sitio** , abra la carpeta páginas del **sitio** .

2. En la cinta de opciones, elija la pestaña **archivos** , abra el menú **nuevo documento** y, a continuación, elija el comando **Página de elementos Web** .

3. En la página **nueva página de elementos Web** , asigne un nombre a la página **nombre samplewebpartpage. aspx**y, a continuación, elija el botón **crear** .

     Aparece la página de elementos Web.

4. En la zona superior de la página de elementos Web, elija la pestaña **Insertar** y, a continuación, elija el botón **elemento Web** .

5. Elija la carpeta **personalizado** , elija el elemento Web **VisualWebPart1** y, a continuación, elija el botón **Agregar** .

     El elemento Web aparece en la página. Los controles siguientes aparecen en el elemento Web:

    - Vista de calendario mensual.

    - Botón **Actualizar** .

    - Casilla de verificación de **calendario** .

    - Casilla **calendario personalizado** .

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Para especificar las listas que se van a incluir en la vista de calendario mensual

En el elemento Web, especifique los calendarios que desee incluir en la vista de calendario mensual y, a continuación, elija el botón **Actualizar** .

Los eventos de todos los calendarios que especificó aparecen en la vista de calendario mensual.

## <a name="see-also"></a>Consulte también

[Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Cómo: crear un elemento](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 Web de SharePoint [Tutorial: crear un elemento Web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
