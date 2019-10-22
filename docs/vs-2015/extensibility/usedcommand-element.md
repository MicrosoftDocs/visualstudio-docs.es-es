---
title: UsedCommand (elemento) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186366"
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
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|GUID|Necesario. El GUID del par de identificador de GUID que identifica el comando.|  
|id|Necesario. El identificador del par de identificador de GUID que identifica el comando.|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
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
