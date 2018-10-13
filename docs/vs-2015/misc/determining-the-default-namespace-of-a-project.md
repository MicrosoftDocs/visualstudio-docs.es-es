---
title: Determinar el Namespace predeterminado de un proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: a456b9b48ce9ba0817070fb5f04b5c9f80ffb149
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223332"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Determinación del espacio de nombres predeterminado de un proyecto
Para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], si la `CustomToolNamespace` propiedad está establecida en el archivo de entrada, a continuación, el valor de `CustomToolNamespace` se convierte en el valor del parámetro de espacio de nombres predeterminado pasando a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método. En caso contrario, el `wszDefaultNamespace` parámetro pasado a `Generate` siempre es igual al espacio de nombres raíz. Para obtener más información sobre los espacios de nombres, vea [palabras clave Namespace](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] utiliza espacios de nombres basados en la carpeta. Es decir, el espacio de nombres está formado por el espacio de nombres raíz, además de los nombres de las carpetas que contiene la herramienta personalizada. Cada nombre de carpeta se convierte en un identificador válido y períodos de separan todos los nombres. Por ejemplo, si el archivo de entrada es FolderA\FolderB\FolderC\MyInput.txt y el espacio de nombres raíz es CL9, el espacio de nombres predeterminada calculada sería **CL9. FolderA.FolderB.FolderC**.  
  
 Se produce una excepción a esta regla cuando la cadena de jerarquía contiene una carpeta de referencia Web. Por ejemplo, si:  
  
-   FolderC eran una carpeta de referencia Web, el espacio de nombres sería **CL9. FolderC**.  
  
-   %Windir%$NTUninstallKB941568_DX7$\Spuninstb eran una carpeta de referencia Web, el espacio de nombres sería **CL9. FolderB.FolderC**.  
  
 Es decir, el espacio de nombres usa el formato siguiente:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Vea también  
 [Implementar generadores de un solo archivo](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrar generadores de un solo archivo](../extensibility/internals/registering-single-file-generators.md)   
 [Exposición de tipos a diseñadores visuales](../extensibility/internals/exposing-types-to-visual-designers.md)