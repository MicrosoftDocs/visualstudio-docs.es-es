---
title: Elemento primario | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988304"
---
# <a name="parent-element"></a>Elemento Parent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento primario de un cuadro combinado o botón sólo puede ser un grupo. El elemento primario de un menú o un grupo puede ser cualquier otro grupo o menú. En un [CommandPlacement (elemento)](../extensibility/commandplacement-element.md), este elemento es necesario; en todas las demás instancias es opcional. Si se omite este elemento, el elemento primario de `Group_Undefined:0` se implicarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Obligatorio. Identificador de comando de GUID o identificador de GUID.|  
|id|Obligatorio. Id. de GUID/ID el identificador de comando.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguna  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados.|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)|Grupos [elemento Button](../extensibility/button-element.md) elementos.|  
|[Menus (Elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|  
|[Groups (Elemento)](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un paquete VSPackage.|  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
