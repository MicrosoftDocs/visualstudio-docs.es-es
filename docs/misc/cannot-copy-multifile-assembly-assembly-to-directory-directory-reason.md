---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
Los ensamblados de múltiples archivos se copian en un subdirectorio del directorio del proyecto desde el que se ejecutarán.  Por ejemplo, si la ruta de acceso de los resultados es c:\\project1\\bin y ahí existe un ensamblado \(cuya propiedad `CopyLocal` es `true`\) denominado Test que contiene archivos a.dll y b.dll, una vez finalizada la copia tendrá la estructura de archivos siguiente:  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 El sistema del proyecto muestra este error si no se puede crear en el disco el directorio c:\\project1\\bin\\Test.  
  
 Este error indica que el espacio en disco es insuficiente o que se está alcanzando el límite MAX\_PATH para longitudes de rutas de acceso.  
  
 **Para corregir este error**  
  
-   Compruebe el espacio en disco.  
  
-   Mueva el proyecto a una carpeta con una longitud de ruta de acceso menor que la de la carpeta en la que se encuentra actualmente el proyecto.  
  
-   Cambie el directorio de resultados a una carpeta con una longitud de ruta de acceso absoluta menor \(aplicable sólo a proyectos de cliente\).  
  
## Vea también  
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)   
 [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/es-es/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)