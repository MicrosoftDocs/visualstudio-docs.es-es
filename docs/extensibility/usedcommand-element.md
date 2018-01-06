---
title: Elemento UsedCommand | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 06375b45e21e0b83c62f2509d666b786479ff2b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Permite que un paquete VSPackage tener acceso a un comando que se define en otro archivo de vsct. Por ejemplo, si el paquete de VS utiliza la norma **copia** comando, que se define mediante el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, puede agregar el comando a un menú o barra de herramientas sin necesidad de volver a implementarlo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido. El GUID del par de Id. de GUID que identifica el comando.|  
|id|Requerido. El identificador del par de Id. de GUID que identifica el comando.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguna||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Los elementos de UsedCommand de grupos y otras agrupaciones UsedCommands.|  
  
## <a name="remarks"></a>Comentarios  
 Mediante la adición de un comando para la `<UsedCommands>` informa de un VSPackage de elemento, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno que el VSPackage requiere que el comando. Debe agregar una `<UsedCommand>` (elemento) para cualquier comando que necesita el paquete no puede incluirse en todas las versiones y las configuraciones de Visual Studio. Por ejemplo, si el paquete llama a un comando que es específico de Visual C++, el comando no estará disponible para los usuarios de Visual Web Developer a menos que incluya un `<UsedCommand>` (elemento) para el comando.  
  
## <a name="example"></a>Ejemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)