---
title: "COM Interop unregistration failed | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
Se ha producido un problema al intentar anular el registro de una copia antigua del ensamblado.  
  
 Si se establece la propiedad **Registrar para interoperabilidad COM**, el sistema del proyecto intentará anular el registro de una copia antigua del objeto COM antes de registrar la copia que se acaba de compilar.  Esta operación se realiza para mantener el Registro actualizado.  
  
 Vea la página de propiedades **Compilación** en la carpeta Propiedades de configuración para obtener acceso a la propiedad **Registrar para interoperabilidad COM**.  
  
 Entre las posibles razones del error se incluyen:  
  
-   Incapacidad para anular el registro de la biblioteca de tipos anterior para el ensamblado.  Puede que se trate de un problema de permisos en el Registro.  
  
-   Incapacidad para anular el registro del ensamblado antiguo.  Puede que también se trate de un problema de permisos en el Registro.  
  
 Si el proceso de anulación del registro falla, se puede provocar una pérdida del GUID para objetos CoCreatable y para cualquier biblioteca de tipos.  No obstante, el proceso de compilación global se realizará correctamente.  
  
## Vea también  
 [Interoperabilidad COM en aplicaciones .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)