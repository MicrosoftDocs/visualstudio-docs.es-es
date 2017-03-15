---
title: "Control de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], heredados - control de comandos"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Control de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor puede definir nuevos comandos. Normalmente se muestran los comandos en un menú, una barra de herramientas, o en un menú contextual.  
  
 Para obtener más información acerca de cómo definir los menús y comandos, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servicio de lenguaje puede controlar los menús contextuales se muestran en el editor, interceptando la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración. Como alternativa, puede controlar el menú contextual en una base por marcador. Para obtener más información consulte [comandos importantes para los filtros de servicio de lenguaje](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Agregar comandos al menú contextual de Editor  
 Para agregar un comando al menú contextual, primero debe definir un conjunto de comandos de menú que pertenecen a un grupo específico. En el siguiente ejemplo se toma del archivo .vsct generado como parte del tutorial [Tutorial: agregar características a un Editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \< guid de menú = "guidCustomEditorCmdSet" id = "IDMX_RTF" prioridad = "0 x 0000" type = "Context">  
  
 \< guid principal = "guidCustomEditorCmdSet" id = "0" />  
  
 \< cadenas>  
  
 \< ButtonText>menú contextual de CustomEditor \< / ButtonText>  
  
 \< CommandName>CustomEditorContextMenu \< / CommandName>  
  
 \< / cadenas>  
  
 \< / menú>  
  
 \< / menús>  
  
 El texto anterior agrega un comando de menú contextual con el texto **menú contextual de CustomEditor**. El GUID de menú es que los del conjunto de comandos que se crea con este editor, y el tipo es "Context".  
  
 También puede utilizar comandos predefinidos que no es necesario que deben definirse en el archivo .vsct. Por ejemplo, si examina el archivo EditorPane.cs generado por la plantilla de paquete de Visual Studio, verá que un conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definidos por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, se administran en los controladores de comando como el método onSelectAll.  
  
## <a name="see-also"></a>Vea también  
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)