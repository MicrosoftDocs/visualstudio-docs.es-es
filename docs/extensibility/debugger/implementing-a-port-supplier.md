---
title: "Implementar un proveedor de puerto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], implementar proveedores de puertos"
  - "proveedores de puertos, implementar"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementar un proveedor de puerto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puertos de fuentes de un proveedor de puerto a petición en el administrador de depuración de la sesión \(SDM\).  Un proveedor de puerto debe ser implementado al depurar a no\-DCOM un equipo o cuando un nuevo dispositivo debe ser compatible.  Por ejemplo, para proporcionar la depuración a un teléfono móvil, puede implementar un proveedor de puerto que proporciona los puertos que se conectan al teléfono móvil \(quizás mediante el INTERPRETARÁ o una conexión de celda\) y muestran los procesos y los programas que se ejecutan en el teléfono.  
  
 Para depurar programas en equipos basados en Windows \(depuración remota incluida, Visual Studio proporciona los proveedores de puerto para código nativo y los procesos \(CLR\) de Common Language Runtime, de modo que no es necesario implementar dispone del proveedor de puerto en esos casos.  
  
## En esta sección  
 [Implementar y registrar un proveedor de puerto](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Describe cómo el SDM interactúa con el proveedor de puerto y los puertos.  
  
 [Interfaces de proveedor de puerto requerido](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta las interfaces que se deben implementar para obtener un proveedor de puerto.  
  
## Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos arquitectónicos de depuración principal.  
  
## Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)