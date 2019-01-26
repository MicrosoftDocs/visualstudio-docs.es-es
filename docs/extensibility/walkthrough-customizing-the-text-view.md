---
title: 'Tutorial: Personalizar la vista de texto | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a697456a15008f305b92aacfb1485be1c08c062
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920402"
---
# <a name="walkthrough-customize-the-text-view"></a>Tutorial: Personalizar la vista de texto
Puede personalizar una vista de texto mediante la modificación de cualquiera de las siguientes propiedades en su mapa de formato del editor:  
  
-   Margen del indicador  
  
-   Símbolo de intercalación de inserción  
  
-   Sobrescribir el símbolo de intercalación  
  
-   Texto seleccionado  
  
-   Texto seleccionado inactivo (es decir, texto seleccionado que se ha perdido el foco)  
  
-   Espacio en blanco visible  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Crear un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `ViewPropertyTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="define-the-content-type"></a>Definir el tipo de contenido  
  
1. Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.  
  
2. Agregue las siguientes `using` directivas:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3. Declare una clase llamada `TestViewCreationListener` que hereda de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportar a esta clase con los siguientes atributos:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar el tipo de contenido al que se aplica este agente de escucha.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar el rol de este agente de escucha.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4. En esta clase, importe el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>Cambiar las propiedades de vista  
  
1.  Configurar la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que se cambian las propiedades de la vista cuando se abre la vista. Para realizar el cambio, primero busque el <xref:System.Windows.ResourceDictionary> que se corresponde con el aspecto de la vista que desea buscar. A continuación, cambie la propiedad adecuada en el diccionario de recursos y establecer las propiedades. Procesar por lotes las llamadas a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método mediante una llamada a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> después de establecer las propiedades.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>Compilar y probar el código  
  
1.  Compile la solución.  
  
     Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.  
  
2.  Cree un archivo de texto y escriba algún texto.  
  
    -   El punto de inserción debe ser magenta y el símbolo de intercalación de sobrescritura deben turquesa.  
  
    -   El margen del indicador (a la izquierda de la vista de texto) debe ser la luz verde.  
  
3.  Seleccione el texto que escribió. El color del texto seleccionado debe ser ligero rosa.  
  
4.  Mientras que el texto seleccionado, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser rosa oscuro.  
  
5.  Activar el espacio en blanco visible. (En el **editar** menú, elija **avanzadas** y, a continuación, haga clic en **ver espacios en blanco**). Escriba algunas de las pestañas en el texto. Se deben mostrar las flechas rojas que representan las fichas.  
  
## <a name="see-also"></a>Vea también  
 [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)