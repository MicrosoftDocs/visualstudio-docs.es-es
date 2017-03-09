---
title: "Memoria virtual baja | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Memoria virtual baja
Este mensaje aparece cuando hay poca memoria virtual y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deja de responder.  Sin embargo, este error no se produce cuando hay poca memoria virtual en el equipo sino cuando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se está quedando sin espacio de direcciones.  Normalmente, este error se produce en equipos que ejecutan sistemas operativos de 32 bits, que restringen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a un espacio de direcciones de 2 GB.  Cuando se trabaja con procesos de 32 bits, la aplicación solo puede direccionar 4 GB de memoria \(2^32 bits\).  Sin embargo, las versiones de 32 bits de Windows reservan 2 GB de espacio de direcciones virtual de un proceso para fines internos \(por ejemplo, para trabajar con la tarjeta de gráficos del equipo u otros controladores del sistema\).  Por tanto, el proceso de 32 bits solo puede utilizar 2 GB para sus propósitos internos.  Los usuarios pueden establecer el modificador \/3GB para asegurarse de que Windows solo se reserva 1 GB para sí mismo y concede 3 GB al proceso.  En la mayoría de los casos, el rendimiento no disminuye con un límite de solo 1 GB para Windows.  
  
 En los sistemas que ejecutan versiones de 64 bits de Windows, este error se produce raramente porque el proceso puede utilizar los 4 GB de espacio direccionable, y Windows puede usar direcciones de memoria de 64 bits para trabajar con el hardware y los controladores del sistema.  Sin embargo, el uso de memoria puede superar los 3 GB o incluso 4 GB cuando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] procesa a algunos conjuntos de datos.  Para obtener más información, vea la entrada de blog sobre [por qué hay ninguna versión de 64 bits de Visual Studio \(todavía\)](http://go.microsoft.com/fwlink/?LinkId=246307).  
  
 Este error se produce normalmente cuando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] almacena en caché grandes cantidades de datos o ejecuta varios procesos que consumen mucha memoria.  
  
 Los escenarios siguientes implican el almacenamiento en caché de grandes cantidades de datos y se pueden corregir normalmente reiniciando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Ejecutar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] por primera vez después de la instalación.  
  
-   Instalar o desinstalar una extensión.  
  
-   Elegir o personalizar elementos del **cuadro de herramientas**.  
  
-   Cambiar la configuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Permitir que el sistema entre en modo de suspensión \(hibernación\) mientras [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está abierto.  
  
 Los siguientes escenarios requieren una gran cantidad de memoria activa.  En estos casos, se recomienda ejecutar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solo con los componentes esenciales abiertos o ejecutar los procesos adicionales en una segunda instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Compilar grandes soluciones.  
  
-   Trabajar con documentos XML grandes.  
  
-   Actualizar soluciones desde una versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Redestinar soluciones.  
  
-   Ejecutar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] mientras se edita código.  
  
-   Ejecutar IntelliTrace en varios proyectos.  
  
 Si estas medidas no impiden el error, puede incrementar el espacio de direcciones disponible en un sistema que ejecute [!INCLUDE[win7](../debugger/includes/win7_md.md)] si ejecuta bcedit.exe con la sintaxis siguiente:  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 Este comando aumenta la asignación de memoria virtual en modo de usuario de 2 a 3 GB en un sistema de basado en x86.  Si se agrega el modificador \/3GB, todo el sistema puede direccionar más memoria y asignar a cada aplicación un porcentaje mayor de la memoria disponible.  
  
> [!NOTE]
>  Debe ejecutar bcdedit.exe con permisos administrativos.  Si está habilitado el cifrado de BitLocker, debe suspenderlo, realizar el cambio, reiniciar el sistema y habilitar de nuevo BitLocker.  
  
 Incluso después de aumentar la asignación de memoria virtual a 3 GB, este error puede repetirse porque cualquier aplicación única puede seguir utilizando solo 2 GB de memoria virtual.  Si este error sigue apareciendo, reduzca el tamaño de la solución y reinicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para reducir la solución, se puede refactorizarla para quitar los proyectos que se utilizan con poca frecuencia o descargar los proyectos que no son necesarios.  Si el error se produce cuando se compila la solución, intente compilarla en un símbolo del sistema.  
  
## Vea también  
 [Resources for Troubleshooting IDE Errors](../ide/reference/resources-for-troubleshooting-integrated-development-environment-errors.md)