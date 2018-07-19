---
title: 'Tutorial: Crear un elemento Web para SharePoint utilizando un diseñador | Microsoft Docs'
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01efc1972ea4833900b5e6f002d36ae51fa63a85
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119450"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Tutorial: Crear un elemento web para SharePoint utilizando un diseñador

Si crea elementos web para un sitio de SharePoint, los usuarios pueden modificar directamente el contenido, la apariencia y comportamiento de las páginas de ese sitio mediante un explorador. En este tutorial se muestra cómo crear un elemento web visualmente usando SharePoint **elemento Web Visual** plantilla de proyecto en Visual Studio.

El elemento web que se va a crear muestra una vista de calendario mensual y una casilla para cada lista de calendarios del sitio. Los usuarios pueden especificar qué listas de calendario para incluir en la vista de calendario mensual activando las casillas de verificación.

En este tutorial se muestran las tareas siguientes:

- Crear un elemento web utilizando el **elemento Web Visual** plantilla de proyecto.
- Diseñar el elemento web mediante el Diseñador de Visual Web Developer en Visual Studio.
- Agregar código para controlar los eventos de los controles en el elemento web.
- Probar el elemento web en SharePoint.

    > [!NOTE]
    > El equipo podría mostrar nombres o ubicaciones en algunos elementos de la interfaz de usuario para Visual Studio diferentes en las instrucciones siguientes. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

Necesita los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint. Consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

## <a name="create-a-web-part-project"></a>Crear un proyecto de elemento web

En primer lugar, cree un proyecto de elemento web utilizando el **elemento Web Visual** plantilla de proyecto.

1. Iniciar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizando el **ejecutar como administrador** opción.

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto** .

3. En el **nuevo proyecto** cuadro de diálogo, bajo **Visual C#** o **Visual Basic**, expanda **Office/SharePoint**y, a continuación, elija el  **Las soluciones de SharePoint** categoría.

4. En la lista de plantillas, elija el **SharePoint 2013 - elemento Web Visual** plantilla y, a continuación, elija el **Aceptar** botón.

     El **Asistente de personalización de SharePoint** aparece. Con este asistente, puede especificar el sitio que va a usar para depurar el proyecto y el nivel de confianza de la solución.

5. En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.

6. Elija la **finalizar** botón para aceptar el sitio local predeterminado de SharePoint.

## <a name="designing-the-web-part"></a>Diseñar el elemento web

Diseñar el elemento web agregando controles desde el **cuadro de herramientas** a la superficie del Diseñador de Visual Web Developer.

1. En el Diseñador de Visual Web Developer, elija el **diseño** tab para cambiar a la vista Diseño.

2. En la barra de menús, elija **vista** > **cuadro de herramientas**.

3. En el **estándar** nodo de la **cuadro de herramientas**, elija el **CheckBoxList** controlar y, a continuación, realice uno de los pasos siguientes:

    - Abra el menú contextual para el **CheckBoxList** control, elija **copia**, abra el menú contextual de la primera línea en el diseñador y, a continuación, elija **pegar**.

    - Arrastre el **CheckBoxList** controlar desde la **cuadro de herramientas**y conectar el control a la primera línea en el diseñador.

4. Repita el paso anterior, pero mueva un botón a la línea siguiente del diseñador.

5. En el diseñador, elija el **Button1** botón.

6. En la barra de menús, elija **vista** > **ventana propiedades**.

     El **propiedades** abre la ventana.

7. En el **texto** propiedad del botón, escriba **actualización**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Controlar los eventos de controles en el elemento web

Agregue código que permita al usuario agregar calendarios a la vista de calendario principal.

1. Siga una de estas series de procedimientos:

    - En el diseñador, haga doble clic en el **actualización** botón.

    - En el **propiedades** ventana para el **actualización** botón, elija la **eventos** botón. En el **haga clic en** propiedad, escriba **Button1_Click**y, a continuación, elija la tecla ENTRAR.

     El archivo de código de control de usuario se abre en el Editor de código y la `Button1_Click` aparece el controlador de eventos. Más adelante, agregará código a este controlador de eventos.

2. Agregue las siguientes instrucciones al principio del archivo de código de control de usuario.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Agregue la siguiente línea de código para el `VisualWebPart1` clase. Este código declara un control de vista de calendario mensual.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Reemplace el `Page_Load` método de la `VisualWebPart1` con el código siguiente. Este código realiza las tareas siguientes:

    - Agrega una vista de calendario mensual al control de usuario.

    - Agrega una casilla para cada lista de calendarios del sitio.

    - Especifica una plantilla para cada tipo de elemento que aparece en la vista de calendario.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Reemplace el `Button1_Click` método de la `VisualWebPart1` con el código siguiente. Este código agrega los elementos de cada calendario seleccionado a la vista de calendario principal.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Probar el elemento web

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. El elemento web se agrega automáticamente a la Galería de elementos Web en SharePoint. Para probar este proyecto, realizará las tareas siguientes:

- Agregar un evento a cada una de las dos listas de calendarios independientes.
- Agregar el elemento web a una página de elementos web.
- Especifique las listas para incluir en la vista de calendario mensual.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Para agregar eventos a listas de calendario en el sitio

1. En Visual Studio, elija el **F5** clave.

     Se abre el sitio de SharePoint y el [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barra Inicio rápido aparece en la página.

2. En la barra Inicio rápido, bajo **enumera**, elija el **calendario** vínculo.

     El **calendario** aparece la página.

     Si ningún vínculo de calendario aparece en la barra Inicio rápido, elija el **contenidos del sitio** vínculo. Si no aparece la página de contenido del sitio un **calendario** de elemento, cree uno.

3. En la página de calendario, elija el día y, a continuación, elija el **agregar** vínculo en el día seleccionado para agregar un evento.

4. En el **título** , escriba **eventos en el calendario predeterminado**y, a continuación, elija el **guardar** botón.

5. Elija la **contenidos del sitio** vincular y, a continuación, elija el **agregar una aplicación** icono.

6. En el **crear** página, elija el **calendario** escriba, asignar nombre al calendario y, a continuación, elija el **crear** botón.

7. Agregar un evento en el calendario nuevo, asigne el nombre del evento **eventos en el calendario personalizado**y, a continuación, elija el **guardar** botón.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Para agregar el elemento web a una página de elementos web

1. En el **contenidos del sitio** página, abra el **páginas Site** carpeta.

2. En la cinta de opciones, elija la **archivos** pestaña, abra el **nuevo documento** menú y, a continuación, elija el **página de elementos Web** comando.

3. En el **nueva página de elementos Web** página, asigne el nombre de la página **SampleWebPartPage.aspx**y, a continuación, elija el **crear** botón.

     Aparece la página de elementos web.

4. En la zona superior de la página de elementos web, elija el **insertar** pestaña y, a continuación, elija el **elemento Web** botón.

5. Elija la **personalizado** carpeta, elija la **VisualWebPart1** elemento web y, a continuación, elija el **agregar** botón.

     El elemento web aparece en la página. Los siguientes controles aparecen en el elemento web:

    - Una vista de calendario mensual.

    - Un **actualización** botón.

    - Un **calendario** casilla de verificación.

    - Un **calendario personalizado** casilla de verificación.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Para especificar listas para incluir en la vista de calendario mensual

En el elemento web, especifique los calendarios que desea incluir en la vista de calendario mensual y, a continuación, elija el **actualización** botón.

Los eventos de todos los calendarios especificados aparecen en la vista de calendario mensual.

## <a name="see-also"></a>Vea también

[Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Cómo: crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
