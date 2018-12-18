---
title: Control de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a155927bb69c55c15a06cb058692038c8b309a30
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230874"
---
# <a name="command-handling"></a>Control de comandos
El editor puede definir nuevos comandos. Normalmente, los comandos se muestran en un menú, en una barra de herramientas o en un menú contextual.  
  
 Para obtener más información sobre cómo definir comandos y menús, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servicio de lenguaje puede controlar qué menús contextuales se muestran en el editor, interceptando la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración. Como alternativa, puede controlar el menú contextual de una base por marcador. Para obtener más información, consulte [comandos importantes para los filtros del servicio de lenguaje](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="add-commands-to-the-editor-context-menu"></a>Agregar comandos en el menú contextual del editor  
 Para agregar un comando al menú contextual, primero debe definir un conjunto de comandos de menú que pertenecen a un grupo específico. En el siguiente ejemplo se toma de la *.vsct* archivo generado como parte del tutorial [Tutorial: agregar características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid del menú = "guidCustomEditorCmdSet" id = "IDMX_RTF" prioridad = "0 x 0000" type = "Context" >  
  
 \<Guid del elemento primario = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Cadenas >  
  
 \<ButtonText > menú contextual de CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Cadenas de >  
  
 \</ Menú >  
  
 \</ Menús >  
  
 El texto anterior agrega un comando de menú contextual con el texto **menú contextual de CustomEditor**. El GUID del menú es parte del conjunto de comandos que se crea con este editor. El tipo es "Contexto".  
  
 También puede usar comandos predefinidos que no es necesario que se definen en el *.vsct* archivo. Por ejemplo, examine el *EditorPane.cs* archivo generado por la plantilla de paquete de Visual Studio. Observará que un conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definido por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, se controlan en los controladores de comandos, como el `onSelectAll` método.  
  
## <a name="see-also"></a>Vea también  
 [Los comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)