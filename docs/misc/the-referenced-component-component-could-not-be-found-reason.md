---
title: "The referenced component &#39;component&#39; could not be found. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The referenced component &#39;component&#39; could not be found. &lt;reason&gt;
El sistema del proyecto no puede resolver una referencia determinada.  Si hace doble clic en este elemento de la Lista de tareas establecerá el foco en el Explorador de soluciones y seleccionará la referencia que no se puede resolver.  
  
 Edite la propiedad [ReferencePaths](http://msdn.microsoft.com/es-es/8e549b39-7256-456a-8fd7-089b23facf9c) de manera que la ruta de acceso incluya los directorios adecuados.  
  
 Este error puede producirse si mueve un proyecto a otro equipo.  La propiedad `ReferencePath` se almacena como una ruta de acceso absoluta.  Si en el equipo A la referencia R1 reside en c:\\R\\R1.dll, el archivo .vbproj.user o .csproj.user almacenará c:\\R como parte de la propiedad `ReferencePath`.  Sin embargo, si en el equipo B R1 reside en d:\\R\\R1.dll, el sistema del proyecto no podrá encontrar R1 porque d:\\R no está en la ruta de acceso de referencia.  
  
 Un escenario parecido es el de control de código fuente.  Si da de alta un proyecto, el archivo .vbproj.user \(o .csproj.user\) no se copia en el equipo porque no está almacenado en el control de código fuente.  Por tanto, el valor inicial de la propiedad `ReferencePath` estará en blanco y todas las referencias que dependan de `ReferencePath` para su resolución quedarán sin resolver.  Para obtener más información, vea "Administrar dependencias" en *Desarrollo en equipo con Visual Studio .NET y Visual SourceSafe*.  
  
 Este error también puede producirse si un proyecto al que se hace referencia no está en la solución actual.  
  
 Este error indica que puede que el proyecto no se compile.  
  
 Para obtener más información sobre la resolución de referencias de ensamblado, vea [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md).  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)