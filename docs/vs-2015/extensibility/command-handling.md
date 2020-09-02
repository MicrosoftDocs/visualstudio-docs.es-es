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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184370"
---
# <a name="command-handling"></a>Control de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor puede definir nuevos comandos. Los comandos se muestran normalmente en un menú, en una barra de herramientas o en un menú contextual.  
  
 Para obtener más información sobre cómo definir comandos y menús, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servicio de lenguaje puede controlar qué menús contextuales se muestran en el editor mediante la interceptación de la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración. Como alternativa, puede controlar el menú contextual en función de cada marcador. Para obtener más información, vea [comandos importantes para filtros del servicio de lenguaje](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Agregar comandos al menú contextual del editor  
 Para agregar un comando al menú contextual, primero debe definir un conjunto de comandos de menú que pertenezcan a un grupo específico. El siguiente ejemplo se toma del archivo. Vsct que se genera como parte del tutorial tutorial [: agregar características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Menú contextual de CustomEditor\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 En el texto anterior se agrega un comando de menú contextual con el **menú contextual texto CustomEditor**. El GUID de menú es el del conjunto de comandos que se crea con este editor y el tipo es "context".  
  
 También puede usar comandos predefinidos que no es necesario definir en el archivo. Vsct. Por ejemplo, si examina el archivo EditorPane.cs generado por la plantilla de paquete de Visual Studio, verá que un conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definido por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> , se controla en controladores de comandos como el método onSelectAll.  
  
## <a name="see-also"></a>Consulte también  
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
