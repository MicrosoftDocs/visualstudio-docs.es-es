---
title: Creación de un elemento web para SharePoint mediante el diseñador
description: En este tutorial, cree un elemento web visualmente mediante la plantilla de proyecto elemento web visual de SharePoint en Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 55f69875b06428c9bbe179e73dd6ea9b4ef40b8e
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112456"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Tutorial: Creación de un elemento web para SharePoint mediante un diseñador

Si crea elementos web para un sitio de SharePoint, los usuarios pueden modificar directamente el contenido, la apariencia y el comportamiento de las páginas de ese sitio mediante un explorador. En este tutorial se muestra cómo crear un elemento web visualmente mediante la plantilla de proyecto elemento **web visual** de SharePoint en Visual Studio.

El elemento web que va a crear muestra una vista de calendario mensual y una casilla para cada lista de calendarios del sitio. Los usuarios pueden especificar qué listas de calendario incluir en la vista de calendario mensual seleccionando las casillas.

En este tutorial se muestran las tareas siguientes:

- Creación de un elemento web mediante la **plantilla de proyecto Elemento web** visual.
- Diseñar el elemento web mediante el diseñador de Visual Web Developer en Visual Studio.
- Agregar código para controlar los eventos de los controles en el elemento web.
- Probar el elemento web en SharePoint.

    > [!NOTE]
    > El equipo puede mostrar diferentes nombres o ubicaciones para algunos elementos de la interfaz de usuario para Visual Studio en las instrucciones siguientes. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Windows y SharePoint.

## <a name="create-a-web-part-project"></a>Creación de un proyecto de elemento web

En primer lugar, cree un proyecto de elemento web mediante la **plantilla de proyecto Elemento web** visual.

1. Empiece [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] por usar la opción Ejecutar **como** administrador.

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.
::: moniker range="=vs-2017"

3. En el **cuadro de diálogo** Nuevo proyecto, en Visual **C#** o **Visual Basic**, expanda **Office/SharePoint** y, a continuación, elija la **categoría Soluciones de SharePoint.**

4. En la lista de plantillas, elija la plantilla **SharePoint 2013 - Visual Web Part** y, a continuación, elija el **botón** Aceptar.

     Aparece **el Asistente para personalización de SharePoint.** Con este asistente, puede especificar el sitio que usará para depurar el proyecto y el nivel de confianza de la solución.
::: moniker-end
::: moniker range=">=vs-2019"
3. En el **cuadro de diálogo Crear** un nuevo proyecto, seleccione el proyecto vacío de *SharePoint** para la versión concreta de SharePoint que ha instalado. Por ejemplo, si tiene la instalación de SharePoint 2019, seleccione la plantilla **SharePoint 2019 - Empty Project (Proyecto vacío de SharePoint 2019).**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. En el **cuadro** Nombre, escriba **TestProject1** y elija el **botón** Crear.

::: moniker-end
5. En la **sección ¿Cuál es el nivel de confianza de esta solución de SharePoint?,** elija el botón de opción Implementar como **solución de** granja.

6. Elija el **botón** Finalizar para aceptar el sitio de SharePoint local predeterminado.

## <a name="designing-the-web-part"></a>Diseño del elemento web

Diseñe el elemento web agregando controles desde el Cuadro **de herramientas** a la superficie del diseñador de Visual Web Developer.

1. En el diseñador de Visual Web Developer, elija la **pestaña Diseño** para cambiar a la vista Diseño.

2. En la barra de menús, elija **Ver cuadro de**  >  **herramientas.**

3. En el **nodo Estándar** del cuadro **de herramientas**, elija el control **CheckBoxList** y, a continuación, realice uno de los pasos siguientes:

    - Abra el menú contextual del control **CheckBoxList,** elija Copiar **,** abra el menú contextual de la primera línea del diseñador y, a continuación, **elija Pegar.**

    - Arrastre el **control CheckBoxList** desde el Cuadro **de** herramientas y conecte el control a la primera línea del diseñador.

4. Repita el paso anterior, pero mueva un botón a la siguiente línea del diseñador.

5. En el diseñador, elija el **botón Button1.**

6. En la barra de menús, elija **Ver**  >  **ventana Propiedades**.

     Se abre la ventana **Propiedades**.

