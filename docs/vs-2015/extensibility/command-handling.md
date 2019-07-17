---
title: Control de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184370"
---
# <a name="command-handling"></a>Control de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor puede definir nuevos comandos. Normalmente, los comandos se muestran en un menú, en una barra de herramientas, o en un menú contextual.  
  
 Para obtener más información sobre cómo definir comandos y menús, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servicio de lenguaje puede controlar qué menús contextuales se muestran en el editor, interceptando la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración. Como alternativa, puede controlar el menú contextual de una base por marcador. Para obtener más información, consulte [comandos importantes para los filtros de servicio de lenguaje](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Adición de comandos en el menú contextual del Editor  
 Para agregar un comando al menú contextual, primero debe definir un conjunto de comandos de menú que pertenecen a un grupo específico. El siguiente ejemplo se tomó del archivo .vsct generado como parte del tutorial [Tutorial: Agregar características a un Editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid del menú = "guidCustomEditorCmdSet" id = "IDMX_RTF" prioridad = "0 x 0000" type = "Context" >  
  
 \<Guid del elemento primario = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Cadenas >  
  
 \<ButtonText > menú contextual de CustomEditor\</ButtonText >  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</ Menú >  
  
 \</ Menús >  
  
 El texto anterior agrega un comando de menú contextual con el texto **menú contextual de CustomEditor**. El GUID del menú es que los del conjunto de comandos que se crea con este editor, y el tipo es "Contexto".  
  
 También puede usar comandos predefinidos que no es necesario que se definen en el archivo .vsct. Por ejemplo, si examina el archivo EditorPane.cs generado por la plantilla de paquete de Visual Studio, puede encontrar que un conjunto de comandos predefinidos, tales como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definido por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, que se tratan en los controladores de comandos, como el método onSelectAll.  
  
## <a name="see-also"></a>Vea también  
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
