---
title: Elemento UsedCommands | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa2dd8bbcfaaa84905f60e2f4ae984f3269c7095
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="usedcommands-element"></a>Elemento UsedCommands
El elemento UsedCommands agrupa elementos de UsedCommand y otras agrupaciones UsedCommands.  
  
 El elemento UsedCommands es opcional. Si no se llama a comandos definidos fuera de su paquete, no es necesario incluir en esta sección en el archivo .vsct.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[UsedCommand (Elemento)](../extensibility/usedcommand-element.md)|El comando que se implementa por otro código.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos (por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados) que proporciona un paquete VSPackage para el entorno de desarrollo integrado (IDE).|  
  
## <a name="example"></a>Ejemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento UsedCommand](../extensibility/usedcommand-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)