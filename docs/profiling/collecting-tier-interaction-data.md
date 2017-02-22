---
title: "Recopilar datos de interacci&#243;n de capas mediante el IDE de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.tierinteraction"
helpviewer_keywords: 
  - "Herramientas de generación de perfiles, generación de perfiles de ADO.NET"
  - "método de generación de perfiles con interacción de capas"
  - "Herramientas de generación de perfiles, método de interacción de capas"
  - "generación de perfiles de rendimiento de ADO.NET"
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Recopilar datos de interacci&#243;n de capas mediante el IDE de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de ADO.NET.  Los datos se recopilan solamente para las llamadas a funciones sincrónicas.  
  
 **Ediciones de Visual Studio**  
  
 Los datos de generación de perfiles de interacción de capas se pueden recopilar usando Visual Studio Ultimate, Visual Studio Premium o Visual Studio Professional.  Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en VS Ultimate y VS Premium.  
  
 **Windows 8 y Windows Server 2012**  
  
 Para recopilar datos de interacción de capas de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012, debe usar el método de instrumentación.  No se pueden recopilar datos de interacción de capas para las aplicaciones de la Tienda Windows.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  Puede incluir datos de interacción de capas en todos los métodos de generación de perfiles de otras versiones compatibles de Windows.  
  
 **Asistente para rendimiento**  
  
 Debido a un error en el Asistente para rendimiento, debe agregar la opción de recopilación de datos de interacción de capas a una ejecución de generación de perfiles desde el Explorador de rendimiento.  También debe agregar el proyecto, el archivo ejecutable o el sitio web al nodo de destino del Explorador de rendimiento.  
  
### Para agregar datos de interacción de capas a una ejecución de generación de perfiles utilizando las páginas de propiedades de la sesión de rendimiento  
  
1.  En el Explorador de rendimiento, elija **Propiedades** en el menú contextual.  
  
2.  Seleccione la página **Interacciones de capas** y, a continuación, active la casilla **Habilitar generación de perfiles de interacción de capa**.  
  
3.  En el Explorador de rendimiento, seleccione el nodo **Destinos** y después especifique el proyecto, el archivo ejecutable o el sitio web cuyo perfil desea generar.  
  
## Vea también  
 [Interacciones de capas \(Vista\)](../profiling/tier-interactions-view.md)