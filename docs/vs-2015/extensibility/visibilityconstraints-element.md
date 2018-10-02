---
title: VisibilityConstraints (elemento) | Microsoft Docs
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
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9fd6d6968984f0640dd73067c286a4259ade6745
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581114"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [VisibilityConstraints (elemento)](https://docs.microsoft.com/visualstudio/extensibility/visibilityconstraints-element).  
  
VisibilityConstraints (elemento) determina la visibilidad estática de los grupos de comandos y las barras de herramientas. En primer lugar se controla la visibilidad mediante las [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) sin tener que cargar el VSPackage.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[VisibilityItem (Elemento)](../extensibility/visibilityitem-element.md)|Determina la visibilidad de los comandos y las barras de herramientas estática.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilidad de los grupos de comandos y las barras de herramientas estática.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos (por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados) que un paquete VSPackage proporciona al IDE.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Vea también  
 [VisibilityItem (elemento)](../extensibility/visibilityitem-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

