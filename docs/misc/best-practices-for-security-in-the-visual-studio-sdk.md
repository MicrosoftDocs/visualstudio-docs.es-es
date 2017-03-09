---
title: "Pr&#225;cticas recomendadas de seguridad en SDK de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "seguridad [SDK de Visual Studio]"
  - "Control de cuentas de usuario [SDK de Visual Studio]"
  - "SDK de Visual Studio, seguridad"
  - "UAC (Control de cuentas de usuario) [SDK de Visual Studio]"
  - "prácticas recomendadas de seguridad, SDK de Visual Studio"
  - "Windows Vista, Control de cuentas de usuario [SDK de Visual Studio]"
ms.assetid: 56c8a113-0c53-4969-a009-a2ab58d855c3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# Pr&#225;cticas recomendadas de seguridad en SDK de Visual Studio
Debe entenderse la seguridad para las extensiones del VSPackage para que puedan crearse los mejores productos posibles.  
  
 Un producto seguro ayuda a proteger lo siguiente:  
  
-   La confidencialidad, integridad y disponibilidad de la información del cliente.  
  
-   La integridad y disponibilidad de los recursos de procesamiento controlados por el propietario o el administrador del sistema.  
  
## Vulnerabilidad de la seguridad  
 Una vulnerabilidad de la seguridad es un punto débil de un producto que hace que sea imposible evitar las actividades malintencionadas de un atacante, incluso cuando el producto se usa correctamente. A continuación se muestran algunos ejemplos:  
  
-   Obtener permisos en un equipo que son superiores a los de usuario.  
  
-   Asumir el funcionamiento del equipo de un usuario.  
  
-   Poner en peligro los datos del equipo del usuario.  
  
> [!IMPORTANT]
>  Nunca dé por sentado que la aplicación se ejecutará solo en entornos específicos. La aplicación podría usarse en una configuración que no espera, especialmente cuando la aplicación se populariza. En su lugar, suponga que el código se ejecutará en entornos hostiles, y diseñe, escriba y pruebe el código en consecuencia.  
  
 Los productos y sistemas diseñados y creados con la seguridad como característica principal son más sólidos que los que se escriben considerando la seguridad como problema secundario. Las aplicaciones seguras también son más resistentes a la crítica de los medios, más atractivas para los usuarios y más baratas de mantener y actualizar.  
  
## API peligrosas  
 Las llamadas a algunas funciones pueden producir vulnerabilidades de seguridad no deseadas si se usan incorrectamente, prohibir su uso no produce necesariamente código seguro. No obstante, algunos proyectos de software han obtenido ventajas apreciables de seguridad mediante la prohibición de funciones que son difíciles de usar de forma segura, como una de las muchas prácticas de desarrollo seguro. Para obtener más información, consulte el apéndice A del libro de Microsoft Press, "Writing Secure Code" de Michael Howard y David LeBlanc.  
  
 La mayoría de los problemas de seguridad son el resultado de confiar en la entrada sin comprobarla adecuadamente. Asegúrese de hacer el seguimiento de los datos al llegar al código y cuestione las implicaciones de las operaciones en los datos. Puede escribir código seguro usando la mayoría de las funciones si las entradas de datos tienen el formato correcto y se comprueba su confiabilidad.  
  
## Problemas de Control de cuentas de usuario \(UAC\)  
 La característica de Control de cuentas de usuario \(UAC\) tiene implicaciones de seguridad que debe comprender. Reduce la exposición del sistema operativo y las aplicaciones a ataques malintencionados.  
  
1.  Para obtener más información acerca de UAC en [!INCLUDE[win7](../debugger/includes/win7_md.md)], vea [¿Qué es el Control de cuentas de usuario?](http://go.microsoft.com/fwlink/?linkid=159927).  
  
2.  Para obtener más información acerca de UAC en [!INCLUDE[win8](../debugger/includes/win8_md.md)], vea [What are User Account Control settings?](http://windows.microsoft.com/windows-8/what-are-uac-settings).  
  
 Antes de la llegada de UAC, los desarrolladores solían ejecutar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con permisos de administrador, incluso cuando no eran necesarios. Debe hacer el desarrollo y prueba de la extensión como usuario normal, para asegurarse de que no necesita derechos elevados innecesariamente.  
  
 Tenga en cuenta que UAC también afecta a la implementación. Los paquetes de instalación deben crearse correctamente para admitir UAC. Un paquete creado incorrectamente provoca por lo general errores de "acceso denegado" porque el instalador intenta usar derechos de usuario normal para realizar una tarea que requiere privilegios elevados.  
  
## Vea también  
 [Prácticas recomendadas de seguridad en VSPackages](../extensibility/internals/best-practices-for-security-in-vspackages.md)   
 [Recursos para crear aplicaciones seguras](http://msdn.microsoft.com/es-es/0ebf5f69-76f2-498a-a2df-83cf3443e132)   
 [Key Security Concepts](../Topic/Key%20Security%20Concepts.md)