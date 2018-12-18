---
title: Cambiar el nombre de nodos de jerarquía del proyecto (C++) | Documentos de Microsoft
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
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 5b86096834b2a841b3fe35e1045bc3897bb7667f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203767"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Cambiar el nombre de nodos de jerarquía del proyecto (C++)
Puede cambiar el nombre de un nodo de jerarquía de carpeta de proyecto mediante el marco de trabajo del proyecto de HierUtil7 para C++ no administrado. Para obtener más información, consulte [ejemplo de HierUtil7](http://msdn.microsoft.com/en-us/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Expanda el nodo de jerarquía  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Expanda el nodo de jerarquía y cambiar el nombre de la carpeta  
  
1.  Seleccione el nodo de jerarquía mediante el método siguiente:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` es el contenedor de la jerarquía correspondiente a la carpeta y `EXPF_SelectItem` proviene el <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> enumeración. El `GUID_MacroExplorer` es una constante GUID definida en Vsshell.idl y es un ejemplo de `rguidPersistenceSlot` en la firma de función de `ExtExpand`, definida en Hu_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Puede encontrar el archivo Hu_node.h en la carpeta, \<raíz de instalación > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2.  Cambiar el nombre de la carpeta mediante el comando de cambio de nombre de registro mediante el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` es un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> puntero: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` es un identificador único del grupo de comandos para que el comando `cmdidRename` pertenece, definido en Vsshlids.h.  
  
## <a name="see-also"></a>Vea también  
 [Crear tipos de proyecto](../extensibility/internals/creating-project-types.md)   
 [Muestras de VSSDK](../misc/vssdk-samples.md)