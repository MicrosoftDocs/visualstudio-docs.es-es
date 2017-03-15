---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
El sistema del proyecto no puede crear la herramienta personalizada.  La herramienta personalizada solicitada no se ejecutará porque el sistema del proyecto no puede crear una instancia de ella.  Asegúrese de que la herramienta personalizada está instalada y registrada correctamente.  
  
 Este error se puede haber provocado al especificar un nombre de herramienta personalizada no válido para la propiedad `CustomTool` de un archivo determinado.  También es posible que se haya editado el archivo de proyecto \(.vbproj\/.csproj\), lo que habría convertido el valor de la propiedad `CustomTool` en no válido.  Asimismo, puede que esté utilizando un proyecto desarrollado en otro equipo que tenga la herramienta personalizada, pero dicha herramienta no está instalada en su equipo.  Para obtener más información sobre la propiedad `CustomTool`, vea [File Properties](http://msdn.microsoft.com/es-es/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 Este error también se puede producir si falla [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) en la herramienta personalizada.  Por ejemplo, puede no estar registrada o que falte una DLL necesaria.  
  
## Vea también  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)