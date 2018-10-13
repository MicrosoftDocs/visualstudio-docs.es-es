---
title: Definir elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a573413c20c305f3645b1d2795901f344ffb235
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229195"
---
# <a name="define-element"></a>Define (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define un par de nombre y valor de símbolo. Este símbolo se puede evaluar mediante atributos condicionales. Para obtener más información, consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md). Vea también el [símbolos elemento](../extensibility/symbols-element.md).  
  
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
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un paquete VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

