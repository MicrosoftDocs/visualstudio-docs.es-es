---
title: 'Tutorial: Personalizar la vista de texto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781821"
---
# <a name="walkthrough-customizing-the-text-view"></a>Tutorial: Personalización de la vista de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede personalizar una vista de texto mediante la modificación de cualquiera de las siguientes propiedades en su mapa de formato del editor:  
  
-   Margen del indicador  
  
-   Símbolo de intercalación de inserción  
  
-   Sobrescribir el símbolo de intercalación  
  
-   Texto seleccionado  
  
-   Texto seleccionado inactivo (es decir, texto seleccionado que se ha perdido el foco)  
  
-   Espacio en blanco visible  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `ViewPropertyTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="defining-the-content-type"></a>Definir el tipo de contenido  
  
1. Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.  
  
2. Agregue las siguientes `using` directivas:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Declare una clase llamada `TestViewCreationListener` que hereda de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportar a esta clase con los siguientes atributos:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar el tipo de contenido al que se aplica este agente de escucha.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar el rol de este agente de escucha.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. En esta clase, importe el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Cambiar las propiedades de vista  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que se cambian las propiedades de la vista cuando se abre la vista. Para realizar el cambio, primero busque el <xref:System.Windows.ResourceDictionary> que se corresponde con el aspecto de la vista que desea buscar. A continuación, cambie la propiedad adecuada en el diccionario de recursos y establecer las propiedades. Procesar por lotes las llamadas a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método mediante una llamada a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> después de establecer las propiedades.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
  
1.  Compile la solución.  
  
     Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
2.  Cree un archivo de texto y escriba algún texto.  
  
    -   El punto de inserción debe ser magenta y el símbolo de intercalación de sobrescritura deben turquesa.  
  
    -   El margen del indicador (a la izquierda de la vista de texto) debe ser la luz verde.  
  
3.  Seleccione el texto que escribió. El color del texto seleccionado debe ser ligero rosa.  
  
4.  Mientras que el texto seleccionado, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser rosa oscuro.  
  
5.  Activar el espacio en blanco visible. (En el **editar** menú, elija **avanzadas** y, a continuación, haga clic en **ver espacios en blanco**). Escriba algunas de las pestañas en el texto. Se deben mostrar las flechas rojas que representan las fichas.  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)

