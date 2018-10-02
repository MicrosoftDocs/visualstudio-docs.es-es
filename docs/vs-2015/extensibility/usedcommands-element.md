---
title: UsedCommands (elemento) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8a3f4719b6d35be56ba447279d3a85d2a3f5118
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577803"
---
# <a name="usedcommands-element"></a>UsedCommands (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [UsedCommands (elemento)](https://docs.microsoft.com/visualstudio/extensibility/usedcommands-element).  
  
UsedCommands (elemento) agrupa elementos UsedCommand y otras agrupaciones UsedCommands.  
  
 UsedCommands (elemento) es opcional. Si no se llama comandos definidos fuera de su paquete, no es necesario incluir en esta sección en el archivo .vsct.  
  
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
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[UsedCommand (Elemento)](../extensibility/usedcommand-element.md)|El comando que se implementa por otro código.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos (por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados) que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE).|  
  
## <a name="example"></a>Ejemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Vea también  
 [UsedCommand (elemento)](../extensibility/usedcommand-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

