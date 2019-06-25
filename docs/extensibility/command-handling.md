---
title: Control de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52c47e7dca715859408f1697fd31f1a1a2cf534b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315553"
---
# <a name="command-handling"></a>Control de comandos
El editor puede definir nuevos comandos. Normalmente, los comandos se muestran en un menú, en una barra de herramientas o en un menú contextual.

 Para obtener más información sobre cómo definir comandos y menús, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

 Un servicio de lenguaje puede controlar qué menús contextuales se muestran en el editor, interceptando la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración. Como alternativa, puede controlar el menú contextual de una base por marcador. Para obtener más información, consulte [comandos importantes para los filtros del servicio de lenguaje](../extensibility/internals/important-commands-for-language-service-filters.md).

## <a name="add-commands-to-the-editor-context-menu"></a>Agregar comandos en el menú contextual del editor
 Para agregar un comando al menú contextual, primero debe definir un conjunto de comandos de menú que pertenecen a un grupo específico. En el siguiente ejemplo se toma de la *.vsct* archivo generado como parte del tutorial [Tutorial: Agregar características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):

 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">

 \<Parent guid="guidCustomEditorCmdSet" id="0"/>

 \<Cadenas >

 \<ButtonText > menú contextual de CustomEditor\</ButtonText >

 \<CommandName>CustomEditorContextMenu\</CommandName>

 \</Strings>

 \</ Menú >

 \</Menus>

 El texto anterior agrega un comando de menú contextual con el texto **menú contextual de CustomEditor**. El GUID del menú es parte del conjunto de comandos que se crea con este editor. El tipo es "Contexto".

 También puede usar comandos predefinidos que no es necesario que se definen en el *.vsct* archivo. Por ejemplo, examine el *EditorPane.cs* archivo generado por la plantilla de paquete de Visual Studio. Observará que un conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definido por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, se controlan en los controladores de comandos, como el `onSelectAll` método.

## <a name="see-also"></a>Vea también
- [Los comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)