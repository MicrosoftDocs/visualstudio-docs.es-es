---
title: 'Tutorial: personalizar la vista de texto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b7a62ee2b55bf2b56ae1d8e28fc1910ed444c29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904934"
---
# <a name="walkthrough-customize-the-text-view"></a>Tutorial: personalizar la vista de texto
Puede personalizar una vista de texto modificando cualquiera de las siguientes propiedades en la asignación de formato del editor:

- Margen del indicador

- Símbolo de intercalación de inserción

- Sobrescribir símbolo de intercalación

- Texto seleccionado

- Texto seleccionado inactivo (es decir, el texto seleccionado que pierde el foco)

- Espacio en blanco visible

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creación de un proyecto MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad**y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `ViewPropertyTest` .

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

## <a name="define-the-content-type"></a>Definir el tipo de contenido

1. Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.

2. Agregue las siguientes directivas `using`:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Declare una clase denominada `TestViewCreationListener` que herede de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exporte esta clase con los siguientes atributos:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar el tipo de contenido al que se aplica este agente de escucha.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar el rol de este agente de escucha.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. En esta clase, importe <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Cambiar las propiedades de la vista

1. Configure el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que las propiedades de la vista se cambien cuando se abra la vista. Para hacer el cambio, busque primero el <xref:System.Windows.ResourceDictionary> que corresponde al aspecto de la vista que desea buscar. A continuación, cambie la propiedad adecuada en el Diccionario de recursos y establezca las propiedades. Procesa por lotes las llamadas al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método llamando al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> después de establecer las propiedades.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Compilar y probar el código

1. Compile la solución.

     Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

2. Cree un archivo de texto y escriba algún texto.

    - El símbolo de intercalación de inserción debe ser magenta y el símbolo de intercalación de sobrescritura debe ser turquesa.

    - El margen del indicador (a la izquierda de la vista de texto) debe ser verde claro.

3. Seleccione el texto que escribió. El color del texto seleccionado debe ser rosa claro.

4. Mientras el texto está seleccionado, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser rosa oscuro.

5. Active el espacio en blanco visible. (En el menú **edición** , seleccione **avanzadas** y, a continuación, haga clic en **Ver espacio en blanco**). Escriba algunas pestañas en el texto. Deben mostrarse las flechas rojas que representan las pestañas.

## <a name="see-also"></a>Consulte también
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
