---
title: VisibilityConstraints (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ade6f2ac15d5b1c46b9b388d13b52d87129a66b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930276"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints (elemento)
VisibilityConstraints (elemento) determina la visibilidad estática de los grupos de comandos y las barras de herramientas. En primer lugar se controla la visibilidad mediante las [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) sin tener que cargar el VSPackage.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
|[VisibilityItem (elemento)](../extensibility/visibilityitem-element.md)|Determina la visibilidad de los comandos y las barras de herramientas estática.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilidad de los grupos de comandos y las barras de herramientas estática.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos (por ejemplo, los elementos de menú, menús, barras de herramientas y cuadros combinados) que un paquete VSPackage proporciona al IDE.|  
  
## <a name="example"></a>Ejemplo  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Vea también  
 [VisibilityItem (elemento)](../extensibility/visibilityitem-element.md)   
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)