7. En la **propiedad Text** del botón, escriba **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Control de los eventos de los controles en el elemento web

Agregue código que permita al usuario agregar calendarios a la vista del calendario maestro.

1. Siga una de estas series de procedimientos:

   - En el diseñador, haga doble clic en el **botón** Actualizar.

   - En la **ventana** Propiedades del botón **Actualizar,** elija el **botón** Eventos. En la **propiedad Click,** **escriba Button1_Click** y, a continuación, elija la tecla Entrar.

     El archivo de código de control de usuario se abre en el Editor de código y aparece `Button1_Click` el controlador de eventos. Más adelante, agregará código a este controlador de eventos.

2. Agregue las siguientes instrucciones a la parte superior del archivo de código de control de usuario.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. Agregue la siguiente línea de código a la `VisualWebPart1` clase . Este código declara un control de vista de calendario mensual.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. Reemplace el `Page_Load` método de la clase por el código `VisualWebPart1` siguiente. Este código realiza las tareas siguientes:

   - Agrega una vista de calendario mensual al control de usuario.

   - Agrega una casilla para cada lista de calendarios del sitio.

   - Especifica una plantilla para cada tipo de elemento que aparece en la vista de calendario.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. Reemplace el `Button1_Click` método de la clase por el código `VisualWebPart1` siguiente. Este código agrega elementos de cada calendario seleccionado a la vista del calendario maestro.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>Prueba del elemento web

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. El elemento web se agrega automáticamente a la Galería de elementos web en SharePoint. Para probar este proyecto, realizará las siguientes tareas:

- Agregue un evento a cada una de las dos listas de calendario independientes.
- Agregue el elemento web a una página de elemento web.
- Especifique las listas que se incluirán en la vista de calendario mensual.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Para agregar eventos a listas de calendario en el sitio

1. En Visual Studio, elija la **tecla F5.**

     Se abre el sitio de SharePoint y la [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] inicio rápido aparece en la página.

2. En la barra inicio rápido, en **Listas,** elija el **vínculo** Calendario.

     Aparece **la página** Calendario.

     Si no aparece ningún vínculo de calendario en la inicio rápido, elija el **vínculo Contenido del** sitio. Si la página Contenido del sitio no muestra un **elemento Calendario,** cree uno.

3. En la página Calendario, elija un  día y, a continuación, elija el vínculo Agregar del día seleccionado para agregar un evento.

4. En el **cuadro Título,** escriba **Evento en el calendario predeterminado** y, a continuación, elija el **botón** Guardar.

5. Elija el **vínculo Contenido del** sitio y, a continuación, elija el icono Agregar **una** aplicación.

6. En la **página** Crear, elija el **Tipo de** calendario, asigne un nombre al calendario y, a continuación, elija **el botón** Crear.

7. Agregue un evento al nuevo calendario, asigne al evento el nombre Evento en el **calendario personalizado** y, a continuación, elija **el botón** Guardar.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Para agregar el elemento web a una página de elemento web

1. En la **página Contenido del** sitio, abra la carpeta Páginas **del** sitio.

2. En la cinta de opciones, elija la **pestaña Archivos,** abra el **menú** Nuevo documento y, a continuación, elija el comando **Página de elementos** web.

3. En la **página Nueva página de elementos web,** asigne a la página el nombre **SampleWebPartPage.aspx** y, a continuación, elija **el botón** Crear.

     Aparece la página del elemento web.

4. En la zona superior de la página del elemento web, elija la **pestaña** Insertar y, a continuación, elija el **botón Elemento** web.

5. Elija la **carpeta Personalizada,** elija el elemento web **VisualWebPart1** y, a continuación, elija **el botón** Agregar.

     El elemento web aparece en la página. Los siguientes controles aparecen en el elemento web:

    - Una vista de calendario mensual.

    - Botón **Actualizar.**

    - Casilla **Calendario.**

    - Casilla **Calendario personalizado.**

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Para especificar listas que se incluirán en la vista de calendario mensual

En el elemento web, especifique los calendarios que desea incluir en la vista de calendario mensual y, a continuación, elija el **botón** Actualizar.

Los eventos de todos los calendarios especificados aparecen en la vista de calendario mensual.

## <a name="see-also"></a>Vea también

[Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Cómo: Crear un elemento web](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 de SharePoint [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
