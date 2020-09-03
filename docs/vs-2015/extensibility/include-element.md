---
title: Elemento include | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1bdc56c9d0b488bdbe24a8534ab516cc0fc831df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203942"
---
# <a name="include-element"></a>Include (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento include especifica un archivo que se puede encontrar en la ruta de inclusión proporcionada para la inserción en el archivo actual.  Todos los símbolos y tipos definidos se convertirán en parte del resultado compilado.  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp  
<Include href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|href|Necesario. La ruta de acceso al archivo de encabezado:<br /><br /> href = "stdidcmd. h"|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos (es decir, elementos de menú, menús, barras de herramientas y cuadros combinados) que un VSPackage proporciona al IDE.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
