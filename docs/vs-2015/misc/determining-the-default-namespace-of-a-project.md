---
title: Determinar el espacio de nombres predeterminado de un proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705770"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Determinación del espacio de nombres predeterminado de un proyecto
En el caso de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , si la `CustomToolNamespace` propiedad se establece en el archivo de entrada, el valor de `CustomToolNamespace` se convierte en el valor del parámetro de espacio de nombres predeterminado que se pasa al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método. De lo contrario, el `wszDefaultNamespace` parámetro que se pasa a `Generate` es siempre igual al espacio de nombres raíz. Para obtener más información sobre los espacios de nombres, vea [palabras clave de espacio de nombres](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] usa espacios de nombres basados en carpetas. Es decir, el espacio de nombres se compone del espacio de nombres raíz, más los nombres de las carpetas que contienen la herramienta personalizada. Cada nombre de carpeta se convierte en un identificador válido y los puntos separan todos los nombres. Por ejemplo, si el archivo de entrada es FolderA\FolderB\FolderC\MyInput.txt y el espacio de nombres raíz es CL9, el espacio de nombres predeterminado calculado sería **CL9. CarpetaA. FolderB. FolderC**.  
  
 Una excepción a esta regla se produce cuando la cadena de jerarquía contiene una carpeta de referencia Web. Por ejemplo, si:  
  
- FolderC eran una carpeta de referencia Web, el espacio de nombres sería **CL9. FolderC**.  
  
- FolderB eran una carpeta de referencia Web, el espacio de nombres sería **CL9. FolderB. FolderC**.  
  
  Es decir, el espacio de nombres utiliza el formato siguiente:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Consulte también  
 [Implementación de generadores de un solo archivo](../extensibility/internals/implementing-single-file-generators.md)   
 [Registro de generadores de un solo archivo](../extensibility/internals/registering-single-file-generators.md)   
 [Exposición de tipos a diseñadores visuales](../extensibility/internals/exposing-types-to-visual-designers.md)