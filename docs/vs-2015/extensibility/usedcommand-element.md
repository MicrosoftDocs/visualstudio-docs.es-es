---
title: UsedCommand (elemento) | Documentos de Microsoft
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
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: abcc3117b46cca424388b849f9baf26d79ca270e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194647"
---
# <a name="usedcommand-element"></a>UsedCommand (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Habilita un VSPackage tener acceso a un comando que se define en otro archivo de vsct. Por ejemplo, si el paquete VSPackage usa el estándar **copia** comando, que se define mediante el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell, puede agregar el comando a un menú o barra de herramientas sin volver a implementarlo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido. El GUID del par de identificador de GUID que identifica el comando.|  
|id|Requerido. El identificador del par de identificador de GUID que identifica el comando.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguna||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[UsedCommands (Elemento)](../extensibility/usedcommands-element.md)|Agrupa los elementos de UsedCommand y otras agrupaciones UsedCommands.|  
  
## <a name="remarks"></a>Comentarios  
 Mediante la adición de un comando para el `<UsedCommands>` informa un VSPackage de elemento, el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage que requiere que el comando del entorno. Debe agregar una `<UsedCommand>` (elemento) para cualquier comando que necesita el paquete no puede incluirse en todas las versiones y configuraciones de Visual Studio. Por ejemplo, si el paquete llama a un comando que es específico de Visual C++, el comando no estará disponible para los usuarios de Visual Web Developer a menos que incluya un `<UsedCommand>` (elemento) para el comando.  
  
## <a name="example"></a>Ejemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Vea también  
 [UsedCommands (elemento)](../extensibility/usedcommands-element.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

