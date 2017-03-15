---
title: "Cambiar el nombre de nodos de jerarqu&#237;a del proyecto (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ejemplo de HierUtil7 [SDK de Visual Studio], cambiar el nombre de nodos del proyecto"
  - "nodos del proyecto, cambiar el nombre en el ejemplo de HierUtil7"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Cambiar el nombre de nodos de jerarqu&#237;a del proyecto (C++)
Puede cambiar el nombre de un nodo de la jerarquía de carpetas del proyecto utilizando el marco del proyecto HierUtil7 para C\+\+ no administrado.  Para obtener más información, vea [HierUtil7 Sample](http://msdn.microsoft.com/es-es/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## Expandir el nodo de la jerarquía  
  
#### Para expandir el nodo de la jerarquía y cambiar el nombre de la carpeta  
  
1.  Seleccione el nodo de la jerarquía mediante el método siguiente:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` es el contenedor de la jerarquía correspondiente a la carpeta y `EXPF_SelectItem` es de la enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> .  `GUID_MacroExplorer` es un definido constante de GUID en Vsshell.idl y es un ejemplo para `rguidPersistenceSlot` en la firma de la función de `ExtExpand`, definido en Hu\_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Puede encontrar el archivo de Hu\_node.h en la carpeta, \<raíz de la instalación\> \\Program Files\\VSIP 8.0\\EnvSDK \\ común \\ hierutil7:  
  
2.  Cambie el nombre de la carpeta enviando el comando cambiar nombre mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` es un puntero de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> : `<IVsUIShell>``srpVsUIShell`.  `guiVSStd97` es un identificador único del grupo de comandos al comando `cmdidRename` pertenece, definido en Vsshlids.h.  
  
## Vea también  
 [Creación de tipos de proyecto](../extensibility/internals/creating-project-types.md)   
 [Muestras de VSSDK](../misc/vssdk-samples.md)