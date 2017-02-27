---
title: "Utilidad de CreateExpInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compilaciones experimentales"
  - "subárbol experimental"
  - "instancia experimental"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Utilidad de CreateExpInstance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la utilidad CreateExpInstance para crear, restablecer, o eliminar una instancia experimental de Visual Studio. Puede utilizar la instancia experimental para depurar y probar las extensiones de Visual Studio sin cambiar el producto subyacente.  
  
## Sintaxis  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### Parámetros  
 O crear  
 Crea la instancia experimental.  
  
 O restablecer  
 Elimina la instancia experimental y, a continuación, crea una nueva.  
  
 \/Clean  
 Elimina la instancia experimental.  
  
 \/ VSInstance  
 El nombre del directorio que contiene la instancia de Visual Studio base para copiar.  
  
 \/ \/Rootsuffix  
 El sufijo de anexar al nombre del directorio de la instancia experimental.  
  
## Comentarios  
 Cuando se trabaja en una extensión de Visual Studio, puede presionar F5 para abrir la instancia experimental de forma predeterminada y la instalación actual. Si no está disponible ninguna instancia experimental, Visual Studio crea uno que tiene la configuración predeterminada.  
  
 La ubicación predeterminada de la instancia experimental depende del número de versión de Visual Studio. Por ejemplo, para Visual Studio 2015, la ubicación es %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ todos los archivos en la ubicación del directorio se consideran parte de esa instancia. Visual Studio no cargará cualquier instancia experimental adicional a menos que se cambia el nombre del directorio a la ubicación predeterminada.  
  
 Visual Studio no tiene acceso al registro del sistema cuando se abre la instancia experimental. Esto difiere de versiones anteriores de Visual Studio, que utiliza una versión experimental del subárbol del registro.  
  
 La utilidad CreateExpInstance reemplaza a la utilidad VsRegEx.  
  
 En el ejemplo siguiente se restablece la instancia experimental de predeterminada de Visual Studio.  
  
 **CreateExpInstance.exe \/Reset \/VSInstance \= 14.0 \/RootSuffix \= Exp**  
  
## Vea también  
 [Publicar un producto](../../misc/releasing-a-visual-studio-integration-product.md)