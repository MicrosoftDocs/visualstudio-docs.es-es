---
title: Elemento primario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 795654925a92f3e9ac0718e070e85c0f4f7f21c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="parent-element"></a>Elemento Parent
El elemento primario de un cuadro combinado o botón sólo puede ser un grupo. El elemento primario de un menú o un grupo puede ser cualquier otro menú o grupo. En un [CommandPlacement elemento](../extensibility/commandplacement-element.md), este elemento es necesario; en todas las demás instancias es opcional. Si se omite este elemento, el elemento primario de `Group_Undefined:0` se se implícito.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido. Identificador de comando de GUID/identificador GUID.|  
|id|Requerido. Identificador de comando del identificador de GUID/ID.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguna  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que proporciona un paquete VSPackage para el entorno de desarrollo integrado (IDE). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)|Grupos de [elemento Button](../extensibility/button-element.md) elementos.|  
|[Menus (Elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|  
|[Groups (Elemento)](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un VSPackage.|  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)