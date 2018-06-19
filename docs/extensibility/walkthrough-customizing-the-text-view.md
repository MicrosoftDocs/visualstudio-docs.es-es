---
title: 'Tutorial: Personalizar la vista de texto | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fb4762a422102b91c44d755d387168ab0572f2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142087"
---
# <a name="walkthrough-customizing-the-text-view"></a>Tutorial: Personalizar la vista de texto
Puede personalizar una vista de texto mediante la modificación de cualquiera de las siguientes propiedades en su mapa de formato del editor:  
  
-   Margen del indicador  
  
-   Punto de inserción  
  
-   Sobrescribir el símbolo de intercalación  
  
-   Texto seleccionado  
  
-   Texto seleccionado inactivo (es decir, texto seleccionado que se ha perdido el foco)  
  
-   Espacio en blanco visible  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Crear un proyecto MEF  
  
1.  Cree un proyecto de C# VSIX. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Llame a la solución `ViewPropertyTest`.  
  
2.  Agregar una plantilla de elementos de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="defining-the-content-type"></a>Definir el tipo de contenido  
  
1.  Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.  
  
2.  Agregue las siguientes `using` directivas:  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Declarar una clase denominada `TestViewCreationListener` que hereda de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportar esta clase con los siguientes atributos:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar el tipo de contenido al que se aplica este agente de escucha.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar el rol de este agente de escucha.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  En esta clase, importe el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Cambiar las propiedades de vista  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que se cambian las propiedades de la vista cuando se abre la vista. Para realizar el cambio, busque el <xref:System.Windows.ResourceDictionary> que se corresponde con el aspecto de la vista que desea buscar. A continuación, cambie la propiedad adecuada en el diccionario de recursos y establecer las propiedades. Procesar por lotes las llamadas a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método mediante una llamada a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> después de establecer las propiedades.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
  
1.  Compile la solución.  
  
     Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
2.  Cree un archivo de texto y escriba algún texto.  
  
    -   El punto de inserción debe ser fucsia y el símbolo de intercalación de sobrescritura debe ser turquesa.  
  
    -   El margen del indicador (a la izquierda de la vista de texto) debe ser la luz verde.  
  
3.  Seleccione el texto que acaba de escribir. El color del texto seleccionado debe ser ligero rosa.  
  
4.  Mientras el texto seleccionado, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser rosa oscuro.  
  
5.  Activar un espacio en blanco visible. (En el **editar** menú, elija **avanzadas** y, a continuación, haga clic en **ver espacios en blanco**). Escriba algunas fichas en el texto. Las flechas rojas que representan las pestañas se deben mostrar.  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)