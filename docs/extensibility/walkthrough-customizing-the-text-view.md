---
title: 'Tutorial: Personalización de la vista de texto ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697467"
---
# <a name="walkthrough-customize-the-text-view"></a>Tutorial: Personalizar la vista de texto
Puede personalizar una vista de texto modificando cualquiera de las siguientes propiedades en su mapa de formato editor:

- Margen del indicador

- Intercalación de inserción

- Sobrescribir el cuidado

- Texto seleccionado

- Texto seleccionado inactivo (es decir, texto seleccionado que ha perdido el foco)

- Espacio en blanco visible

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `ViewPropertyTest`nombre a la solución .

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

## <a name="define-the-content-type"></a>Definir el tipo de contenido

1. Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.

2. Agregue las siguientes directivas `using`:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Declare una `TestViewCreationListener` clase denominada <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>que herede de . Exporte esta clase con los siguientes atributos:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>para especificar el tipo de contenido al que se aplica este agente de escucha.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>para especificar el rol de este agente de escucha.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. En esta clase, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>importe el archivo .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Cambiar las propiedades de la vista

1. Configure el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que las propiedades de la vista se cambien cuando se abra la vista. Para realizar el cambio, <xref:System.Windows.ResourceDictionary> primero busque el que corresponde al aspecto de la vista que desea encontrar. A continuación, cambie la propiedad adecuada en el diccionario de recursos y establezca las propiedades. Lote las llamadas al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método mediante una llamada al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, el después de establecer las propiedades.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Compile y pruebe el código

1. Compile la solución.

     Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

2. Cree un archivo de texto y escriba algún texto.

    - El intercalador de inserción debe ser magenta y el intercalador de sobrescritura debe ser de color turquesa.

    - El margen del indicador (a la izquierda de la vista de texto) debe ser de color verde claro.

3. Seleccione el texto que escribió. El color del texto seleccionado debe ser de color rosa claro.

4. Mientras el texto está seleccionado, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser de color rosa oscuro.

5. Active el espacio en blanco visible. (En el menú **Edición,** seleccione **Avanzado** y, a continuación, haga clic en **Ver espacio en blanco**). Escriba algunas pestañas en el texto. Se deben mostrar las flechas rojas que representan las pestañas.

## <a name="see-also"></a>Vea también
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
