---
title: Definir elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2596023628086ce5e921eeb8499956828d4c8a5c
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497166"
---
# <a name="define-element"></a>Definir el elemento
Define un par de nombre y valor de símbolo. Este símbolo se puede evaluar mediante atributos condicionales. Para obtener más información, consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md). Vea también el [Symbols (elemento)](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|name|Requerido. El nombre del símbolo:<br /><br /> nombre = "Mode"|  
|value|Requerido. El valor del símbolo:<br /><br /> valor = "Estándar"|  
|Condición|Opcional. Para obtener más información, consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)