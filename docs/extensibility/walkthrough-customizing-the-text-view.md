---
title: "Tutorial: Personalizar la vista de texto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevos - personalizar la vista"
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Tutorial: Personalizar la vista de texto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede personalizar una vista de texto al modificar cualquiera de las siguientes propiedades en su mapa de formato del editor:  
  
-   Margen del indicador  
  
-   Punto de inserción  
  
-   Sobrescribir el símbolo de intercalación  
  
-   Texto seleccionado  
  
-   Texto seleccionado inactivo \(es decir, texto seleccionado que se ha perdido el foco\)  
  
-   Espacio en blanco visible  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Crear un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `ViewPropertyTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## Definir el tipo de contenido  
  
1.  Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.  
  
2.  Agregue las siguientes `using` directivas:  
  
     [!CODE [VSSDKViewPropertyTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkviewpropertytest#1)]  
  
3.  Declare una clase denominada `TestViewCreationListener` que hereda de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportar esta clase con los siguientes atributos:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar el tipo de contenido al que se aplica este agente de escucha.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar la función de este agente de escucha.  
  
     [!CODE [VSSDKViewPropertyTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdkviewpropertytest#2)]  
  
4.  En esta clase, importe la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!CODE [VSSDKViewPropertyTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdkviewpropertytest#3)]  
  
## Cambiar las propiedades de vista  
  
1.  Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que se cambian las propiedades de la vista cuando se abre la vista. Para realizar el cambio, busque el <xref:System.Windows.ResourceDictionary> que se corresponde con el aspecto de la vista que desea buscar. A continuación, cambie la propiedad adecuada en el diccionario de recursos y establecer las propiedades. Procesar por lotes las llamadas a la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método llamando el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, el <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> después de establecer las propiedades.  
  
     [!CODE [VSSDKViewPropertyTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdkviewpropertytest#4)]  
  
## Compilar y probar el código  
  
1.  Compile la solución.  
  
     Cuando se ejecuta este proyecto en el depurador, se crea una instancia de una segunda instancia de Visual Studio.  
  
2.  Cree un archivo de texto y escriba algún texto.  
  
    -   El punto de inserción debe ser fucsia y el símbolo de intercalación de sobrescritura deben turquesa.  
  
    -   El margen del indicador \(a la izquierda de la vista de texto\) debe ser la luz verde.  
  
3.  Seleccione el texto que escribió. El color del texto seleccionado debe ser ligero rosa.  
  
4.  Mientras está seleccionado el texto, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser rosa oscuro.  
  
5.  Encienda el espacio en blanco visible. \(En el **Editar** menú, seleccione **avanzadas** y, a continuación, haga clic en **Ver espacios en blanco**\). Escriba algunas de las pestañas en el texto. Se deben mostrar las flechas rojas que representan las fichas.  
  
## Vea también  
 [Servicio de lenguaje y los puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)